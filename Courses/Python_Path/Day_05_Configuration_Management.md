# Week 1: Architecture Fundamentals - Day 5
# Configuration Management

* [Syllabus](./Syllabus.md)
* [Previous: Day 4](./Day_04_Service_Layer.md)
* [Next: Week 2: Day 6](./Day_06_Custom_Exceptions.md)

## 🎯 30-Minute Learning Objectives
By the end of this session, you will:
* Understand configuration management principles
* Implement environment-based configuration
* Create configuration classes
* Fix configuration issues in Personal History

## ⏰ Session Timeline
```
5 min: Review Service Layer
10 min: Learn Configuration Patterns  
15 min: Implement Config Class
5 min: Apply to Personal History
5 min: Review & Next Steps
```

## 📚 Core Concepts

### 1. What is Configuration Management?
**Configuration** = Settings that change based on environment:
- Development vs Production
- Different users/machines
- API keys, file paths, feature flags

**Problem:** Hardcoded values scattered through code
```python
# Bad: Hardcoded everywhere
DB_PATH = "/home/user/data.db"
LOG_FILE = "./app.log"
API_KEY = "secret123"
MAX_RETRIES = 3
```

### 2. Configuration Sources (Priority Order):
```
1. Command Line Arguments (highest priority)
2. Environment Variables
3. Configuration Files
4. Default Values (lowest priority)
```

### 3. Common Problems in Your Code:

#### **Problem 1: Hardcoded Paths**
```python
# habits_archive/config.py
PY_FILE_LOCATION = "./.ph/userfile"  # ❌ Hardcoded

# db.py  
DIR_LOCATION = "/home/${USER}/.local/share/"  # ❌ Won't expand!
```

#### **Problem 2: No Environment Support**
```python
# Can't change for different environments
# Development: "./.ph/userfile"
# Production: "/var/lib/personal_history/"
# Testing: "/tmp/test_ph/"
```

#### **Problem 3: Mixed Configuration**
```python
# Configuration scattered
def some_function():
    timeout = 30  # ❌ Buried in code
    retries = 3   # ❌ Not configurable
```

## 💻 Code Examples

### **Example 1: Basic Configuration Class**

#### **Before: Hardcoded Values**
```python
# Scattered throughout code
DATA_DIR = "./data"
LOG_LEVEL = "INFO"
DB_URL = "sqlite:///app.db"
MAX_FILE_SIZE = 1024 * 1024  # 1MB
```

#### **After: Configuration Class**
```python
import os
from pathlib import Path
from typing import Optional
from dataclasses import dataclass

@dataclass
class AppConfig:
    """Centralized configuration management"""
    
    # Default values
    data_dir: Path = Path("./data")
    log_level: str = "INFO"
    db_url: str = "sqlite:///app.db"
    max_file_size: int = 1024 * 1024  # 1MB
    debug: bool = False
    
    @classmethod
    def from_env(cls):
        """Create config from environment variables"""
        return cls(
            data_dir=Path(os.getenv("PH_DATA_DIR", "./data")),
            log_level=os.getenv("PH_LOG_LEVEL", "INFO").upper(),
            db_url=os.getenv("PH_DB_URL", "sqlite:///app.db"),
            max_file_size=int(os.getenv("PH_MAX_FILE_SIZE", "1048576")),
            debug=os.getenv("PH_DEBUG", "false").lower() == "true"
        )
    
    def validate(self):
        """Validate configuration"""
        if not self.data_dir:
            raise ValueError("data_dir must be set")
        
        if self.log_level not in ["DEBUG", "INFO", "WARNING", "ERROR"]:
            raise ValueError(f"Invalid log level: {self.log_level}")
        
        if self.max_file_size <= 0:
            raise ValueError("max_file_size must be positive")
        
        # Ensure data directory exists
        self.data_dir.mkdir(parents=True, exist_ok=True)
        
        return self

# Usage
config = AppConfig.from_env().validate()
print(f"Data directory: {config.data_dir}")
print(f"Log level: {config.log_level}")
```

### **Example 2: Multi-Environment Configuration**

