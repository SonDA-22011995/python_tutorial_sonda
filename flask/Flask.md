- [Flask Terminology](#flask-terminology)
  - [`class flask.Flask`](#class-flaskflask)
    - [About the First Parameter - `import_name`](#about-the-first-parameter---import_name)
    - [`route(rule, **options)`](#routerule-options)
    - [`get(rule, **option)`](#getrule-option)
    - [`post(rule, **options)`](#postrule-options)
    - [`delete(rule, **options)`](#deleterule-options)
  - [`class flask.Request`](#class-flaskrequest)
    - [`get_json`](#get_json)
  - [URL variables | Route parameters](#url-variables--route-parameters)
  - [Builtin Configuration Values](#builtin-configuration-values)
    - [`PROPAGATE_EXCEPTIONS`](#propagate_exceptions)
- [Flask REST API](#flask-rest-api)
  - [First REST API](#first-rest-api)
  - [Create store in REST API](#create-store-in-rest-api)
  - [Create items in our REST API](#create-items-in-our-rest-api)
- [Flask CLI](#flask-cli)
  - [Environment Variables From dotenv](#environment-variables-from-dotenv)
    - [FLASK_APP](#flask_app)
    - [FLASK_DEBUG](#flask_debug)
    - [FLASK_RUN_PORT](#flask_run_port)
    - [FLASK_RUN_HOST](#flask_run_host)
  - [flask run](#flask-run)
- [Flask-Smorest](#flask-smorest)
  - [Why use Flask-Smorest](#why-use-flask-smorest)
  - [`flask_smorest.abort`](#flask_smorestabort)
    - [How to use](#how-to-use)
    - [Why you should use `flask_smorest.abort` in Flask](#why-you-should-use-flask_smorestabort-in-flask)
  - [How to use Flask-Smorest `MethodViews` and `Blueprints`](#how-to-use-flask-smorest-methodviews-and-blueprints)
    - [`Blueprints`](#blueprints)
    - [MethodViews](#methodviews)
    - [Import blueprints and Flask-Smorest configuration](#import-blueprints-and-flask-smorest-configuration)
  - [`marshmallow`](#marshmallow)
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

### `delete(rule, **options)`

Shortcut for route() with methods=["DELETE"].

## `class flask.Request`

- The request object used by default in Flask. Remembers the matched endpoint and view arguments.

### `get_json`

- get_json(force=False, silent=False, cache=True)
- Parse data as JSON.
- If the mimetype does not indicate JSON (`application/json`, see `is_json`), or parsing fails, `on_json_loading_failed()` is called and its return value is used as the return value. By default this raises a 415 Unsupported Media Type resp.

## URL variables | Route parameters

- How to Use: define a route parameter in the URL rule within the `@app.route()` decorator using angle brackets `<variable_name>`.
- The name you use in the URL must match the name of the argument in the corresponding Python function. Your function then receives the `<variable_name>` as a keyword argument

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

## Builtin Configuration Values

- The following configuration values are used internally by Flask:

### `PROPAGATE_EXCEPTIONS`

- Exceptions are re-raised rather than being handled by the app’s error handlers. If not set, this is implicitly `true` if `TESTING` or `DEBUG` is enabled.
- Default: `None`

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

## Environment Variables From dotenv

- If `python-dotenv` is installed, running the flask command will set environment variables defined in the files `.env` and `.flaskenv`. You can also specify an extra file to load with the `--env-file` option. Dotenv files can be used to avoid having to set `--app` or `FLASK_APP` manually, and to set configuration using environment variables similar to how some deployment services work.
- The files are only loaded by the flask command or calling `run()`. If you would like to load these files when running in production, you should call `load_dotenv()` manually.

### FLASK_APP

- option is used to specify how to load the application.
- `FLASK_APP = src/hello`: Sets the current working directory to src then imports hello.

- `FLASK_APP = hello.web`: Imports the path hello.web.

- `FLASK_APP = hello:app2`: Uses the app2 Flask instance in hello.

- `FLASK_APP = 'hello:create_app("dev")'`: The create_app factory in hello is called with the string `'dev'` as the argument

### FLASK_DEBUG

- Debug mode is enabled.
- Default: `Flase`

### FLASK_RUN_PORT

- To set the port for the run command

```
FLASK_RUN_PORT=9999
```

### FLASK_RUN_HOST

- To set the host for the run command
- You cannot just choose any random IP address; it must match the IP address assigned to your machine by the router.
  - To check this: Open the Command Prompt (cmd) and type the command ipconfig.
  - Look for the line: IPv4 Address. If the number displayed there is different from `192.168.3.2`, you must use that specific number in your `.flaskenv` file.

```
FLASK_RUN_HOST=192.168.3.2 # wrong
FLASK_RUN_HOST=192.168.2.67 # correct
```

- Recommendation: This command instructs Flask to listen on all available network interfaces of the machine (including Wi-Fi, LAN, and localhost)

```
FLASK_RUN_HOST=0.0.0.0
```

- If you do not specify a host address, the default IP address is `localhost` (`127.0.0.1`).
- The Loopback IP Address
  - `127.0.0.0` to `127.255.255.255` is reserved for loopback, i.e., a host’s own address,
    also known as the localhost addres
  - `127.0.0.1` is typically configured as the default loopback address on operating systems.

## flask run

- Run web application
- Parameter

  - `host` (str | None) – the hostname to listen on. Set this to `'0.0.0.0'` to have the server available externally as well. Defaults to `'127.0.0.1'` or the host in the SERVER_NAME config variable if present.

  - `port` (int | None) – the port of the webserver. Defaults to `5000` or the port defined in the SERVER_NAME config variable if present.

  - `debug` (bool | None) – if given, enable or disable debug mode. See `debug`.

  - `load_dotenv` (bool) – Load the nearest .env and .flaskenv files to set environment variables. Will also change the working directory to the directory containing the first file found.

  - `options` (Any) – the `options` to be forwarded to the underlying Werkzeug server. See werkzeug.serving.run_simple() for more information.

- Example: `flask run --host=0.0.0.0 --port=5000 --debug`

# Flask-Smorest

## Why use Flask-Smorest

- I was looking to compare the three libraries in a few key areas:

  - Ease of use and getting started. Many REST APIs are essentially microservices, so being able to whip one up quickly and without having to go through a steep learning curve is definitely interesting.
  - Maintainability and expandability. Although many start as microservices, sometimes we have to maintain projects for a long time. And sometimes, they grow past what we originally envisioned.
  - Activity in the library itself. Even if a library is suitable now, if it is not actively maintained and improved, it may not be suitable in the future. We'd like to teach something that you will use for years to come.
  - Documentation and usage of best practice. The library should help you write better code by having strong documentation and guiding you into following best practice. If possible, it should use existing, actively maintained libraries as dependencies instead of implementing their own versions of them.
  - Developer experience in production projects. The main point here was: how easy is it to produce API documentation with the library of choice. Hundreds of students have asked me how to integrate Swagger in their APIs, so it would be great if the library we teach gave it to you out of the box.

- Flask-Smorest is the most well-rounded. It ticks all the boxes above

## `flask_smorest.abort`

### How to use

```
from flask_smorest import abort

@app.get("/store/<string:store_id>")
def get_store(store_id):
    try:
        # Here you might also want to add the items in this store
        # We'll do that later on in the course
        return stores[store_id]
    except KeyError:
        abort(404, message="Store not found.")
```

### Why you should use `flask_smorest.abort` in Flask

- Errors are control flow, not normal data
- `abort()` immediately stops execution

```
def service():
    if invalid:
        abort(400)

def view():
    service()
    save_to_db()  # ❌ will not be executed

# With return, you must propagate the error through every layer.
# With abort(), you raise the error once and execution stops immediately.
```

- Clear separation of concerns
- Consistent and centralized error responses
- Correct HTTP semantics
- Better scalability and maintainability

## How to use Flask-Smorest `MethodViews` and `Blueprints`

### `Blueprints`

- The Blueprint arguments are the same as the Flask Blueprint1, with an added optional description keyword argument:
- **stores** is the name of the blueprint. This will be shown in the documentation and is prepended to the endpoint names when you use url_for (we won't use it).
  `__name__` is the **import name**.
- The description will be shown in the documentation UI.

```
# resources/store.py
import uuid
from flask import request
from flask.views import MethodView
from flask_smorest import Blueprint, abort
from db import stores


blp = Blueprint("stores", __name__, description="Operations on stores")

```

### MethodViews

- The endpoint is associated to the MethodView class. Here, the class is called Store and the endpoint is `/store/<string:store_id>`.
- There are two methods inside the Store class: get and delete. These are going to map directly to `GET` `/store/<string:store_id>` and `DELETE` `/store/<string:store_id>`.

```
@blp.route("/store/<string:store_id>")
class Store(MethodView):
    def get(self, store_id):
        pass

    def delete(self, store_id):
        pass
```

### Import blueprints and Flask-Smorest configuration

```
from flask import Flask
from flask_smorest import Api

from resources.item import blp as ItemBlueprint
from resources.store import blp as StoreBlueprint


app = Flask(__name__)

app.config["PROPAGATE_EXCEPTIONS"] = True
app.config["API_TITLE"] = "Stores REST API"
app.config["API_VERSION"] = "v1"
app.config["OPENAPI_VERSION"] = "3.0.3"
app.config["OPENAPI_URL_PREFIX"] = "/"
app.config["OPENAPI_SWAGGER_UI_PATH"] = "/swagger-ui"
app.config["OPENAPI_SWAGGER_UI_URL"] = "https://cdn.jsdelivr.net/npm/swagger-ui-dist/"

api = Api(app)

api.register_blueprint(ItemBlueprint)
api.register_blueprint(StoreBlueprint)

```

## `marshmallow`

- Marshmallow is a Python library used to validate, serialize, and deserialize data.

- It allows developers to:

  - Validate incoming data (e.g. API request payloads)
  -
  - Convert raw input data (JSON, dict) into Python objects (deserialization)
  -
  - Convert Python objects into JSON-ready data (serialization)
  -
  - Enforce data structure and types using schemas
  -
  - Produce consistent and meaningful validation errors

- Marshmallow helps keep APIs safe, predictable, and maintainable by ensuring that all input and output data follows well-defined rules.

```
from marshmallow import Schema, fields, validates_schema, ValidationError


class ItemSchema(Schema):
    id = fields.Str(dump_only=True)
    name = fields.Str(required=True)
    price = fields.Float(required=True)
    store_id = fields.Str(required=True)

class ItemUpdateSchema(Schema):
    name = fields.Str()
    price = fields.Float()

    @validates_schema
    def validate_at_least_one(self, data, **kwargs):
        if not data:
            raise ValidationError("At least one field is required")

class StoreSchema(Schema):
    id = fields.Str(dump_only=True)
    name = fields.Str(required=True)
```

```
from schemas import ItemSchema

@blp.arguments(ItemSchema)
def post(self, item_data):
    for item in items.values():
        if (
            item_data["name"] == item["name"]
            and item_data["store_id"] == item["store_id"]
        ):
            abort(400, message=f"Item already exists.")

    item_id = uuid.uuid4().hex
    item = {**item_data, "id": item_id}
    items[item_id] = item

    return item

```

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
