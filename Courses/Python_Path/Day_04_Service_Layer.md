# Week 1: Architecture Fundamentals - Day 4
# Service Layer - Business Logic Organization

* [Syllabus](./Syllabus.md)
* [Previous: Day 3](./Day_03_Repository_Pattern.md)
* [Next: Day 5](./Day_05_Configuration_Management.md)

## 🎯 30-Minute Learning Objectives
By the end of this session, you will:
* Understand the Service Layer pattern
* Separate business logic from controllers
* Implement service classes
* Apply to Personal History business rules

## ⏰ Session Timeline
```
5 min: Review Repository Pattern
10 min: Learn Service Layer Concepts  
15 min: Implement Service Class
5 min: Apply to Personal History
5 min: Review & Next Steps
```

## 📚 Core Concepts

### 1. What is a Service Layer?
A **Service Layer**:
- **Contains** business logic and rules
- **Sits between** controllers and models/repositories
- **Orchestrates** multiple operations
- **Validates** business rules
- **Handles** transactions and coordination

### 2. The Architecture Stack:
```
┌─────────────────┐
│   Controllers   │ ← User input/output
├─────────────────┤
│   Services      │ ← Business logic & rules
├─────────────────┤
│ Repositories    │ ← Data access
├─────────────────┤
│   Models        │ ← Data structures
└─────────────────┘
```

### 3. Why Use Services?

#### **Problem: Business Logic in Controllers**
```python
# Controller doing too much
class UserController:
    def register_user(self, email, password):
        # Validation (should be in service)
        if not self._is_valid_email(email):
            return {"error": "Invalid email"}
        
        # Business rule (should be in service)
        if self._user_exists(email):
            return {"error": "User already exists"}
        
        # Data processing (should be in service)
        hashed_password = self._hash_password(password)
        verification_token = self._generate_token()
        
        # Data access (should use repository)
        user = {
            "email": email,
            "password": hashed_password,
            "token": verification_token,
            "created_at": datetime.now()
        }
        
        with open(f'users/{email}.json', 'w') as f:
            json.dump(user, f)
        
        # Notification (should be in service)
        self._send_verification_email(email, verification_token)
        
        return {"success": True}
```

#### **Solution: Separate Service Layer**
```python
# Controller (thin)
class UserController:
    def __init__(self, user_service):
        self.service = user_service
    
    def register_user(self, email, password):
        try:
            user = self.service.register(email, password)
            return {"success": True, "user_id": user.id}
        except ValidationError as e:
            return {"error": str(e)}
        except UserExistsError as e:
            return {"error": str(e)}

# Service (business logic)
class UserService:
    def __init__(self, user_repository, email_service):
        self.repository = user_repository
        self.email_service = email_service
    
    def register(self, email, password):
        # Validation
        self._validate_email(email)
        self._validate_password(password)
        
        # Business rules
        if self.repository.find_by_email(email):
            raise UserExistsError(f"User {email} already exists")
        
        # Data processing
        hashed_password = self._hash_password(password)
        verification_token = self._generate_token()
        
        # Create user
        user = User(
            email=email,
            password_hash=hashed_password,
            verification_token=verification_token
        )
        
        # Save
        saved_user = self.repository.save(user)
        
        # Side effects (notifications)
        self.email_service.send_verification(email, verification_token)
        
        return saved_user
```

## 💻 Code Examples

### **Example 1: Personal History Service**

#### **Without Service Layer:**
```python
# Controller doing business logic
class HistoryController:
    def add_activity(self, activity_type, duration, project=None):
        # Validation
        if duration <= 0:
            raise ValueError("Duration must be positive")
        
        if activity_type not in ['work', 'family', 'exercise']:
            raise ValueError("Invalid activity type")
        
        # Business rule: max 24 hours per day
        today_activities = self._get_todays_activities()
        total_today = sum(a.duration for a in today_activities)
        
        if total_today + duration > 24 * 60:  # 24 hours in minutes
            raise ValueError("Cannot exceed 24 hours in a day")
        
        # Create activity
        activity = Activity(
            type=activity_type,
            duration=duration,
            project=project,
            timestamp=datetime.now()
        )
        
        # Save
        self.repository.save(activity)
        
        # Update analytics
        self._update_daily_total(activity_type, duration)
        
        return activity
```

