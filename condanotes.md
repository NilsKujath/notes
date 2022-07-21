# Notes on Conda

`conda --version` displays version.
`conda update conda` updates conda to the current version.

## About Environments

The path under which Conda stores virtual environment can be seen by running `conda info --envs`.
On MacOS (if using anaconda3) they are usually stored under `~/opt/anaconda3/envs/`.

## Managing Environments

### Creating Environments
A new environment with no installed packages can be created by running:
```
$ conda create --name <new_environment_name>
```
Installing all needed packages at the same time avoids dependency issues. A new environment `<new_environment_name>` with a specific version of python and specific pacckages can be created by running:
```
$ conda create --name <new_environment_name> [ python[=i.i] ] [ <package_name>[=i.i.i] ]*
```

An environment can then be activated or deactivated by running either:
```
$ conda activate <new_environment_name>
$ conda deactivate <new_environment_name>
```
Check which environments exists (`*` marks the active one) by running: `conda info --envs`.

### Removing Environments

To remove an environemnt, run:
```
$ conda env remove --name <environment_name>
```

## Managing Packages

To list the packages that are in a specific environment, run:
```
$ conda list -n <environment_name>
```