```python
import json
import yaml  # pip install pyyaml
from enum import Enum
from pathlib import Path

class Environment(Enum):
    DEVELOPMENT = "development"
    TESTING = "testing"
    PRODUCTION = "production"

class ConfigManager:
    def __init__(self, env: Optional[Environment] = None):
        self.env = env or self._detect_environment()
        self.config = self._load_config()
    
    def _detect_environment(self) -> Environment:
        """Detect environment from variable"""
        env_str = os.getenv("PH_ENV", "development").lower()
        
        try:
            return Environment(env_str)
        except ValueError:
            return Environment.DEVELOPMENT
    
    def _load_config(self) -> dict:
        """Load configuration with fallbacks"""
        config = {}
        
        # 1. Load defaults
        config.update(self._load_defaults())
        
        # 2. Load environment-specific config
        env_config = self._load_environment_config()
        config.update(env_config)
        
        # 3. Override with environment variables
        config.update(self._load_env_vars())
        
        return config
    
    def _load_defaults(self) -> dict:
        """Default configuration"""
        return {
            "data_dir": Path.home() / ".personal_history",
            "log_level": "INFO",
            "log_file": "ph.log",
            "crypto_algorithm": "sha256",
            "max_activities_per_day": 50,
            "backup_enabled": True,
            "backup_count": 7,
        }
    
    def _load_environment_config(self) -> dict:
        """Load from config file if exists"""
        config_file = Path(f"config/{self.env.value}.json")
        
        if config_file.exists():
            with open(config_file) as f:
                return json.load(f)
        
        # Try YAML
        yaml_file = Path(f"config/{self.env.value}.yaml")
        if yaml_file.exists():
            with open(yaml_file) as f:
                return yaml.safe_load(f)
        
        return {}
    
    def _load_env_vars(self) -> dict:
        """Load from environment variables with PH_ prefix"""
        config = {}
        
        # Map environment variables to config keys
        env_mappings = {
            "PH_DATA_DIR": "data_dir",
            "PH_LOG_LEVEL": "log_level",
            "PH_LOG_FILE": "log_file",
            "PH_DEBUG": "debug",
        }
        
        for env_var, config_key in env_mappings.items():
            value = os.getenv(env_var)
            if value is not None:
                # Convert string to appropriate type
                if config_key == "data_dir":
                    config[config_key] = Path(value)
                elif config_key == "debug":
                    config[config_key] = value.lower() == "true"
                else:
                    config[config_key] = value
        
        return config
    
    def get(self, key, default=None):
        """Get configuration value"""
        return self.config.get(key, default)
    
    @property
    def data_dir(self) -> Path:
        return Path(self.config["data_dir"])
    
    @property
    def log_level(self) -> str:
        return self.config["log_level"]

# Usage
config = ConfigManager()
print(f"Environment: {config.env.value}")
print(f"Data dir: {config.data_dir}")
print(f"Log file: {config.get('log_file')}")
```

### **Example 3: Simple Configuration for Personal History**

```python
import os
from pathlib import Path
from dataclasses import dataclass

@dataclass
class PHConfig:
    """Personal History Configuration"""
    
    # Core settings
    data_dir: Path
    identity_file: Path
    history_file: Path
    pending_file: Path
    
    # Application settings
    log_level: str = "INFO"
    crypto_algorithm: str = "sha256"
    hash_chain_seed: str = "personal-history-v001"
    
    # Feature flags
    enable_backup: bool = True
    enable_analytics: bool = False
    strict_validation: bool = True
    
    @classmethod
    def create(cls, data_dir: Optional[str] = None):
        """Create configuration with sensible defaults"""
        
        # Determine data directory
        if data_dir:
            base_dir = Path(data_dir)
        else:
            base_dir = Path.home() / ".personal_history"
        
        # Ensure directory exists
        base_dir.mkdir(parents=True, exist_ok=True)
        
        return cls(
            data_dir=base_dir,
            identity_file=base_dir / "identity.json",
            history_file=base_dir / "history.ph.json",
            pending_file=base_dir / "pending.json",
            log_level=os.getenv("PH_LOG_LEVEL", "INFO"),
            enable_backup=os.getenv("PH_ENABLE_BACKUP", "true").lower() == "true",
        )
    
    def validate(self):
        """Validate configuration"""
        # Check directories
        if not self.data_dir.exists():
            self.data_dir.mkdir(parents=True)
        
        # Check permissions
        if not os.access(self.data_dir, os.W_OK):
            raise PermissionError(f"Cannot write to {self.data_dir}")
        
        # Validate settings
        if self.log_level not in ["DEBUG", "INFO", "WARNING", "ERROR"]:
            raise ValueError(f"Invalid log level: {self.log_level}")
        
        return self

# Usage in application
config = PHConfig.create().validate()

# Use in repository
class ActivityRepository:
    def __init__(self, config: PHConfig):
        self.config = config
        self.data_file = config.data_dir / "activities.json"
```

## 🔍 Configuration Issues in Your Code

### **Current Personal History Configuration:**
Look at your code:

1. **`habits_archive/config.py`:**
   ```python
   PY_FILE_LOCATION = "./.ph/userfile"  # ❌ Hardcoded relative path
   ```

2. **`db.py`:**
   ```python
   DIR_LOCATION = "/home/${USER}/.local/share/"  # ❌ ${USER} won't expand!
   ```

3. **Missing:** Environment variable support
4. **Missing:** Configuration validation
5. **Missing:** Different environments support

