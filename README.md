# Jinja for Naja Atra

## What's this?

This is a Jinja extension for pythone simple http server (https://github.com/keijack/python-simple-http-server)

## How to use?

install

```
python3 -m pip install simple_http_server_jinja
```

```python
from naja_atra import route, server
from naja_atra_jinja import JinjaView, set_env
from jinja2 import Environment, FileSystemLoader

@route("/index")
def index(name: str = "world"):
    return JinjaView("index.html", {"name": name})

def main():
    env = Environment(loader=FileSystemLoader("/you/own/template/folder"))
    set_env(env)
    server.start(port=9090)

if __name__ == "__main__":
    main()

```

For the above code, the templates should be placed in the `templates` folder in your project's root. 

```
|--templates
|----index.html
|----page.html
|--main.py
```

You can set your own Jinja2 Environment via `set_env` function:

```python
from naja_atra import route, server
from naja_atra_jinja import JinjaView, set_env
from jinja2 import Environment, FileSystemLoader

@route("/index")
def index(name: str = "world"):
    return JinjaView("index.html", {"name": name})

def main():
    env = Environment(loader=FileSystemLoader("/you/own/template/folder"))
    set_env(env)
    server.start(port=9090)

if __name__ == "__main__":
    main()
```