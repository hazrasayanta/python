Here’s how you can **read a CSV file and insert its data into a MongoDB database** using Python.

---

## 📁 **Folder Structure**

```
csv_to_db_project/
│── main.py                 # Main script
│── requirements.txt        # Dependencies
│── config.py               # Configuration settings (MongoDB URI, folder path)
│── utils/
│   │── __init__.py         # Makes `utils` a package
│   │── csv_to_db.py        # Function to insert CSV data into MongoDB
│   │── mongo_connect.py    # MongoDB connection setup
│── data/                   # Store CSV files here
```

---

## 1️⃣ **Install Dependencies**

Add this to `requirements.txt`:

```
pandas
pymongo
```

Install using:

```sh
pip install -r requirements.txt
```

---

## 2️⃣ **`config.py`** (Configuration settings)

```python
MONGO_URI = "mongodb://localhost:27017/"
DB_NAME = "mydatabase"
COLLECTION_NAME = "csv_data"
CSV_FOLDER = "./data"
```

---

## 3️⃣ **`utils/mongo_connect.py`** (MongoDB Connection)

```python
from pymongo import MongoClient
from config import MONGO_URI, DB_NAME

def connect_to_mongo():
    client = MongoClient(MONGO_URI)
    db = client[DB_NAME]
    return db
```

---

## 4️⃣ **`utils/csv_to_db.py`** (Insert CSV Data into MongoDB)

```python
import pandas as pd
import os
from utils.mongo_connect import connect_to_mongo
from config import COLLECTION_NAME

def csv_to_mongo(csv_file):
    db = connect_to_mongo()
    collection = db[COLLECTION_NAME]
  
    # Read CSV into DataFrame
    df = pd.read_csv(csv_file)
  
    # Convert DataFrame to dictionary
    data = df.to_dict(orient="records")

    # Insert into MongoDB
    if data:
        collection.insert_many(data)
        print(f"Inserted {len(data)} records from {csv_file} into MongoDB.")
    else:
        print(f"No data found in {csv_file}.")
```

---

## 5️⃣ **`main.py`** (Run Everything)

```python
import os
from utils.csv_to_db import csv_to_mongo
from config import CSV_FOLDER

if __name__ == "__main__":
    for file in os.listdir(CSV_FOLDER):
        if file.endswith(".csv"):
            file_path = os.path.join(CSV_FOLDER, file)
            print(f"Processing {file_path}...")
            csv_to_mongo(file_path)
```

---

## 🎯 **How It Works**

1. **Reads a CSV file** from the `data/` folder.
2. **Converts CSV data into a dictionary** .
3. **Inserts data into a MongoDB collection** .

Let me know if you need modifications! 🚀
