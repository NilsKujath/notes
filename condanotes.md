# Notes on Conda

`conda --version` displays version.
`conda update conda` updates conda to the current version.

## About Environments

## Managing Environments

A new environment `<new_environment_name>` with a specific version of python is created by running:
```
$ conda create --name <new_environment_name> python=3.9
```
This environment can then be activated by running:
```
$ conda activate <new_environment_name>
```
Check which environments exists (`*` marks the active one) by running: `conda info --envs`.

## Managing Packages
