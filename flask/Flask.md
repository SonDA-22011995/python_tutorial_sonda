- [Flask Terminology](#flask-terminology)
  - [`class flask.Flask`](#class-flaskflask)
    - [About the First Parameter - `import_name`](#about-the-first-parameter---import_name)
    - [`route(rule, **options)`](#routerule-options)
    - [`get(rule, **option)`](#getrule-option)
    - [`post(rule, **options)`](#postrule-options)
  - [](#)
- [Flask REST API](#flask-rest-api)
  - [First REST API](#first-rest-api)
- [Flask CLI](#flask-cli)
  - [flask run](#flask-run)
- [JSON](#json)

# Flask Terminology

## `class flask.Flask`

- class flask.Flask(import_name, static_url_path=None, static_folder='static', static_host=None, host_matching=False, subdomain_matching=False, template_folder='templates', instance_path=None, instance_relative_config=False, root_path=None)

- The flask object implements a WSGI application and acts as the central object. It is passed the name of the module or package of the application. Once it is created it will act as a central registry for the view functions, the URL rules, template configuration and much more.

### About the First Parameter - `import_name`

- The idea of the first parameter is to give Flask an idea of what belongs to your application. This name is used to find resources on the filesystem, can be used by extensions to improve debugging information and a lot more.

- So it’s important what you provide there. If you are using a single module, **name** is always the correct value. If you however are using a package, it’s usually recommended to hardcode the name of your package there.

- For example if your application is defined in yourapplication/app.py you should create it with one of the two versions below:

```
app = Flask('yourapplication')
app = Flask(__name__.split('.')[0])
```

### `route(rule, **options)`

- Decorate a view function to register it with the given URL rule and options
- The endpoint decorator `@app.route("/")` registers the route's endpoint with Flask.
- Parameters:
  - `rule` (str) – The URL rule string.

```
from flask import Flask

app = Flask(__name__)

@app.route("/")
def home():
    return "Hello"

```

### `get(rule, **option)`

- Shortcut for route() with methods=["GET"].

```
@app.get("/store")
def get_stores():
    return {"stores": stores}
```

### `post(rule, **options)`

- Shortcut for route() with methods=["POST"].

##

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

# JSON

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
