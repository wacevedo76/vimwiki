# Week 1: Architecture Fundamentals - Day 3
# Repository Pattern - Data Access Layer

* [Syllabus](./Syllabus.md)
* [Previous: Day 2](./Day_02_MVC_Implementation.md)
* [Next: Day 4](./Day_04_Service_Layer.md)

## 🎯 30-Minute Learning Objectives
By the end of this session, you will:
* Understand the Repository pattern
* Separate data access from business logic
* Implement a simple repository
* Apply to Personal History data layer

## ⏰ Session Timeline
```
5 min: Review Separation of Concerns
10 min: Learn Repository Pattern  
15 min: Implement Simple Repository
5 min: Apply to Personal History
5 min: Review & Next Steps
```

## 📚 Core Concepts

### 1. What is the Repository Pattern?
A **Repository** is a layer that:
- **Separates** data access logic from business logic
- **Provides** a collection-like interface for data
- **Abstracts** the underlying data source (files, database, API)
- **Centralizes** data access code in one place

### 2. Why Use Repositories?

#### **Problem: Data Access Scattered**
```python
# Business logic mixed with data access
class UserService:
    def get_user(self, user_id):
        # Direct database/file access
        with open(f'users/{user_id}.json') as f:
            return json.load(f)
    
    def save_user(self, user):
        # Different file access pattern
        with open(f'users/{user.id}.json', 'w') as f:
            json.dump(user.to_dict(), f)
    
    # More data access scattered throughout...
```

#### **Solution: Centralized Repository**
```python
# Business logic uses repository interface
class UserService:
    def __init__(self, user_repository):
        self.repository = user_repository
    
    def get_user(self, user_id):
        return self.repository.get(user_id)  # Clean!
    
    def save_user(self, user):
        self.repository.save(user)  # Consistent!
```

### 3. Repository Interface
A good repository provides **CRUD** operations:
- **C**reate - Add new items
- **R**ead - Retrieve items
- **U**pdate - Modify existing items
- **D**elete - Remove items

Plus query methods:
- `find_by_id()`
- `find_all()`
- `find_by_criteria()`

## 💻 Code Examples

### **Example 1: File-Based Repository**

#### **Without Repository:**
```python
# Data access scattered in business logic
def load_activities():
    with open('activities.json') as f:
        return json.load(f)

def save_activity(activity):
    activities = load_activities()
    activities.append(activity)
    with open('activities.json', 'w') as f:
        json.dump(activities, f)
```

#### **With Repository:**
```python
class ActivityRepository:
    def __init__(self, filepath='activities.json'):
        self.filepath = Path(filepath)
    
    def _load_data(self):
        if not self.filepath.exists():
            return []
        with open(self.filepath) as f:
            return json.load(f)
    
    def _save_data(self, data):
        with open(self.filepath, 'w') as f:
            json.dump(data, f, indent=2)
    
    # Repository interface
    def find_all(self):
        return self._load_data()
    
    def find_by_id(self, activity_id):
        activities = self._load_data()
        for activity in activities:
            if activity['id'] == activity_id:
                return activity
        return None
    
    def save(self, activity):
        activities = self._load_data()
        activities.append(activity)
        self._save_data(activities)
        return activity
    
    def update(self, activity_id, updates):
        activities = self._load_data()
        for i, activity in enumerate(activities):
            if activity['id'] == activity_id:
                activities[i].update(updates)
                self._save_data(activities)
                return activities[i]
        raise ValueError(f"Activity {activity_id} not found")
    
    def delete(self, activity_id):
        activities = self._load_data()
        filtered = [a for a in activities if a['id'] != activity_id]
        if len(filtered) == len(activities):
            raise ValueError(f"Activity {activity_id} not found")
        self._save_data(filtered)
```

### **Example 2: Using the Repository**

#### **Business Logic (Clean):**
```python
class ActivityService:
    def __init__(self, repository):
        self.repository = repository
    
    def log_activity(self, activity_type, duration, notes=""):
        activity = {
            'id': str(uuid.uuid4()),
            'type': activity_type,
            'duration': duration,
            'notes': notes,
            'timestamp': datetime.now().isoformat()
        }
        
        return self.repository.save(activity)
    
    def get_todays_activities(self):
        activities = self.repository.find_all()
        today = datetime.now().date().isoformat()
        
        return [
            a for a in activities
            if a['timestamp'].startswith(today)
        ]
    
    def get_total_time(self, activity_type):
        activities = self.repository.find_all()
        matching = [a for a in activities if a['type'] == activity_type]
        
        return sum(a['duration'] for a in matching)
```

