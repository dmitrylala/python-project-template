# {{ cookiecutter.project_name }}

## Подготовка окружения

Для этого достаточно выполнить `make vendor`. Под капотом используется uv, если его нет, установить можно так: `pip install --user uv`.

Ознакомься с другими полезными командами:
```{{ cookiecutter.syntax_highlighting }}
$ make
vendor            Install all necessary packages
fmt               Format code
lint              Lint code
test              Run test. You can run `make test tests/path/file.py`
clean             Clean generated files
```
