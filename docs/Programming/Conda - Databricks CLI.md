# Conda - Databricks CLI

## Synopsis

We can use `conda` Python environments to setup and use Databricks CLI without impacting/altering your host Python environment.

## 1) Create `conda` environments and install `databricks-cli`

### CLI

```shell
conda create --name databricks pip

conda activate databricks # Activate the environment

pip install --upgrade databricks-cli
```

The Python pseudo-environment with databricks-cli is activated ready for Step 2.

### YAML Environment

Define the following in `databricks.yml` 

```yaml
name: databricks
channels:
  - conda-forge
  - defaults
dependencies:
  - python=3.11
  - pip
  - pip:
	  - databricks-cli
```

```shell
conda env create --file databricks.yml
#or
conda env update -f <path_to_yaml_file>`
```

You can then activate the environment ready for Step 2.

```
conda activate databricks
```

## 2) Configure authentication

### Using a PAT

From Databricks, go to User Settings > Access Tokens > Generate New Access Token

In your dotfile (e.g., `.zshrc`)

```
export DATABRICKS_TOKEN=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

Then run:

```shell
databricks configure --token
```

### Using Azure AAD

```shell
az account set --subscription xxxx # Azure subscription

token_response=$(az account get-access-token --resource xxxxxxxxxxxxxxxxxxxxxxxxxx) # Databricks ResourceID

export DATABRICKS_AAD_TOKEN=$(jq .accessToken -r <<< "$token_response")

databricks configure --aad-token
```



