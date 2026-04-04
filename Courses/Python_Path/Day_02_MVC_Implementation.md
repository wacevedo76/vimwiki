# Week 1: Architecture Fundamentals - Day 2
# MVC Implementation - Separating Concerns

* [Syllabus](./Syllabus.md)
* [Previous: Day 1](./Day_01_MVC_Pattern_Theory.md)
* [Next: Day 3](./Day_03_Repository_Pattern.md)

## 🎯 30-Minute Learning Objectives
By the end of this session, you will:
* Practice separating mixed responsibilities
* Refactor a function into MVC components
* Understand dependency injection
* Apply MVC to Personal History code

## ⏰ Session Timeline
```
5 min: Review MVC Concepts
10 min: Learn Separation Techniques  
15 min: Hands-On Refactoring
5 min: Apply to Personal History
5 min: Review & Next Steps
```

## 📚 Core Concepts

### 1. Identifying Mixed Responsibilities
**Problem Code** does multiple things:
```python
def process_user_data(data):
    # 1. Validate input (Controller/Model)
    if not data.get('name'):
        print("Error: Name required")  # 2. Display error (View)
    
    # 3. Process data (Model)
    processed = data['value'] * 2
    
    # 4. Format output (View)
    print(f"Result: {processed}")
    
    # 5. Save to file (Model)
    with open('output.txt', 'w') as f:
        f.write(str(processed))
    
    return processed
```

**Three responsibilities mixed:** Validation/processing, Display, File I/O

### 2. Separation Techniques

#### **Technique 1: Extract Model Methods**
```python
# Before:
def calculate_and_save(data):
    result = data * 2  # Business logic
    save_to_file(result)  # Data persistence
    return result

# After:
class CalculatorModel:
    def calculate(self, data):  # Pure business logic
        return data * 2
    
    def save_result(self, result):  # Data persistence
        with open('output.txt', 'w') as f:
            f.write(str(result))
```

#### **Technique 2: Extract View Methods**
```python
# Before:
def handle_user(data):
    # ... processing ...
    print(f"Result: {result}")  # Mixed with logic
    
# After:
class ResultView:
    def display_result(self, result):
        print(f"Result: {result}")
    
    def display_error(self, message):
        print(f"Error: {message}")
```

#### **Technique 3: Controller Coordination**
```python
class UserController:
    def __init__(self, model, view):
        self.model = model
        self.view = view
    
    def process_data(self, user_input):
        try:
            # 1. Validate (could be in Model)
            validated = self.validate_input(user_input)
            
            # 2. Process (Model)
            result = self.model.calculate(validated)
            
            # 3. Save (Model)
            self.model.save_result(result)
            
            # 4. Display (View)
            self.view.display_result(result)
            
        except ValueError as e:
            # Error handling with View
            self.view.display_error(str(e))
```

### 3. Dependency Injection
**Instead of:** Creating dependencies inside classes
```python
class UserController:
    def __init__(self):
        self.model = CalculatorModel()  # Hardcoded dependency
        self.view = ResultView()        # Hardcoded dependency
```

**Use:** Pass dependencies as parameters
```python
class UserController:
    def __init__(self, model, view):  # Dependencies injected
        self.model = model
        self.view = view
```

**Benefits:**
- Easier testing (can pass mock objects)
- More flexible (swap implementations)
- Clearer dependencies

## 💻 Code Transformation Example

### **Before: Monolithic Function** (from your habits code)
```python
def create_file(userdata: Dict, directory_path="./.ph/userfile"):
    # Mixed responsibilities:
    # 1. Unpack data (Controller)
    # 2. Create filename (Model/View?)
    # 3. Check file existence (Model)
    # 4. Construct data (Model)
    # 5. Write file (Model)
    # 6. Print message (View)
    
    user_raw_data, user_hashes, filename = (
        userdata["user_raw_data"], 
        userdata["user_hashes"], 
        userdata["filename"]
    )
    
    target_dir = Path(directory_path)
    target_dir.mkdir(parents=True, exist_ok=True)
    
    file_path = target_dir / f"{filename}.json"
    
    if file_path.exists():
        print(f"Warning: {file_path} already exists.")  # View
        return None
    
    profile = {  # Model
        "epoch_time": user_raw_data["epoch_time"],
        # ... more data construction
    }
    
    with open(file_path, "w", encoding="utf-8") as f:  # Model
        json.dump(profile, f, indent=2)
    
    print(f"File created: {file_path}")  # View
    return str(file_path)
```

### **After: Separated MVC**