#### **With Service Layer:**
```python
# Service class
class ActivityService:
    def __init__(self, activity_repository, analytics_service):
        self.repository = activity_repository
        self.analytics = analytics_service
        self.allowed_types = {'work', 'family', 'exercise', 'learning'}
    
    def add_activity(self, activity_type, duration, project=None, user_id=None):
        # Validation
        self._validate_activity_type(activity_type)
        self._validate_duration(duration)
        
        # Business rules
        self._check_daily_limit(user_id, duration)
        self._check_concurrent_activities(user_id)
        
        # Create activity
        activity = Activity(
            type=activity_type,
            duration=duration,
            project=project,
            user_id=user_id,
            timestamp=datetime.now()
        )
        
        # Save
        saved_activity = self.repository.save(activity)
        
        # Update analytics (side effect)
        self.analytics.record_activity(activity)
        
        # Notify if interesting pattern
        if self._is_interesting_pattern(activity):
            self._notify_pattern_detected(activity)
        
        return saved_activity
    
    def _validate_activity_type(self, activity_type):
        if activity_type not in self.allowed_types:
            raise ValidationError(
                f"Activity type must be one of: {self.allowed_types}"
            )
    
    def _validate_duration(self, duration):
        if duration <= 0:
            raise ValidationError("Duration must be positive")
        if duration > 8 * 60:  # 8 hours in minutes
            raise ValidationError("Single activity cannot exceed 8 hours")
    
    def _check_daily_limit(self, user_id, new_duration):
        today = datetime.now().date()
        todays_activities = self.repository.find_by_user_and_date(user_id, today)
        total_today = sum(a.duration for a in todays_activities)
        
        if total_today + new_duration > 24 * 60:  # 24 hours
            raise BusinessRuleError(
                f"Cannot exceed 24 hours per day. Already have {total_today} minutes"
            )
    
    def _check_concurrent_activities(self, user_id):
        # Check if user has overlapping activities
        recent = self.repository.find_recent_by_user(user_id, minutes=5)
        if recent:
            raise BusinessRuleError(
                "Cannot start new activity while another is active"
            )
```

### **Example 2: Using the Service**

#### **Controller (Thin):**
```python
class ActivityController:
    def __init__(self, activity_service, view):
        self.service = activity_service
        self.view = view
    
    def handle_add_activity(self, user_input):
        try:
            # Parse input
            activity_type = user_input.get('type')
            duration = int(user_input.get('duration', 0))
            project = user_input.get('project')
            
            # Use service
            activity = self.service.add_activity(
                activity_type=activity_type,
                duration=duration,
                project=project,
                user_id=self.current_user.id
            )
            
            # Display result
            return self.view.show_activity_added(activity)
            
        except ValidationError as e:
            return self.view.show_validation_error(str(e))
        except BusinessRuleError as e:
            return self.view.show_business_error(str(e))
        except Exception as e:
            return self.view.show_unexpected_error(str(e))
```

## 🔍 Service Layer in Your Code

### **Current Personal History:**
Look at `personal_history/ph/v001/services/` directory:

```
services/
├── __init__.py
└── (might be empty or have services)
```

**Question:** Do you have service classes separating business logic?

### **Your habits code business logic:**
```python
# habits_archive/create.py
def generate_hash_values(firstname, lastname, tax_id, password):
    # Mixed: validation + processing + formatting
    # This could be a HashService class!
```

## 🛠️ Hands-On Exercise (15 minutes)

