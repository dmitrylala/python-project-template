FROM python:{{ cookiecutter.python_version }}

# Dev deps (Remove for prod)
RUN apt-get update && apt-get install -y vim wget curl git

RUN sh -c "$(wget -O- https://github.com/deluan/zsh-in-docker/releases/download/v1.1.1/zsh-in-docker.sh)" -- \
        -t robbyrussell \
        -p https://github.com/zsh-users/zsh-autosuggestions

ENV ZSH_AUTOSUGGEST_HIGHLIGHT_STYLE="fg=#dedede,bg=#9c9c9c,bold,underline"
# Dev deps end

RUN python -m pip install --upgrade pip && pip install poetry -U

COPY pyproject.toml poetry.lock ./
COPY {{ cookiecutter.project_slug }} ./{{ cookiecutter.project_slug }}

RUN poetry config virtualenvs.create false \
        && poetry install --without dev --no-interaction --no-ansi

ENTRYPOINT [ "zsh" ]
