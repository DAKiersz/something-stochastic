# Conda - MkDocs Environment

## Synopsis

Using your favourite shell, we create an environment and install required dependencies for generating documentation based on Python `__doc__ `strings.

## Steps

Create the environment and install packages (you can also use `conda/mkdocs.yml` with `conda env create -f conda/mkdocs.yml`)

```
conda create -n mkdocs python=3.9
```

```
conda activate mkdocs
```

```
pip install mkdocs mkdocs-material "mkdocstrings[python]" pymdown-extensions
```

Verify packages are in your environment;

```
conda list
```

Build the static website from the root directory (where `mkdocs.yml` is)

```
mkdocs build
```

Start a server on localhost:

```
mkdocs serve
```

