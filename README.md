# Simple API using PythonAnywhere.com
- This is a simple API using [PythonAnywhere.com](https://www.pythonanywhere.com/) platform
- This API will select 5 random names from the list given. The lists of names will be sent by POST method from the local server.
- You will need 2 differents server for this. 1 local server and 1 API server.
- Deploy `sel-rand-names.py` at local server, and the following configuration at [PythonAnywhere.com](https://www.pythonanywhere.com)
- A node can use the API to send a list of names and retrieve 5 random names as the output. See demo.

## WSGI Configuration in PythonAnywhere
```python
import sys

path = '/home/yourusername/app-path'
if path not in sys.path:
    sys.path.append(path)

# Import aplikasi Flask
from app import app as application
```

## `App.py` in PythonAnywhere

This is `app.py` source code file. Should be deploy at API server.

```python
from flask import Flask, request, jsonify
import random

app = Flask(__name__)

@app.route('/random-names', methods=['POST'])
def random_names():
    data = request.json
    names = data.get("names", [])
    if not names or len(names) < 5:
        return jsonify({"error": "Senarai nama mestilah sekurang-kurangnya 5"}), 400

    selected_names = random.sample(names, 5)
    return jsonify({"selected_names": selected_names})

if __name__ == "__main__":
    app.run()
```

## File Structure

This is the example of file structure in PythonAnywhere:
```plaintext
/home/riszaf601/random-names/
├── app.py
```

## Demo URL
[Link to Simple API](https://simple-api-using-pythonanywhere-xaj2hcge4thvgjzk3xuvwa.streamlit.app/)


### Show some love!
[![Buy Me a Coffee](https://img.buymeacoffee.com/button-api/?text=Buy%20me%20a%20coffee&emoji=☕&slug=suriyakame&button_colour=FFDD00&font_colour=000000&font_family=Cookie&outline_colour=000000&coffee_colour=ffffff)](https://buymeacoffee.com/suriyakame)

