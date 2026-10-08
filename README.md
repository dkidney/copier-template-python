# copier-template-python

A copier template for python projects.

## install copier

This template uses copier, which is a library and CLI app for rendering project templates.

https://copier.readthedocs.io/en/stable/updating/

You can install it using homebrew

```sh
brew install copier
```

## create a project

To generate a project from this template via the command line using one of the following methods:

```sh
src=https://github.com/dkidney/copier-template-python.git
dst=project/folder

# from a branch
copier copy --vcs-ref main ${src} ${dst}

# from a tag
copier copy --vcs-ref v0.2.0 ${src} ${dst}

# from a commit
copier copy --vcs-ref a1b2c3d4 ${src} ${dst}

# from a cloned local version of the template repo
copier copy --vcs-ref HEAD ~/github/copier-template-python ${dst}
```

## prompts

After you have submitted the `copier copy` command you will be present with a series of input prompts (all of which have defaults)

* `Project name`
* `Package name` - by default this will convert your project name into lower_snake_case
* `Project description`
* `Your name`
* `Python version`
* `Include a data folder`

## project structure

The project tree should look something like this:

```
.
├── main.py
├── Makefile
├── notebooks
│   └── helloworld.ipynb
├── pyproject.toml
├── README.md
├── src
│   └── {{ package_name }}
│       ├── __init__.py
│       └── helloworld.py
└── tests
    └── test_import.py
```

You can set up a venv and install dependencies using the Makefile

```sh
make clean # removes and existing .venv files
make venv # sets up a new .venv
make sync # uv sync
```

And you can run tests and checks 

```sh
make test # uv run pytest
make check # uv run ruff check
make format # uv run ruff format --check
```

You can also run pre-commit on your staged files

```sh
uv run pre-commit install  # installs the pre-commit hook
uv run pre-commit run --all-files  # checks all staged files
```
