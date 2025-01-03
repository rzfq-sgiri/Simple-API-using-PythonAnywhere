# Simple API
- This is a simple API using [pythonanywhere](https://www.pythonanywhere.com/) platform
- This API will select 5 random names from the list given
- A node can use the API to send a list of names and retrieve 5 random names as the output.

## WSGI Configuration
```python
import sys

path = '/home/yourusername/app-path'
if path not in sys.path:
    sys.path.append(path)

# Import aplikasi Flask
from app import app as application
```

## App.py in PythonAnywhere
```python
from flask import Flask, request, jsonify
import random

app = Flask(__name__)

@app.route('/random-names', methods=['POST'])
def random_names():
    data = request.json
    names = data.get("names", [])
    if not names or len(names) < 10:
        return jsonify({"error": "Senarai nama mestilah sekurang-kurangnya 10"}), 400

    selected_names = random.sample(names, 5)
    return jsonify({"selected_names": selected_names})

if __name__ == "__main__":
    app.run()
```

## Demo URL
[Link to Simple API](https://simple-api-using-pythonanywhere-xaj2hcge4thvgjzk3xuvwa.streamlit.app/)