## 🔍 Repository Pattern in Your Code

### **Current Personal History Approach:**
Look at `personal_history/ph/v001/models/activity.py`:

```python
class Activity:
    def __init__(self, activity_type, data=None, duration=None, ...):
        # Model class - good!
        pass
    
    def to_dict(self):
        # Conversion method - good!
        pass
```

**But where's data access?** It's in controllers or mixed elsewhere.

### **Your habits code data access:**
```python
# habits_archive/create.py
def create_file(userdata: Dict, directory_path="./.ph/userfile"):
    # Direct file operations mixed with logic
    target_dir = Path(directory_path)
    target_dir.mkdir(parents=True, exist_ok=True)
    
    file_path = target_dir / f"{filename}.json"
    
    with open(file_path, "w", encoding="utf-8") as f:
        json.dump(profile, f, indent=2)
```

**Problem:** File operations mixed with business logic.

## 🛠️ Hands-On Exercise (15 minutes)

### **Exercise 1: Identify Data Access in Personal History**
Look at your v0.01 code:

1. **Open** `personal_history/ph/v001/controllers/history_controller.py`
2. **Search for:** File operations, data loading/saving
3. **Question:** Is data access separated or mixed?

### **Exercise 2: Design a Repository Interface**
For Personal History activities, design a repository interface:

**What operations would you need?**
```python
class ActivityRepository:
    def save(self, activity): ...
    def find_by_date(self, date): ...
    def find_by_type(self, activity_type): ...
    def get_all(self): ...
    def update(self, activity_id, updates): ...
    # Add more as needed...
```

**Task:** List 5-6 methods that would be useful for Personal History.

### **Exercise 3: Simple Implementation**
Sketch a simple file-based repository:

```python
class FileActivityRepository:
    def __init__(self, data_dir="~/.personal_history"):
        self.data_dir = Path(data_dir).expanduser()
        self.data_dir.mkdir(parents=True, exist_ok=True)
    
    def _get_filepath(self):
        today = datetime.now().strftime("%Y-%m-%d")
        return self.data_dir / f"activities_{today}.json"
    
    def save(self, activity):
        filepath = self._get_filepath()
        # Implement: Load existing, append, save
        pass
```

## 🔄 Apply to Personal History (5 minutes)

### **Current v0.01 Data Flow:**
1. **Activity created** in controller
2. **Added to day** in model
3. **Saved to file** in... where?

**Check:** Look for file writing in:
- `controllers/history_controller.py`
- `models/file.py`
- `core.py`

### **Action Item:**
1. Find where Personal History files are written
2. Note if it's mixed with business logic
3. Think about extracting to a repository

### **Potential Improvement:**
```python
# Current (possibly mixed):
def save_history(history_data, filepath):
    # Mixed: validation + formatting + file I/O
    
# With repository:
class HistoryRepository:
    def save(self, history):
        # Only file I/O here
        pass
    
# Business logic elsewhere:
def process_and_save(history):
    # Validation and processing
    validated = validate_history(history)
    formatted = format_for_storage(validated)
    # Repository handles storage
    return repository.save(formatted)
```

## 📝 Review & Next Steps (5 minutes)

### **Key Takeaways:**
1. **Repository pattern** separates data access from business logic
2. **CRUD interface** provides consistent data operations
3. **Abstraction** allows switching data sources (files → database)
4. **Centralization** makes data access code easier to maintain

### **Benefits for Personal History:**
1. **Cleaner controllers** - No file operations mixed with logic
2. **Easier testing** - Mock repository for unit tests
3. **Flexible storage** - Could switch from JSON files to SQLite
4. **Consistent interface** - Same methods for all data access

### **Tomorrow's Preview:**
**Day 4:** Service Layer - We'll learn about organizing business logic

### **Homework (Optional):**
1. Look for all file I/O in your Personal History code
2. Note which files/functions do data access
3. Sketch a repository interface that would cover all needs

## 🎯 Success Checklist
- [ ] Understand Repository pattern purpose
- [ ] Can identify data access in code
- [ ] See benefits for Personal History
- [ ] Can design simple repository interface

## 💡 Pro Tip
**Start with interface:** Design the repository methods you need first, then implement. This ensures your business logic stays clean regardless of implementation details.

---
**Time Spent:** [ ] 30-45 minutes  
**Confidence Level:** [ ] Low [ ] Medium [ ] High  
**Applied to PH:** [ ] Yes [ ] No

*Use Personal History to track your learning progress!*