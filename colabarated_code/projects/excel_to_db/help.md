Here’s a structured folder setup for your Python project:

```
excel_to_json_project/
│── main.py                 # Main script to run
│── requirements.txt        # Dependencies
│── config.py               # Configuration settings (MongoDB URI, folder path)
│── utils/
│   │── __init__.py         # Makes `utils` a package
│   │── excel_to_json.py    # Function to convert Excel to JSON
│   │── mongo_connect.py    # MongoDB connection setup
│   │── hash_util.py        # Hashing function
│   │── folder_watcher.py   # Folder monitoring
│── data/                   # Store Excel files here
│── output/                 # Store generated JSON files here
```

---

### 1️⃣ **`requirements.txt`** (Dependencies)

```
pandas
openpyxl
pymongo
```

Install using:

```sh
pip install -r requirements.txt
```

---

### 2️⃣ **`config.py`** (Configuration settings)

```python
MONGO_URI = "mongodb://localhost:27017/"
DB_NAME = "mydatabase"
WATCH_FOLDER = "./data"
```

---

### 3️⃣ **`utils/excel_to_json.py`** (Convert Excel to JSON)

```python
import pandas as pd
import json
import os

def excel_to_json(excel_file, output_dir="./output"):
    df = pd.read_excel(excel_file)
    json_data = df.to_json(orient="records", indent=4)
  
    # Save JSON to file
    json_filename = os.path.join(output_dir, os.path.splitext(os.path.basename(excel_file))[0] + ".json")
    with open(json_filename, "w") as f:
        f.write(json_data)
  
    return json_filename
```

---

### 4️⃣ **`utils/mongo_connect.py`** (MongoDB Connection)

```python
from pymongo import MongoClient
from config import MONGO_URI, DB_NAME

def connect_to_mongo():
    client = MongoClient(MONGO_URI)
    db = client[DB_NAME]
    return db
```

---

### 5️⃣ **`utils/hash_util.py`** (Create Hash from JSON String)

```python
import json
import hashlib

def create_json_hash(data):
    json_string = json.dumps(data, sort_keys=True)
    return hashlib.sha256(json_string.encode()).hexdigest()
```

---

### 6️⃣ **`utils/folder_watcher.py`** (Monitor Folder for New Files)

```python
import os
import time
from utils.excel_to_json import excel_to_json
from config import WATCH_FOLDER

def watch_folder():
    seen_files = set(os.listdir(WATCH_FOLDER))
    print(f"Watching folder: {WATCH_FOLDER}")

    while True:
        current_files = set(os.listdir(WATCH_FOLDER))
        new_files = current_files - seen_files

        for new_file in new_files:
            if new_file.endswith(".xlsx"):  # Process only Excel files
                file_path = os.path.join(WATCH_FOLDER, new_file)
                print(f"Processing new file: {new_file}")
                excel_to_json(file_path)

        seen_files = current_files  # Update seen files
        time.sleep(2)

```

---

### 7️⃣ **`main.py`** (Run Everything)

```python
import threading
from utils.folder_watcher import watch_folder
from utils.mongo_connect import connect_to_mongo

if __name__ == "__main__":
    # Start watching folder in a separate thread
    watcher_thread = threading.Thread(target=watch_folder, daemon=True)
    watcher_thread.start()

    # Connect to MongoDB
    db = connect_to_mongo()
    print("Connected to MongoDB:", db.name)

    # Keep main thread alive
    while True:
        time.sleep(10)
```

---

### 🎯 **How It Works**

1. **Watch for new Excel files** in `data/`
2. **Convert Excel to JSON** and save to `output/`
3. **Hash the JSON** (if needed for verification)
4. **Store JSON in MongoDB** (extend as needed)

Let me know if you need tweaks! 🚀
