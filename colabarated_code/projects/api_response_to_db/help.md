Here's a complete Flask project structure to achieve this:

* The Flask app will fetch a random joke from `https://official-joke-api.appspot.com/random_joke`.
* It will store the joke in MongoDB.
* The app will expose an endpoint (`/fetch_and_store`) that, when hit, triggers the fetch and storage process.

---

### 📂 Project Structure:

```
flask-joke-app/
│── app/
│   │── __init__.py
│   │── config.py
│   │── database.py
│   │── models.py
│   │── routes.py
│── run.py
│── requirements.txt
│── .env
│── README.md
```

---

### 📝 `requirements.txt`

```txt
Flask
pymongo
requests
python-dotenv
```

---

### 🛠 `app/__init__.py`

```python
from flask import Flask
from app.database import mongo
from app.routes import joke_routes

def create_app():
    app = Flask(__name__)

    # Load MongoDB Config
    app.config.from_object('app.config')

    # Initialize MongoDB
    mongo.init_app(app)

    # Register Routes
    app.register_blueprint(joke_routes)

    return app
```

---

### 🛠 `app/config.py`

```python
import os
from dotenv import load_dotenv

load_dotenv()

class Config:
    MONGO_URI = os.getenv("MONGO_URI", "mongodb://localhost:27017/jokesdb")
```

---

### 🛠 `.env`

```env
MONGO_URI=mongodb://localhost:27017/jokesdb
```

---

### 🛠 `app/database.py`

```python
from flask_pymongo import PyMongo

mongo = PyMongo()
```

---

### 🛠 `app/models.py`

```python
from app.database import mongo

def save_joke(joke_data):
    """Saves a joke to MongoDB"""
    jokes_collection = mongo.db.jokes
    jokes_collection.insert_one(joke_data)
```

---

### 🛠 `app/routes.py`

```python
from flask import Blueprint, jsonify
import requests
from app.models import save_joke

joke_routes = Blueprint("jokes", __name__)

@joke_routes.route('/fetch_and_store', methods=['GET'])
def fetch_and_store():
    """Fetches a joke and stores it in MongoDB"""
    response = requests.get("https://official-joke-api.appspot.com/random_joke")
  
    if response.status_code == 200:
        joke_data = response.json()
        save_joke(joke_data)
        return jsonify({"message": "Joke saved successfully", "joke": joke_data}), 201
    else:
        return jsonify({"error": "Failed to fetch joke"}), 500
```

---

### 🛠 `run.py`

```python
from app import create_app

app = create_app()

if __name__ == "__main__":
    app.run(debug=True)
```

---

### 🚀 How to Run:

1. **Install Dependencies**
   ```sh
   pip install -r requirements.txt
   ```
2. **Run MongoDB Locally**
   ```sh
   mongod --dbpath /path/to/data/directory
   ```
3. **Start Flask App**
   ```sh
   python run.py
   ```
4. **Test API**
   ```sh
   curl http://127.0.0.1:5000/fetch_and_store
   ```

This will fetch a random joke and store it in MongoDB. 🎉