#### **Model (data_model.py)**
```python
class FileModel:
    def __init__(self, data_dir="./.ph/userfile"):
        self.data_dir = Path(data_dir)
    
    def ensure_directory(self):
        self.data_dir.mkdir(parents=True, exist_ok=True)
    
    def file_exists(self, filename):
        file_path = self.data_dir / f"{filename}.json"
        return file_path.exists()
    
    def construct_profile(self, user_raw_data, user_hashes):
        return {
            "epoch_time": user_raw_data["epoch_time"],
            "creation_time": user_raw_data["creation_time"],
            # ... data construction
        }
    
    def save_profile(self, filename, profile_data):
        file_path = self.data_dir / f"{filename}.json"
        with open(file_path, "w", encoding="utf-8") as f:
            json.dump(profile_data, f, indent=2)
        return str(file_path)
```

#### **View (file_view.py)**
```python
class FileView:
    def show_warning(self, filepath):
        print(f"Warning: {filepath} already exists.")
    
    def show_success(self, filepath):
        print(f"File created: {filepath}")
    
    def show_error(self, message):
        print(f"Error: {message}")
```

#### **Controller (file_controller.py)**
```python
class FileController:
    def __init__(self, model, view):
        self.model = model
        self.view = view
    
    def create_file(self, userdata):
        try:
            # Unpack data
            user_raw_data = userdata["user_raw_data"]
            user_hashes = userdata["user_hashes"]
            filename = userdata["filename"]
            
            # Model operations
            self.model.ensure_directory()
            
            if self.model.file_exists(filename):
                self.view.show_warning(filename)
                return None
            
            profile = self.model.construct_profile(user_raw_data, user_hashes)
            filepath = self.model.save_profile(filename, profile)
            
            # View operation
            self.view.show_success(filepath)
            return filepath
            
        except Exception as e:
            self.view.show_error(str(e))
            raise
```

## 🛠️ Hands-On Exercise (15 minutes)

### **Exercise 1: Analyze `generate_hash_values`**
Open `habits_archive/create.py` and examine:
```python
def generate_hash_values(firstname: str, lastname: str, tax_id: str, password: str) -> Dict:
```

**Identify responsibilities:**
1. **Data processing:** Hashing values ✓ (Model)
2. **Time conversion:** `_certs()` helper ✓ (Model/Utility)
3. **Data construction:** Building dictionaries ✓ (Model)
4. **Formatting:** String formatting? (View)

**Task:** How would you separate this?

### **Exercise 2: Plan Refactoring**
Create a simple refactoring plan:

**Current:** One function doing everything
```python
def generate_hash_values(...):
    # hashing + time conversion + dict building
```

**Proposed:**
```
hash_model.py:
  - HashGenerator (handles SHA-256)
  - TimeConverter (handles epoch conversion)
  - DataBuilder (constructs dictionaries)

hash_controller.py:
  - Coordinates the three model classes
  - Handles input validation
```

## 🔄 Apply to Personal History (5 minutes)

### **Review Your v0.01 Structure:**
Look at `personal_history/ph/v001/models/identity.py`

**Notice:**
1. Clean `Identity` class (Model)
2. Separate responsibilities
3. Clear methods for each operation

### **Compare with habits code:**
1. **habits/create.py:** 186 lines, mixed responsibilities
2. **v001/models/identity.py:** ~50 lines, focused Model

### **Action Item:**
1. Open both files side by side
2. Notice the improvement in separation
3. Identify one habit function that could use similar refactoring

## 📝 Review & Next Steps (5 minutes)

### **Key Takeaways:**
1. **Separate by responsibility:** Data, Display, Coordination
2. **Dependency Injection:** Pass dependencies, don't create them
3. **Your v0.01** shows good separation already
4. **Refactoring** improves testability and maintainability

### **Tomorrow's Preview:**
**Day 3:** Repository Pattern - We'll learn about data access layers

### **Homework (Optional):**
1. Pick one small function from habits code
2. Sketch how to separate into Model/View/Controller
3. Don't implement yet - just plan

## 🎯 Success Checklist
- [ ] Can identify mixed responsibilities in code
- [ ] Understand separation techniques
- [ ] See value of dependency injection
- [ ] Recognize MVC improvements in v0.01

## 💡 Pro Tip
**Start small:** When refactoring, extract one responsibility at a time. Test after each extraction to ensure nothing breaks.

---
**Time Spent:** [ ] 30-45 minutes  
**Confidence Level:** [ ] Low [ ] Medium [ ] High  
**Applied to PH:** [ ] Yes [ ] No

*Track your learning in Personal History!*