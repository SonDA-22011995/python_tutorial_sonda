- [Basic Application Structure](#basic-application-structure)
  - [Initialization](#initialization)
  - [Routes and View Functions](#routes-and-view-functions)
    - [URL dynamic](#url-dynamic)
  - [Command-Line Options](#command-line-options)
  - [The Request-Response Cycle](#the-request-response-cycle)
    - [Application and Request Contexts](#application-and-request-contexts)
    - [Request Dispatching](#request-dispatching)
    - [The Request Object](#the-request-object)
    - [Request Hooks](#request-hooks)
    - [Responses](#responses)
      - [Redirect](#redirect)
      - [Abort](#abort)
    - [Handling basic configurations](#handling-basic-configurations)
    - [Configuring using class-based settings](#configuring-using-class-based-settings)

# Basic Application Structure

## Initialization

- The only required argument to the Flask class constructor is the name of the main module or package of the application. For most applications, Python’s `__name__` variable is the correct value for this argument

```
# learn.py

from flask import Flask
app = Flask(__name__)
```

- Run flask app by cli command: `flask --app learn --debug run`

## Routes and View Functions

- Clients such as web browsers send requests to the web server, which in turn sends them to the Flask application instance. The Flask application instance needs to know what code it needs to run for each URL requested, so it keeps a mapping of URLs to Python functions. The association between a URL and the function that handles it is called a route.
- The most convenient way to define a route in a Flask application is through the `app.route` decorator exposed by the application instance

```
@app.route('/')
def index():
    return '<h1>Hello World!</h1>'
```

- Flask also offers a more traditional way to set up the application routes with the `app.add_url_rule()`
  method
- `app.add_url_rule()` Parameters:
  - rule (str) – The URL rule string.
  - endpoint (str | None) – The endpoint name to associate with the rule and view function. Used when routing and building URLs. Defaults to `view_func.__name__`.
  - view_func (ft.RouteCallable | None) – The view function to associate with the endpoint name.
  - provide_automatic_options (bool | None) – Add the OPTIONS method and respond to OPTIONS requests automatically.
  - options (t.Any) – Extra options passed to the Rule object.

- The alternative for `app.route` decorator

```
def index():
    return '<h1>Hello World!</h1>'

app.add_url_rule('/', 'index', index)
```

- Full example `app.add_url_rule()`

```
from flask import Flask, request, jsonify

app = Flask(__name__)

def user_detail(user_id):
    return jsonify({
        "user_id": user_id,
        "method": request.method
    })

app.add_url_rule(
    rule="/users/<int:user_id>",          # rule
    endpoint="user_detail_endpoint",       # endpoint
    view_func=user_detail,                 # view_func
    provide_automatic_options=True,        # provide_automatic_options
    methods=["GET", "POST"],               # options
    strict_slashes=False                   # options
)

if __name__ == "__main__":
    app.run(debug=True)
```

### URL dynamic

- You can add variable sections to a URL by marking sections with `<variable_name>`. Your function then receives the `<variable_name>` as a keyword argument. Optionally, you can use a converter to specify the type of the argument like `<converter:variable_name>`.

| Converter | Description                                          |
| --------- | ---------------------------------------------------- |
| `string`  | (Default) Accepts any text **without a slash (`/`)** |
| `int`     | Accepts **positive integers**                        |
| `float`   | Accepts **positive floating-point values**           |
| `path`    | Like `string` but also accepts **slashes (`/`)**     |
| `uuid`    | Accepts **UUID strings**                             |

```
from flask import Flask
app = Flask(__name__)

@app.route('/')
def index():
    return '<h1>Hello World!</h1>'

@app.route('/user/<name>')
def user(name):
    return '<h1>Hello, {}!</h1>'.format(name)
```

## Command-Line Options

```
flask --help
flask run --help

```

## The Request-Response Cycle

### Application and Request Contexts

- Flask uses contexts to temporarily make certain objects globally accessible

```
from flask import request

@app.route('/')
def index():
    user_agent = request.headers.get('User-Agent')
    return '<p>Your browser is {}</p>'.format(user_agent)
```

- There are two contexts in Flask: the `application context` and the `request context`

| Variable name | Context             | Description                                                                                                                              |
| ------------- | ------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| current_app   | Application context | The application instance for the active application.                                                                                     |
| g             | Application context | An object that the application can use for temporary storage during the handling of a request. This variable is reset with each request. |
| request       | Request context     | The request object, which encapsulates the contents of an HTTP request sent by the client.                                               |
| session       | Request context     | The user session, a dictionary that the application uses to store data that is preserved between requests for a specific user.           |

### Request Dispatching

- When the application receives a request from a client, it needs to find out what view function to invoke to service it. For this task, Flask looks up the URL given in the request in the application’s URL map, which contains a mapping of URLs to the view
  functions that handle them.
- Flask builds this map using the data provided in the `app.route` decorator, or the equivalent non-decorator version,
  `app.add_url_rule()`
- Flask attaches methods to each route so that different request methods sent to the same URL can be handled by different view functions
- Example to see what the URL map in a Flask application looks like

```
# in terminal
# server.py is python file declare app = Flask(__name__)

(venv) $ python
from server import app

app.url_map

>>>Map([<Rule '/' (HEAD, OPTIONS, GET) -> index>,
>>><Rule '/static/<filename>' (HEAD, OPTIONS, GET) -> static>,
>>><Rule '/user/<name>' (HEAD, OPTIONS, GET) -> user>])

```

### The Request Object

```
from flask import request
```

| Attribute / Method | Description                                                                           |
| ------------------ | ------------------------------------------------------------------------------------- |
| `form`             | A dictionary with all the form fields submitted with the request.                     |
| `args`             | A dictionary with all the arguments passed in the query string of the URL.            |
| `values`           | A dictionary that combines the values in `form` and `args`.                           |
| `cookies`          | A dictionary with all the cookies included in the request.                            |
| `headers`          | A dictionary with all the HTTP headers included in the request.                       |
| `files`            | A dictionary with all the file uploads included with the request.                     |
| `get_data()`       | Returns the buffered data from the request body.                                      |
| `get_json()`       | Returns a Python dictionary with the parsed JSON included in the body of the request. |
| `blueprint`        | The name of the Flask blueprint that is handling the request.                         |
| `endpoint`         | The name of the Flask endpoint that is handling the request.                          |
| `method`           | The HTTP request method, such as `GET` or `POST`.                                     |
| `scheme`           | The URL scheme (`http` or `https`).                                                   |
| `is_secure()`      | Returns `True` if the request came through a secure (HTTPS) connection.               |
| `host`             | The host defined in the request, including the port number if given by the client.    |
| `path`             | The path portion of the URL.                                                          |
| `query_string`     | The query string portion of the URL, as a raw binary value.                           |
| `full_path`        | The path and query string portions of the URL.                                        |
| `url`              | The complete URL requested by the client.                                             |
| `base_url`         | Same as `url`, but without the query string component.                                |
| `remote_addr`      | The IP address of the client.                                                         |
| `environ`          | The raw WSGI environment dictionary for the request.                                  |

### Request Hooks

- Sometimes it is useful to execute code before or after each request is processed
- For example, at the start of each request it may be necessary to create a database connection or authenticate the user making the request
- Instead of duplicating the code that performs these actions in every view function, Flask gives you the option to register
  common functions to be invoked before or after a request is dispatched

- Request hooks are implemented as **decorators**. These are the four hooks supported by Flask:
  - `before_request`: Registers a function to run before each request.
  - `before_first_request`: Registers a function to run only before the first request is handled. This can be aconvenient way to add server initialization tasks.
  - `after_request`: Registers a function to run after each request, but only if no unhandled exceptions occurred.
  - `teardown_request`: Registers a function to run after each request, even if unhandled exceptions occurred.

### Responses

- In most cases the response is a simple string that is sent back to the client as an HTML page
- Flask by default sets to `200`, the code that indicates that the request was carried out successfully
- When a view function needs to respond with a different status code, it can add the numeric code as a second return value after the response tex

```
@app.route('/')
def index():
    return '<h1>Bad Request</h1>', 400
```

- Flask view functions have the option of returning a **response object**
- The `make_response()` function takes one, two, or three arguments, the same values that can be returned from a view function, and returns an equivalent response object

```
from flask import make_response

@app.route('/')
def index():
    response = make_response('<h1>This document carries a cookie!</h1>')
    response.set_cookie('answer', '42')
    return response

```

| Attribute / Method | Description                                                                       |
| ------------------ | --------------------------------------------------------------------------------- |
| `status_code`      | The numeric HTTP status code                                                      |
| `headers`          | A dictionary-like object with all the headers that will be sent with the response |
| `set_cookie()`     | Adds a cookie to the response                                                     |
| `delete_cookie()`  | Removes a cookie                                                                  |
| `content_length`   | The length of the response body                                                   |
| `content_type`     | The media type of the response body                                               |
| `set_data()`       | Sets the response body as a string or bytes value                                 |
| `get_data()`       | Gets the response body                                                            |

#### Redirect

- There is a special type of response called a redirect. This response does not include a page document; it just gives the browser a new URL to navigate to
- A redirect is typically indicated with a 302 response status code and the URL to go to given in a Location header
- Flask provides a `redirect()` helper function that creates this type of response

```
from flask import redirect
@app.route('/')
def index():
    return redirect('http://www.example.com')
```

#### Abort

- Another special response is issued with the `abort()` function, which is used for error handling
- `abort()` does not return control back to the function because it raises an
  exception

```
from flask import abort


@app.route('/user/<id>')
def get_user(id):
    user = load_user(id)
    if not user:
        abort(404)
    return '<h1>Hello, {}</h1>'.format(user.name)
```

### Handling basic configurations

- The `config` is actually a subclass of a dictionary and can be modified just like any dictionary:

```
app = Flask(__name__)
app.config['DEBUG'] = True
```

- To update multiple keys at once you can use the `dict.update()` method:

```
app.config.update(
    TESTING=True,
    SECRET_KEY='192b9bdd22ab9ed4d12e236c78afcb9a393ec15f71bbf5dc987d54727823bcbf'
)
```

- Alternatively, we can pass debug as a named argument to app.run, as follows:

```
app.run(debug=True)
```

- In new versions of Flask, the debug mode can also be set on an environment variable

```
# Windows (Command Prompt – CMD)

set FLASK_APP=app.py
set FLASK_ENV=development
set FLASK_DEBUG=1
flask run
```

```
# Windows (PowerShell)

$env:FLASK_APP="app.py"
$env:FLASK_ENV="development"
$env:FLASK_DEBUG="1"
flask run
```

```
# macOS / Linux (bash, zsh)

export FLASK_APP=app.py
export FLASK_ENV=development
export FLASK_DEBUG=1
flask run
```

- From a Python configuration file (`*.cfg`), where the configuration can be fetched using the following statement:

```
# myconfig.cfg

DEBUG = True
SECRET_KEY = "super-secret-key"
DATABASE_URI = "postgresql://user:pass@localhost:5432/mydb"
TIMEOUT = 30
```

```
# fetch config

app.config.from_pyfile("myconfig.cfg")
```

- Configuring from Python Files, where the configuration can be fetched using the following statement:

```
app.config.from_object('myapplication.default_settings')
``

- New in Flask version 2.0 is a capability to load from generic configuration file formats such as JSON or TOML:

```

import tomllib
import json

app.config.from_file('config.json', load=json.load)

app.config.from_file('config.toml', load=toml.load)

```



### Setting up with Docker
```

### Configuring using class-based settings

- An effective way of laying out configurations for different deployment modes, such as production, testing, staging, and so on, can be cleanly done using the inheritance pattern of classes

```
# configuration.py file

# Base config class
class BaseConfig(object):
    SECRET_KEY = 'A random secret key'
    DEBUG = True
    TESTING = False
    NEW_CONFIG_VARIABLE = 'my value'

# Production specific config'
class ProductionConfig(BaseConfig):
    DEBUG = False
    SECRET_KEY = open('/path/to/secret/file').read()

# Staging specific config'
class StagingConfig(BaseConfig):
    DEBUG = True

# Development environment specific config
class DevelopmentConfig(BaseConfig):
    DEBUG = True
    TESTING = True
    SECRET_KEY = 'Another random secret key
```

- Important information: In a production configuration, the secret key is generally stored in a separate file because, for security reasons, it should not be a part of your version control system. This should be kept in the local filesystem on the machine itself, whether it is your machine or a server

- Now, we can use any of the preceding classes while loading the application’s configuration via `from_object()`. Let’s say that we save the preceding class-based configuration in a file named configuration.py, as follows:

```
app.config.from_object('configuration.DevelopmentConfig')

# or
# from configuration import DevelopmentConfig
# app.config.from_object(DevelopmentConfig)
```
