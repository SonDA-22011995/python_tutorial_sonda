- [Flask Terminology](#flask-terminology)
  - [`class flask.Flask`](#class-flaskflask)
    - [About the First Parameter - `import_name`](#about-the-first-parameter---import_name)
    - [`route(rule, **options)`](#routerule-options)
    - [`get(rule, **option)`](#getrule-option)
    - [`post(rule, **options)`](#postrule-options)
  - [`class flask.Request`](#class-flaskrequest)
    - [`get_json`](#get_json)
  - [URL variables | Route parameters](#url-variables--route-parameters)
- [Flask REST API](#flask-rest-api)
  - [First REST API](#first-rest-api)
  - [Create store in REST API](#create-store-in-rest-api)
  - [Create items in our REST API](#create-items-in-our-rest-api)
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

## `class flask.Request`

- The request object used by default in Flask. Remembers the matched endpoint and view arguments.

### `get_json`

- get_json(force=False, silent=False, cache=True)
- Parse data as JSON.
- If the mimetype does not indicate JSON (`application/json`, see `is_json`), or parsing fails, `on_json_loading_failed()` is called and its return value is used as the return value. By default this raises a 415 Unsupported Media Type resp.

## URL variables | Route parameters

- How to Use: ou define a route parameter in the URL rule within the `@app.route()` decorator using angle brackets `<variable_name>`. The name you use in the URL must match the name of the argument in the corresponding Python function.

- Basic example

```
from flask import Flask
app = Flask(__name__)

@app.route('/user/<username>')
def show_user_profile(username):
    # show the user profile for that user
    return f'User: {username}'

if __name__ == '__main__':
    app.run(debug=True)
```

- URL Converters: By default, the parameter type is a string (without slashes). Flask supports various type converters to filter the parameters in the URL

| **Type**   | **Description**                                |
| ---------- | ---------------------------------------------- |
| **string** | _(Default)_ Accepts any text without slashes.  |
| **int**    | Accepts positive integers.                     |
| **float**  | Accepts positive floating-point values.        |
| **path**   | Similar to `string`, but also accepts slashes. |
| **uuid**   | Accepts UUID strings.                          |

- Example with an Integer Converter

```
@app.route('/post/<int:post_id>')
def show_post(post_id):
    # show the post with the given id, which is an integer
    return f'Post ID: {post_id}'

```

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

## Create store in REST API

- Create store

```
from flask import Flask, request

stores = [
    {
        "name": "My Store",
        "is_active": True,
        "items": [
            {
                "name": "my item",
                "price": 15.99
            }
        ]
    }
]

app = Flask(__name__)

@app.post("/store")
def create_store():
    request_data = request.get_json()
    new_store = {"name": request_data["name"], "items": []}
    stores.append(new_store)
    return new_store, 201
```

## Create items in our REST API

```
@app.post("/store/<string:name>/item")
def create_item(name):
    request_data = request.get_json()
    for store in stores:
        if store["name"] == name:
            new_item = {"name": request_data["name"], "price": request_data["price"]}
            store["items"].append(new_item)
            return new_item
    return {"message": "Store not found"}, 404
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
