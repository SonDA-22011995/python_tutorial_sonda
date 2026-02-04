- [Basic Application Structure](#basic-application-structure)
  - [Initialization](#initialization)
  - [Generate a different secret key](#generate-a-different-secret-key)
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
  - [Instance Folders](#instance-folders)
  - [Setting up with Docker](#setting-up-with-docker)
  - [Configuring using class-based settings](#configuring-using-class-based-settings)
  - [Composition of views and models](#composition-of-views-and-models)
- [Templates](#templates)
  - [The Jinja2 Template Engine](#the-jinja2-template-engine)
    - [Rendering Templates](#rendering-templates)
    - [Comments](#comments)
    - [Variables](#variables)
    - [Working with Manual Escaping](#working-with-manual-escaping)
    - [Filters](#filters)
    - [`for` Statements](#for-statements)
    - [`if` statement](#if-statement)
    - [`with` Statement](#with-statement)
    - [`macro`](#macro)
    - [`include`](#include)
    - [Template inheritance](#template-inheritance)
    - [Context Processors](#context-processors)
    - [Registering Filters](#registering-filters)
  - [Links](#links)
  - [Handling Application Errors](#handling-application-errors)
    - [Registering](#registering)
    - [Generic Exception Handlers](#generic-exception-handlers)
    - [Custom Error Pages](#custom-error-pages)
  - [Organizing static files](#organizing-static-files)
- [Web Forms](#web-forms)
  - [Install Flask-WTF](#install-flask-wtf)
  - [Configuration](#configuration)
    - [Protecting applications from CSRF](#protecting-applications-from-csrf)
  - [Form Classes](#form-classes)
    - [The list of standard field Basic](#the-list-of-standard-field-basic)
    - [The list of WTForms built-in validators](#the-list-of-wtforms-built-in-validators)
  - [Form Handling in View Functions](#form-handling-in-view-functions)
  - [HTML Rendering of Forms](#html-rendering-of-forms)
  - [Display any error messages](#display-any-error-messages)
  - [Redirects and User Sessions](#redirects-and-user-sessions)
  - [Message Flashing](#message-flashing)
  - [Custom validations](#custom-validations)
  - [Custom widgets](#custom-widgets)
- [Databases](#databases)
- [Other](#other)
  - [How to decode user session](#how-to-decode-user-session)

# Basic Application Structure

## Initialization

- The only required argument to the Flask class constructor is the name of the main module or package of the application. For most applications, Python’s `__name__` variable is the correct value for this argument

```
# learn.py

from flask import Flask
app = Flask(__name__)
```

- Run flask app by cli command: `flask --app learn --debug run`
- `--app hello`: The given name is imported, automatically detecting an app (app or application) or factory (create_app or make_app).
- `--app` has three parts: an optional path that sets the current working directory, a Python file or dotted import path, and an optional variable name of the instance or factory. If the name is a factory, it can optionally be followed by arguments in parentheses. The following values demonstrate these parts:
- `--app src/hello`: Sets the current working directory to src then imports hello.
- `--app hello.web`: Imports the path hello.web.
- `--app hello:app2`: Uses the app2 Flask instance in hello.
- `--app 'hello:create_app("dev")'`: The create_app factory in hello is called with the string 'dev' as the argument.

## Generate a different secret key

```
import secrets
str(secrets.SystemRandom().getrandbits(128))
```

```
import os
os.urandom(24).hex()
```

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

## Handling basic configurations

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
```

- New in Flask version 2.0 is a capability to load from generic configuration file formats such as JSON or TOML:

```
import tomllib
import json

app.config.from_file('config.json', load=json.load)

app.config.from_file('config.toml', load=toml.load)
```

## Instance Folders

- The instance folder is designed to not be under version control and be deployment specific. It’s the perfect place to drop things that either change at runtime or configuration files
- By default, the instance folder is picked up from the application automatically if we have a folder named instance in our application at the application level, as follows

```
# Uninstalled module
my_app/
    app.py
    instance/
        config.cfg
```

```
# Uninstalled package:
/myapp
    /__init__.py
/instance
```

- For explicit configuration use the instance_path parameter

```
app = Flask(__name__, instance_path='/absolute/path/to/instance/folder')
```

- To load the configuration file from the instance folder, we can use the instance_relative_config parameter on the application object, as follow

```
app = Flask(
    __name__, instance_path='path/to/instance/folder',
    instance_relative_config=True
)
app.config.from_pyfile('config.cfg', silent=True)
```

- In the preceding code, first, the instance folder is loaded from the given path; then, the configuration file is loaded from the config.cfg file in the given instance folder. Here, silent=True is optional and is used to suppress the error if config.cfg is not found in the instance folder. If silent=True is not given and the file is not found, then the application will fail, giving the following error

```
IOError: [Errno 2] Unable to load configuration file (No such file or
directory): '/absolute/path/to/config/file'
```

## Setting up with Docker

## Configuring using class-based settings

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

- In Flask CLI

```
set FLASK_CONFIG=configuration.DevelopmentConfig
flask run
```

## Composition of views and models

- As our application becomes bigger, we might want to structure it in a modular manner
- File structure. After that, create a new file called `run.py` in the topmost folder. As its name implies, this file will be used to run the application

```
flask_app/
    run.py
    my_app/
        __init__.py
        hello/
            __init__.py
            models.py
            views.py
```

- The `flask_app/run.py`

```
from my_app import app

app.run(debug=True)
```

- The `flask_app/my_app/__init__.py`

```
from flask import Flask
import my_app.hello.views

app = Flask(__name__)
```

- The `flask_app/my_app/hello/__init__.py`

```
# No content.
# We need this file just to make this folder a python module.
```

- The `flask_app/my_app/hello/models.py`

```
MESSAGES = {
    'default': 'Hello to the World of Flask!',
}
```

- The `flask_app/my_app/hello/views.py`

```
from my_app import app
from my_app.hello.models import MESSAGES

@app.route('/')
@app.route('/hello')
def hello_world():
    return MESSAGES['default']

@app.route('/show/<key>')
def get_message(key):
    return MESSAGES.get(key) or "%s not found!" % key

@app.route('/add/<key>/<message>')
def add_or_update_message(key, message):
    MESSAGES[key] = message
    return "%s Added/Updated" % key
```

- We can run this app using just `run.py`, as follows:

```
python run.py
```

- To run the application in the development environment, modify the `run.py` file with the following:

```
from my_app import app
app.env="development"
app.run(debug=True)
```

# Templates

- Flask will look for templates in the templates folder. So if your application is a module, this folder is next to that module, if it’s a package it’s actually inside your package:

- Case 1: a module:

```
/application.py
/templates
    /hello.html
```

Case 2: a package:

```
/application
    /__init__.py
    /templates
        /hello.html
```

## The Jinja2 Template Engine

### Rendering Templates

- To render a template you can use the `render_template()` method. All you have to do is provide the name of the template and the variables you want to pass to the template engine as keyword arguments

```
from flask import Flask, render_template


@app.route('/')
def index():
    return render_template('index.html')

@app.route('/user/<name>')
def user(name):
    return render_template('user.html', name=name)
```

- `name` this value is passed to the context of the template to be rendered – that is, user.html – and the resulting template is rendered

### Comments

- Syntax: `{# ... #}`

```
{# note: commented-out template because we no longer use this
    {% for user in users %}
        ...
    {% endfor %}
#}
```

### Variables

- Syntax `{{ <variable_name> }}`
- Jinja2 recognizes variables of any type, even complex types such as lists, dictionaries, and objects. The following are some more examples of variables used in templates

```
<p>A value from a dictionary: {{ mydict['key'] }}.</p>
<p>A value from a list: {{ mylist[3] }}.</p>
<p>A value from a list, with a variable index: {{ mylist[myintvar] }}.</p>
<p>A value from an object's method: {{ myobj.somemethod() }}.</p>
```

### Working with Manual Escaping

- Escaping works by piping the variable through the `|e` filter

```
{{ user.username|e }}
```

### Filters

- Syntax `{{ <variable_name>|<filter_name>}}`

| Filter name | Description                                                                      |
| ----------- | -------------------------------------------------------------------------------- |
| safe        | Renders the value without applying escaping                                      |
| capitalize  | Converts the first character of the value to uppercase and the rest to lowercase |
| lower       | Converts the value to lowercase characters                                       |
| upper       | Converts the value to uppercase characters                                       |
| title       | Capitalizes each word in the value                                               |
| trim        | Removes leading and trailing whitespace from the value                           |
| striptags   | Removes any HTML tags from the value before rendering                            |

### `for` Statements

- Syntax:

```
{% for item in seq: %}
    ...
{% endfor %}
```

| Variable           | Description                                                                |
| ------------------ | -------------------------------------------------------------------------- |
| `loop.index`       | The current iteration of the loop (**1-indexed**)                          |
| `loop.index0`      | The current iteration of the loop (**0-indexed**)                          |
| `loop.revindex`    | The number of iterations from the end of the loop (**1-indexed**)          |
| `loop.revindex0`   | The number of iterations from the end of the loop (**0-indexed**)          |
| `loop.first`       | `True` if this is the first iteration                                      |
| `loop.last`        | `True` if this is the last iteration                                       |
| `loop.length`      | The total number of items in the sequence                                  |
| `loop.cycle()`     | A helper function to cycle through values (e.g. CSS classes, colors, etc.) |
| `loop.depth`       | The current depth of a recursive loop (**starts at 1**)                    |
| `loop.depth0`      | The current depth of a recursive loop (**starts at 0**)                    |
| `loop.previtem`    | The item from the previous iteration (undefined in the first iteration)    |
| `loop.nextitem`    | The item from the next iteration (undefined in the last iteration)         |
| `loop.changed(*v)` | `True` if the passed value differs from the previous call                  |

- Inside of a for-loop block, you can access some special variables:

### `if` statement

- Syntax

```
{% if users %}
<ul>
{% for user in users %}
    <li>{{ user.username|e }}</li>
{% endfor %}
</ul>
{% endif %}
```

```
{% if kenny.sick %}
    Kenny is sick.
{% elif kenny.dead %}
    You killed Kenny!  You bastard!!!
{% else %}
    Kenny looks okay --- so far
{% endif %}
```

### `with` Statement

- The `with` statement makes it possible to create a new inner scope. Variables set within this scope are not visible outside of the scope.

```
{% with %}
    {% set foo = 42 %}
    {{ foo }}           # foo is 42 here
{% endwith %}
# foo is not visible here any longer
```

### `macro`

- `macros` are similar to functions in Python code

- Declare:

```
{% macro render_comment(comment) %}
    <li>{{ comment }}</li>
{% endmacro %}

- How to use
<ul>
    {% for comment in comments %}
    {{ render_comment(comment) }}
    {% endfor %}
</ul>
```

- To make `macros` more reusable, they can be stored in standalone files that are then `imported` from all the templates that need them

```
{% import 'macros.html' as macros %}

<ul>
    {% for comment in comments %}
    {{ macros.render_comment(comment) }}
    {% endfor %}
</ul>
```

### `include`

- The `include` tag renders another template and outputs the result into the current template.
- The included template has access to context of the current template by default. Use `without context` to use a separate context instead. `with context` is also valid, but is the default behavior

```
{% include 'header.html' %}
Body goes here.
{% include 'footer.html' %}
```

```
{% include "sidebar.html" without context %}
{% include "sidebar.html" ignore missing %}
{% include "sidebar.html" ignore missing with context %}
{% include "sidebar.html" ignore missing without context %}
```

### Template inheritance

- Template inheritance allows you to build a base “skeleton” template that contains all the common elements of your site and defines blocks that child templates can override.

- Base Template: In this example, the `{% block %}` tags define four blocks that child templates can fill in. All the block tag does is tell the template engine that a child template may override those placeholders in the template.

```
<!DOCTYPE html>
<html lang="en">
<head>
    {% block head %}
    <link rel="stylesheet" href="style.css" />
    <title>{% block title %}{% endblock %} - My Webpage</title>
    {% endblock %}
</head>
<body>
    <div id="content">{% block content %}{% endblock %}</div>
    <div id="footer">
        {% block footer %}
        &copy; Copyright 2008 by <a href="http://domain.invalid/">you</a>.
        {% endblock %}
    </div>
</body>
</html>
```

- Child Template:
  - The `{% extends %}` tag is the key here. It tells the template engine that this template “extends” another template
  - The filename of the template depends on the template loader. For example, the **FileSystemLoader** allows you to access other templates by giving the filename. You can access templates in subdirectories with a slash: `{% extends "layout/default.html" %}`

```
{% extends "base.html" %}
{% block title %}Index{% endblock %}
{% block head %}
    {{ super() }}
    <style type="text/css">
        .important { color: #336699; }
    </style>
{% endblock %}
{% block content %}
    <h1>Index</h1>
    <p class="important">
      Welcome to my awesome homepage.
    </p>
{% endblock %}
```

### Context Processors

- To inject new variables automatically into the context of a template, context processors exist in Flask
- Context processors run before the template is rendered and have the ability to inject new values into the template context.
- A context processor is a function that returns a dictionary. The keys and values of this dictionary are then merged with the template context, for all templates in the app
- The context processor below makes the `format_price` function available to all templates:

```
@app.context_processor
def utility_processor():
    def format_price(amount, currency="€"):
        return f"{amount:.2f}{currency}"
    return dict(format_price=format_price)
```

```
{{ format_price(0.33) }}
```

### Registering Filters

- If you want to register your own filters in Jinja you have two ways to do that. You can either put them by hand into the `jinja_env` of the application or use the `template_filter()` decorator.

```
@app.template_filter('reverse')
def reverse_filter(s):
    return s[::-1]
```

```
def reverse_filter(s):
    return s[::-1]
app.jinja_env.filters['reverse'] = reverse_filter
```

- Once registered, you can use the filter in your templates in the same way as Jinja’s builtin filters, for example if you have a Python list in context called mylist

```
{% for x in mylist | reverse %}
{% endfor %}
```

## Links

- Flask provides the `url_for()` helper function, which generates URLs from the information stored in the application’s URL map
- In its simplest usage, this function takes the view function name (funtion name declare in `@app.route` decorator or endpoint name for routes defined with `app.add_url_route()`) as its single argument and returns its URL
- For example, `url_for('user', name='john', page=2, version=1)` would return `/user/john?page=2&version=1`.

```
@app.route('/blogs/<int:id>')
def blogs(id: int):
```

```
<a href="{{ url_for('blogs',id=blog.get('id')) }}">Read</a>
```

- `flask.url_for` Parameters:
  - `endpoint (str)` – The endpoint name associated with the URL to generate. If this starts with a ., the current blueprint name (if any) will be used.
  - `_anchor (str | None)` – If given, append this as #anchor to the URL.
  - `_method (str | None)` – If given, generate the URL associated with this method for the endpoint.
  - `_scheme (str | None)` – If given, the URL will have this scheme if it is external.
  - `_external (bool | None)` – If given, prefer the URL to be internal (False) or require it to be external (True). External URLs include the scheme and domain. When not in an active request, URLs are external by default.
  - `values (Any)` – Values to use for the variable parts of the URL rule. Unknown keys are appended as query string arguments, like ?a=b&c=d.
  - Return type: str

## Handling Application Errors

### Registering

- Register handlers by decorating a function with `errorhandler()`. Or use `register_error_handler()` to register the function later. Remember to set the error code when returning the response.
- `werkzeug.exceptions.HTTPException` subclasses like BadRequest and their HTTP codes are interchangeable when registering handlers. (BadRequest.code == 400)

```
@app.errorhandler(werkzeug.exceptions.BadRequest)
def handle_bad_request(e):
    return 'bad request!', 400

# or, without the decorator
app.register_error_handler(400, handle_bad_request)
```

```
@app.errorhandler(404)
def page_not_found(e):
    return render_template('404.html'), 404

@app.errorhandler(500)
def internal_server_error(e):
    return render_template('500.html'), 500
```

### Generic Exception Handlers

```
from flask import json
from werkzeug.exceptions import HTTPException

@app.errorhandler(HTTPException)
def handle_exception(e):
    """Return JSON instead of HTML for HTTP errors."""
    # start with the correct headers and status code from the error
    response = e.get_response()
    # replace the body with JSON
    response.data = json.dumps({
        "code": e.code,
        "name": e.name,
        "description": e.description,
    })
    response.content_type = "application/json"
    return response

# python exception

@app.errorhandler(Exception)
def handle_exception(e):
    # pass through HTTP errors
    if isinstance(e, HTTPException):
        return e

    # now you're handling non-HTTP exceptions only
    return render_template("500_generic.html", e=e), 500
```

### Custom Error Pages

```
import logging
from flask import abort, render_template, request

# a username needs to be supplied in the query args
# a successful request would be like /profile?username=jack
@app.route("/profile")
def user_profile():
    username = request.arg.get("username")
    # if a username isn't supplied in the request, return a 400 bad request
    if username is None:
        logging.warning(<<error_message>>)
        abort(400, description=<<error_message>>)

    user = get_user(username=username)
    # if a user can't be found by their username, return 404 not found
    if user is None:
        logging.warning(<<error_message>>)
        abort(404,description=<<error_message>>)

    return render_template("profile.html", user=user)
```

```
from flask import render_template

@app.errorhandler(404)
def page_not_found(e):
    # note that we set the 404 status explicitly
    return render_template('404.html', message=e.description), 404
```

- When using Application Factories:

```
from flask import Flask, render_template

def page_not_found(e):
  return render_template('404.html', message=e.description), 404

def create_app(config_filename):
    app = Flask(__name__)
    app.register_error_handler(404, page_not_found)
    return app
```

- An example template might be this:

```
{% extends "layout.html" %}
{% block title %}Page Not Found{% endblock %}
{% block body %}
  <h1>Page Not Found</h1>
  <p>What you were looking for is just not there.</p>
  <p>{{ message }}</p>
  <a href="{{ url_for('index') }}">go somewhere nice</a>
{% endblock %}
```

## Organizing static files

- Flask recommends a specific way of organizing static files in an application, as follows:

```
my_app/
├── app.py
├── config.py
├── __init__.py
├── static/
│   ├── css/
│   ├── js/
│   └── images/
│       └── logo.png
```

- While rendering this in templates (say, the logo.png file), we can refer to the static files using the
  following code `<img src='/static/images/logo.png'>`

- It is always a good practice to use url_for to create URLs for static files rather than explicitly
  defining them, as follows `<img src="{{ url_for('static', filename='logo.png') }}">`

- `static_folder` The folder with static files that is served at. Default to 'static'
- `static_url_path` Relative to the application root_path or an absolute path. Defaults to '/static'.

```
app = Flask(
    _name_,
    static_url_path='/differentstatic',
    static_folder='/path/to/static/folder'
)
```

- Changing static-folder

```
my_app/
├── app.py
└── assets/
    └── logo.png
```

```
app = Flask(
    __name__,
    static_folder="assets"
)
```

```
# url static file
http://localhost:5000/static/logo.png
```

- Changing url path

```
my_app/
├── app.py
└── static/
    └── logo.png
```

```
app = Flask(
    __name__,
    static_url_path="/public"
)
```

```
# url
http://localhost:5000/public/logo.png
```

# Web Forms

## Install Flask-WTF

```
pip install flask-wtf
```

## Configuration

- A CSRF (cross-site request forgery) attack occurs when a malicious website sends requests to the application server on which the user is currently logged in
- Flask-WTF requires a secret key to be configured in the application because this key is part of the mechanism the extension uses to protect all forms against cross-site request forgery (CSRF) attack

```
app = Flask(__name__)
app.config['SECRET_KEY'] = <<your_secret_key>>
```

### Protecting applications from CSRF

- Some configuration bits also need to be done in our application

```
app.config['WTF_CSRF_SECRET_KEY'] = 'random key for form'
```

- With CSRF enabled, we will have to provide an additional field in our forms; this is a hidden field and
  contains the CSRF token. WTForms takes care of the hidden field for us, and we just have to add
  `{{ form.csrf_token }}` to our form:

```
<form method="POST" action="/some-action-like-create-
  product">
    {{ form.csrf_token }}
</form>
```

- For this, we need to include another step in our application’s configuration:

```
from flask_wtf.csrf import CSRFProtect
#
# Add configurations #
CSRFProtect(app)
```

- The preceding configuration will allow us to access the CSRF token using {{ csrf_token() }}
  anywhere in our templates. Now, there are two ways to add a CSRF token to AJAX POST requests.

- One way is to fetch the CSRF token in our script tag and use it in the POST request:

```
<script type="text/javascript">
    var csrfToken = "{{ csrf_token() }}";
</script>
```

- Another way is to render the token in a meta tag and use it whenever required:

```
<meta name="csrf-token" content="{{ csrf_token() }}"/>
```

- The difference between the two approaches is that the first approach may have to be repeated in
  multiple places, depending on the number of script tags in the application

- Now, to add the CSRF token to the AJAX POST request, we have to add the X-CSRFToken attribute
  to it. This attribute’s value can be taken from either of the two approaches stated here. We will take
  the second one for our example:

```
$.ajaxSetup({
    beforeSend: function(xhr, settings) {
        if (!/^(GET|HEAD|OPTIONS|TRACE)$/i
          .test(settings.type)) {
            xhr.setRequestHeader("X-CSRFToken", csrftoken)
        }
    }
})
```

## Form Classes

- There are three main parts of `WTForms—forms`, `fields`, and `validators`
  - `WTForms—forms`is represented in the server by a class that inherits from the class `FlaskForm`
  - `fields`: representations of input fields and perform rudimentary type checking. Fields contain a number of useful properties, such as a **label**, **description**, and **a list of validation errors**, in addition to the data the field contains
  - Every field has a `widget` instance. The widget’s job is rendering an HTML representation of that field. Widget instances can be specified for each field but every field has one by default which makes sense. Some fields are simply conveniences, for example `TextAreaField` is simply a `StringField` with the default widget being a TextArea.
  - `validators`: are functions that are attached to fields that make sure that the data submitted in the form is within our constraints

```
from flask_wtf import FlaskForm as Form
from wtforms import StringField, TextAreaField
from wtforms.validators import DataRequired, Length

class CommentForm(Form):
    name = StringField('Name',validators=[DataRequired(), Length(max=255)])
    text = TextAreaField('Comment', validators=[DataRequired()])
```

- `data`– Take existing data from keys in this dict matching form field attributes. obj takes precedence if it also has a matching attribute. Only used if formdata is not passed.

```
from add_form import AddForm
form = AddForm(data=book)
```

### The list of standard field Basic

| Field Name              | HTML Input          | When to Use / Meaning                                                       |
| ----------------------- | ------------------- | --------------------------------------------------------------------------- |
| **StringField**         | `text`              | Default text input. Use for usernames, titles, short text.                  |
| **TextAreaField**       | `textarea`          | Multi-line text input. Use for descriptions, comments, notes.               |
| **PasswordField**       | `password`          | Password input. Value is not re-rendered. Always hash on backend.           |
| **HiddenField**         | `hidden`            | Store internal data (IDs, tokens). Must be validated (do not trust client). |
| **BooleanField**        | `checkbox`          | True/False input. Use for flags, toggles, agreement checkboxes.             |
| **IntegerField**        | `text`              | Integer numbers. Use for quantities, counters, ages.                        |
| **FloatField**          | `text`              | Floating-point numbers (IEEE float). Rarely used due to precision issues.   |
| **DecimalField**        | `text`              | Decimal numbers with precision. Use for money and financial values.         |
| **IntegerRangeField**   | `range`             | Slider for integer values. Use for ratings, ranges.                         |
| **DecimalRangeField**   | `range`             | Slider for decimal values. Use when a numeric range UI is needed.           |
| **DateField**           | `date`              | Date input. Stores `datetime.date`. Use for birthdays, due dates.           |
| **TimeField**           | `time`              | Time input. Stores `datetime.time`. Use for schedules, hours.               |
| **DateTimeField**       | `text`              | Date + time as text. Stores `datetime.datetime`.                            |
| **DateTimeLocalField**  | `datetime-local`    | Native browser date-time picker. Preferred for UX.                          |
| **MonthField**          | `month`             | Month picker. Stores date with day = 1.                                     |
| **SelectField**         | `select`            | Dropdown selection (single value). Use `coerce` for non-string types.       |
| **SelectMultipleField** | `select (multiple)` | Multiple selections. Returns a list of values.                              |
| **RadioField**          | `radio`             | Single selection shown as radio buttons. Alternative to SelectField.        |
| **EmailField**          | `email`             | Email input. Browser-level email validation.                                |
| **URLField**            | `url`               | URL input. Browser-level URL validation.                                    |
| **TelField**            | `tel`               | Telephone number input. UX-focused, not strict validation.                  |
| **SearchField**         | `search`            | Search input field. Mainly for UI semantics.                                |
| **ColorField**          | `color`             | Color picker input. Returns a hex color value.                              |
| **FileField**           | `file`              | Single file upload. Only stores filename; framework handles file data.      |
| **MultipleFileField**   | `file`              | Multiple file uploads. Returns list of filenames.                           |
| **SubmitField**         | `submit`            | Submit button. Useful to detect which button was pressed.                   |

### The list of WTForms built-in validators

| Validator            | Purpose                                                                | When to Use                                                                                      |
| -------------------- | ---------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------ |
| **DataRequired**     | Ensures coerced field data is truthy (non-empty, non-zero, non-false). | Use when the final parsed value must be meaningful. Avoid for numeric fields where `0` is valid. |
| **InputRequired** ⭐ | Ensures input data was actually submitted by the user.                 | Preferred validator for required fields. Use instead of `DataRequired` in most cases.            |
| **Optional**         | Allows empty input and stops further validation.                       | Use for optional fields that should skip other validators if left empty.                         |
| **Email**            | Validates email address format (uses `email_validator`).               | Use for email fields; can also check domain deliverability.                                      |
| **EqualTo**          | Compares value of two fields.                                          | Use for password confirmation, email confirmation, repeated inputs.                              |
| **Length**           | Validates string length (min/max).                                     | Use for usernames, passwords, text fields with size limits.                                      |
| **NumberRange**      | Validates numeric value is within a range.                             | Use for prices, quantities, ratings, percentages.                                                |
| **Regexp**           | Validates input using a regular expression.                            | Use for custom patterns (usernames, codes, formats).                                             |
| **URL**              | Validates URL format via regex.                                        | Use for website links; allow localhost or IP if needed.                                          |
| **IPAddress**        | Validates IPv4 and/or IPv6 addresses.                                  | Use for network configuration, firewall rules, logs.                                             |
| **MacAddress**       | Validates MAC address format.                                          | Use for hardware/network identification forms.                                                   |
| **UUID**             | Validates UUID format.                                                 | Use for IDs, tokens, API identifiers.                                                            |
| **AnyOf**            | Ensures value is in an allowed list.                                   | Use when value must match a fixed whitelist.                                                     |
| **NoneOf**           | Ensures value is NOT in a forbidden list.                              | Use to block reserved words, banned values.                                                      |
| **ReadOnly**         | Ensures submitted value matches existing field data.                   | Use for fields that must not be changed by the client.                                           |
| **Disabled**         | Ensures no data is submitted for the field.                            | Use for disabled fields that should never be modified.                                           |

## Form Handling in View Functions

- `form.validate_on_submit` method of the form returns True when the form was submitted and the data was accepted by all the field validators.
- `form.name.data` you don’t have to pass request.form to Flask-WTF; it will load automatically

```
@app.route('/', methods=['GET', 'POST'])
def index():
    name = None
    form = NameForm()
    if form.validate_on_submit():
        name = form.name.data
        form.name.data = ''
    return render_template('index.html', form=form, name=name)
```

## HTML Rendering of Forms

- A CSRF token hidden field is created automatically. You can render this in your template by `form.csrf_token`
- If your form has multiple hidden fields, you can render them in one block using `form.hidden_tag()`.
- Rendering the `novalidate` attribute on the form tag, or the `formnovalidate` attribute on a submit button

```
<form method="POST" action="{{url_for('login')}}" novalidate>
    #  {{ form.hidden_tag() }}
    {{ form.csrf_token }}
    {{ form.name.label(class="css_class") }} {{ form.name(size=20, class="css_class") }}
    <input type="submit" value="Go">
</form>
```

## Display any error messages

```
@app.route('/submit', methods=['GET', 'POST'])
def submit():
    form = MyForm()
    if form.validate_on_submit():
        return redirect('/success')
    return render_template('submit.html', form=form)
```

- If your forms include validation, you’ll need to add to your template to display any error messages. Using the `form.name` field from the example above, that would look like this:

```
{% if form.name.errors %}
    <ul class="errors">
    {% for error in form.name.errors %}
        <li>{{ error }}</li>
    {% endfor %}
    </ul>
{% endif %}
```

## Redirects and User Sessions

- Consequently, it is considered good practice for web applications to never leave a `POST` request as the last request sent by the browser
- This is achieved by responding to POST requests with a redirect instead of a normal response
- When the browser receives a redirect response, it issues a `GET` request for the redirect URL, and that is the page that it displays
- But this approach brings a second problem. When the application handles the `POST` request, it has access to the name entered by the user in form.name.data, but as soon as that request ends the form data is lost. Because the POST request is handled with a redirect, the application needs to store the name so that the redirected request can have it and use it to build the actual response.
- Applications can “remember” things from one request to the next by storing them in the user session, a private storage that is available to each connected client
- `form.name.data` is now placed in the user session as `session['name']` so that it is remembered beyond the request

```
from flask import Flask, render_template, session, redirect, url_for
@app.route('/', methods=['GET', 'POST'])
def index():
    form = NameForm()
    if form.validate_on_submit():
        session['name'] = form.name.data
        return redirect(url_for('index'))
    return render_template('index.html', form=form, name=session.get('name'))
```

## Message Flashing

- The flashing system basically makes it possible to record a message at the end of a request and access it next request and only next request

```
from flask import Flask, render_template, session, redirect, url_for, flash
@app.route('/', methods=['GET', 'POST'])
def index():
    form = NameForm()
    if form.validate_on_submit():
        old_name = session.get('name')
        if old_name is not None and old_name != form.name.data:
            flash('Looks like you have changed your name!')
        session['name'] = form.name.data
        return redirect(url_for('index'))
    return render_template('index.html',form = form, name = session.get('name'))
```

```
{% block content %}
<div class="container">
    {% for message in get_flashed_messages() %}
    <div class="alert alert-warning">
        <button type="button" class="close" data-dismiss="alert">&times;</button>
        {{ message }}
    </div>
    {% endfor %}
    {% block page_content %}{% endblock %}
</div>
{% endblock %}

```

## Custom validations

- There are two ways to provide custom validators. By defining a custom validator and using it on a field

```
from wtforms.validators import ValidationError

def is_42(form, field):
    if field.data != 42:
        raise ValidationError('Must be 42')

class FourtyTwoForm(Form):
    num = IntegerField('Number', [is_42])
```

- Or by providing an in-form field-specific validator:

```
class FourtyTwoForm(Form):
    num = IntegerField('Number')

    def validate_num(form, field):
        if field.data != 42:
            raise ValidationError('Must be 42')
```

## Custom widgets

- In the below example, we extended the behavior of the existing TextInput widget to append a CSS class as needed

```
class MyTextInput(TextInput):
    def __init__(self, error_class='has_errors'):
        super(MyTextInput, self).__init__()
        self.error_class = error_class

    def __call__(self, field, **kwargs):
        if field.errors:
            c = kwargs.pop('class', '') or kwargs.pop('class_', '')
            kwargs['class'] = '%s %s' % (self.error_class, c)
        return super(MyTextInput, self).__call__(field, **kwargs)
```

- However, widgets need not extend from an existing widget, and indeed don’t even have to be a class. For example, here is a widget that renders a SelectMultipleField as a collection of checkboxes

```
def select_multi_checkbox(field, ul_class='', **kwargs):
    kwargs.setdefault('type', 'checkbox')
    field_id = kwargs.pop('id', field.id)
    html = ['<ul %s>' % html_params(id=field_id, class_=ul_class)]
    for value, label, checked, render_kw in field.iter_choices():
        choice_id = '%s-%s' % (field_id, value)
        options = dict(kwargs, name=field.name, value=value, id=choice_id)
        if checked:
            options['checked'] = 'checked'
        html.append('<li><input %s /> ' % html_params(**options))
        html.append('<label for="%s">%s</label></li>' % (choice_id, label))
    html.append('</ul>')
    return ''.join(html)

class TestForm(Form):
    tester = SelectMultipleField(choices=my_choices, widget=select_multi_checkbox)
```

# Databases

# Other

## How to decode user session

```
import base64

base64.urlsafe_b64decode( '<<user_session>>===' )

```
