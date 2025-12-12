- [Flask Terminology](#flask-terminology)
  - [`route(rule, **options)`](#routerule-options)
  - [`get(rule, **option)`](#getrule-option)
  - [JSON](#json)
- [Flask REST API](#flask-rest-api)
  - [First REST API](#first-rest-api)
- [Flask CLI](#flask-cli)
  - [flask run](#flask-run)

# Flask Terminology

## `route(rule, **options)`

- Decorate a view function to register it with the given URL rule and options
- The endpoint decorator `@app.route("/")` registers the route's endpoint with Flask.

```
from flask import Flask

app = Flask(__name__)

@app.route("/")
def home():
    return "Hello"

```

## `get(rule, **option)`

- Shortcut for route() with methods=["GET"].

```
@app.get("/store")
def get_stores():
    return {"stores": stores}
```

## JSON

```
{
    "key": "value",
    "another": 25,
    "listic_data": [
        1,
        3,
        7
    ],
    "sub_objects": {
        "name": "Rolf",
        "age": 25
    }
}
```

- So at its core, you've got:
  - Strings
  - Numbers
  - Booleans (true or false)
  - Lists
  - Objects (akin to dictionaries in Python). Note that objects are not ordered, so the keys could come back in any order. This is not a problem!
- When we return a Python dictionary in a Flask route, Flask automatically turns it into JSON for us, so we don't have to. Remember that "turning it into JSON" means two things:
  - Change Python keywords and values so they match the JSON standard (e.g. True to true).
  - Turn the whole thing into a single string that our API can return.

# Flask REST API

## First REST API

```
from flask import Flask

app = Flask(__name__)

stores = [{"name": "My Store", "items": [{"name": "my item", "price": 15.99}]}]

@app.get("/store")
def get_stores():
    return {"stores": stores}
```

# Flask CLI

## flask run

- Run web application