### **Your v0.01 Improvement:**
Check if v0.01 has better configuration:
- Look for configuration in `core.py` or other files
- Check if paths are configurable
- Look for environment variable usage

## 🛠️ Hands-On Exercise (15 minutes)

### **Exercise 1: Fix the ${USER} Issue**
The problem in `db.py`:
```python
DIR_LOCATION = "/home/${USER}/.local/share/"  # Won't work!
```

**Solutions:**
```python
# Option 1: Use os.path.expanduser
import os
DIR_LOCATION = os.path.expanduser("~/.local/share/")

# Option 2: Use pathlib with expanduser
from pathlib import Path
DIR_LOCATION = Path.home() / ".local" / "share"

# Option 3: Configurable with fallback
DATA_DIR = os.getenv("PH_DATA_DIR", str(Path.home() / ".local" / "share"))
```

**Task:** Choose the best solution and explain why.

### **Exercise 2: Design Personal History Config**
Design a configuration class for Personal History:

**What needs to be configurable?**
1. Data directory location
2. Logging settings
3. Cryptographic settings
4. Feature flags
5. File paths

**Sketch the class:**
```python
class PersonalHistoryConfig:
    def __init__(self):
        self.data_dir = ...  # How to determine?
        self.log_level = ...
        self.hash_algorithm = ...
        # Add more...
    
    @classmethod
    def from_env(cls):
        # Load from environment variables
        pass
```

### **Exercise 3: Create Simple Config**
Implement a simple version:

```python
import os
from pathlib import Path

def get_ph_config():
    """Simple configuration getter"""
    data_dir = Path(os.getenv("PH_DATA_DIR", "~/.personal_history"))
    data_dir = data_dir.expanduser()  # Expands ~ to home directory
    
    return {
        "data_dir": data_dir,
        "log_level": os.getenv("PH_LOG_LEVEL", "INFO"),
        "debug": os.getenv("PH_DEBUG", "false").lower() == "true",
    }
```

## 🔄 Apply to Personal History (5 minutes)

### **Current Configuration Issues:**
1. **Hardcoded paths** in habits code
2. **Environment variable** `${USER}` that won't expand
3. **No configuration validation**
4. **Mixed concerns** - configuration scattered

### **Action Item:**
1. Create a `config.py` file for Personal History v0.01
2. Move all configuration there
3. Add environment variable support
4. Add validation

### **Simple Implementation:**
```python
# personal_history/ph/v001/config.py
import os
from pathlib import Path
from dataclasses import dataclass

@dataclass
class PHConfig:
    data_dir: Path = Path.home() / ".personal_history"
    log_level: str = "INFO"
    
    @classmethod
    def load(cls):
        data_dir = Path(os.getenv("PH_DATA_DIR", "~/.personal_history"))
        return cls(
            data_dir=data_dir.expanduser(),
            log_level=os.getenv("PH_LOG_LEVEL", "INFO")
        )

# Usage in other files:
from .config import PHConfig
config = PHConfig.load()
```

## 📝 Review & Next Steps (5 minutes)

### **Key Takeaways:**
1. **Never hardcode** paths or settings
2. **Use environment variables** for different environments
3. **Centralize configuration** in one place
4. **Validate configuration** at startup
5. **Use Path objects** for file paths (not strings)

### **Benefits for Personal History:**
1. **Works everywhere** - Home directory, different users, servers
2. **Environment-specific** - Development vs production
3. **Easy to change** - Modify environment variables, not code
4. **Validation** - Catch configuration errors early

### **Week 1 Complete!**
You've learned:
- **Day 1:** MVC Pattern Theory
- **Day 2:** MVC Implementation
- **Day 3:** Repository Pattern  
- **Day 4:** Service Layer
- **Day 5:** Configuration Management

### **Next Week Preview:**
**Week 2:** Error Handling & Validation
- Day 6: Custom Exceptions
- Day 7: Comprehensive Error Handling
- Day 8: Input Validation Strategies
- Day 9: Data Validation Patterns
- Day 10: Error Recovery & Logging

### **Homework (Optional):**
1. Fix the `${USER}` issue in your habits code
2. Create a simple configuration class for Personal History
3. Move one hardcoded value to configuration

## 🎯 Success Checklist
- [ ] Understand configuration management principles
- [ ] Can identify configuration issues in code
- [ ] Know how to fix `${USER}` problem
- [ ] Can design simple configuration class

## 💡 Pro Tip
**Use `Path.home()`** instead of string manipulation for home directory. It works cross-platform and handles edge cases.

---
**Time Spent:** [ ] 30-45 minutes  
**Confidence Level:** [ ] Low [ ] Medium [ ] High  
**Applied to PH:** [ ] Yes [ ] No

*Congratulations on completing Week 1!* 🎉