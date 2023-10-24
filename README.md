Python Project Template
=======================

You can use this repository as a template when creating a new repository on GitHub, to get my preferred setup for a Python project.

After creating the new project, there are a few things you'll need to configure.

## Rename the main package

You'll need to rename the package from "mylib" to something sensible:

```sh
git mv mylib newname
sed -i'' -e 's/mylib/newname/' tests/* .projections.json
```

## Choosing the Python version

The version of Python that your project uses is needed by the GitHub Action that runs the tests, and perhaps by your local Python installation tool.

You can create it like this:

```sh
echo 3.11.3 > .python-version  # 3.11.3 is just an example
```

## Run the tests locally

You need to get everything installed, and that first test running. Start by creating a virtual environment:

```sh
python3 -m venv .venv
activate
```

Now we can install our development tools:

```sh
pip install --upgrade pip
pip install pip-tools
pip-compile dev-requirements.in
pip-sync dev-requirements.txt
```

Once you've got non-development dependencies you can specify them in `requirements.in`, running these commands to install them alongside your development dependencies:

```sh
pip-compile requirements.in
pip-sync requirements.txt dev-requirements.txt
```
