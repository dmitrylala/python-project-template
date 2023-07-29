ARG PYTHON_VERSION="{{ cookiecutter.python_image }}"

FROM python:${PYTHON_VERSION} as python_stage

RUN apt-get update && \
	apt-get install -y git

# Install poetry
RUN python -m pip install --upgrade pip && pip install poetry -U

WORKDIR /venv

# Copy from local
COPY pyproject.toml poetry.lock ruff.toml README.md ./
COPY {{ cookiecutter.project_slug }} ./{{ cookiecutter.project_slug }}

# Installing dependencies
RUN poetry config virtualenvs.create false \
	&& poetry install --without dev --no-interaction --no-ansi
