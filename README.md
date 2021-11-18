# Rain API Server with Visualization Examples

An example project for RESTful API development using OpenAPI and Python. It contains a few examples for data visualization on a web browser.

## Installation

checkout <https://gitlab.com/cjaikaeo/rain-vis-daq-2021f>

```bash
# [if not yet have it] install OpenAPI-to-GraphQL
$ npm install -g openapi-to-graphql-cli@2.5.0
```

download/add `openapi-generator-cli-4.3.1.jar` to the project

```bash
# generate,update /autogen
$ java -jar openapi-generator-cli-4.3.1.jar generate -i openapi/rain-api.yaml -o autogen -g python-flask

$ cd autogen
$ pip install -r requirements.txt

# start sever
$ python -m openapi_server
```

testing: go to <http://localhost:8080/rain-api/v3/ui>

create `config.py`

```py
OPENAPI_AUTOGEN_DIR = 'autogen'
DB_HOST = 'iot.cpe.ku.ac.th'
DB_USER = <USERNAME> # 'b62xxxxxxxx'
DB_PASSWD = <PASSWORD> # 'email@ku.th'
DB_NAME = 'rain'
```

run [app.py](app.py)

in another terminal

```bash
# Start GraphQL IDE
# from v2 add `--cors` to cross-origin resource sharing
$ openapi-to-graphql --cors -u http://localhost:8080/rain-api/v3 openapi/rain-api.yaml
```

open [index](html/index.html) on browser