### **Exercise 1: Identify Business Logic**
Look at your Personal History v0.01:

1. **Open** `personal_history/ph/v001/core.py`
2. **Search for:** Validation, business rules, calculations
3. **Question:** Is business logic separated or mixed with data access?

### **Exercise 2: Design a HashService**
From your `generate_hash_values` function, design a service:

**Current function does:**
1. Validates inputs (implicitly)
2. Hashes multiple values
3. Converts time formats
4. Constructs data structures

**Proposed HashService:**
```python
class HashService:
    def __init__(self, hash_algorithm='sha256'):
        self.algorithm = hash_algorithm
    
    def hash_sensitive_data(self, tax_id, password):
        # Business rule: must hash sensitive data
        pass
    
    def create_user_identity(self, firstname, lastname, tax_id, password):
        # Orchestrates multiple operations
        pass
    
    def validate_tax_id_format(self, tax_id):
        # Business rule validation
        pass
```

### **Exercise 3: Simple Service Implementation**
Create a simple `TimeTrackingService` for Personal History:

```python
class TimeTrackingService:
    def __init__(self, activity_repository):
        self.repository = activity_repository
    
    def log_work_session(self, project, duration_minutes, description=""):
        # 1. Validate duration (5 min to 8 hours)
        # 2. Check for overlapping sessions
        # 3. Apply work-specific rules
        # 4. Create and save activity
        # 5. Return result with metadata
        pass
    
    def get_daily_summary(self, date):
        # Business logic: categorize, total, analyze patterns
        pass
```

## 🔄 Apply to Personal History (5 minutes)

### **Current v0.01 Business Logic:**
Check where these business rules might be:
1. **Activity validation** (allowed types, duration limits)
2. **Time calculations** (durations, totals, averages)
3. **File naming conventions** (your hash-based approach)
4. **Sync rules** (pending vs committed activities)

### **Action Item:**
1. Find one piece of business logic in your code
2. Note if it's mixed with data access or presentation
3. Think about extracting to a service class

### **Potential Service for Personal History:**
```python
class PersonalHistoryService:
    def __init__(self, activity_repo, identity_repo, file_repo):
        self.activities = activity_repo
        self.identities = identity_repo
        self.files = file_repo
    
    def create_daily_history(self, user_id, date):
        # Business logic:
        # 1. Get activities for date
        # 2. Validate and process
        # 3. Create forward-secure hash chain
        # 4. Generate .ph.json file
        # 5. Sign with user identity
        pass
    
    def verify_history_integrity(self, filepath):
        # Business logic for verification
        pass
```

## 📝 Review & Next Steps (5 minutes)

### **Key Takeaways:**
1. **Service Layer** contains business logic and rules
2. **Separation** keeps controllers thin and focused
3. **Testability** - Services can be tested independently
4. **Reusability** - Services can be used by multiple controllers

### **Benefits for Personal History:**
1. **Clean architecture** - Clear separation of concerns
2. **Business rules centralized** - Easy to modify and test
3. **Thin controllers** - Focus on input/output only
4. **Flexible** - Services can be composed and reused

### **Tomorrow's Preview:**
**Day 5:** Configuration Management - We'll learn about managing settings and environment

### **Homework (Optional):**
1. Identify 2-3 business rules in Personal History
2. Sketch a service class that would contain them
3. Note where these rules are currently implemented

## 🎯 Success Checklist
- [ ] Understand Service Layer purpose
- [ ] Can identify business logic in code
- [ ] See benefits for Personal History
- [ ] Can design simple service interface

## 💡 Pro Tip
**Ask "What are the rules?":** When writing code, separate "what are the business rules?" (service) from "how do I get/show data?" (controller/repository/view).

---
**Time Spent:** [ ] 30-45 minutes  
**Confidence Level:** [ ] Low [ ] Medium [ ] High  
**Applied to PH:** [ ] Yes [ ] No

*Track your architecture learning in Personal History!*