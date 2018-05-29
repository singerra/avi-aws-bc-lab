# Lab Build Template for Frey

## Prereqs

Install terraform and ansible and make sure you have the avi config role installed: https://github.com/avinetworks/ansible-role-aviconfig

## Usage
Export the following variables as environment variables.

*TF_VAR_access_key - AWS access key
*TF_VAR_secret_key - AWS secret key
*TF_VAR_password - Avi Controller password

The name can be anything you like, shouldn't be to long.

First initialize the environment using `make init`.

After this is done run `make` or `make apply` using the parameter "environment=name".

    Example: make environment=frey-lab

This will apply the terraform configuration and deploy the controller, some perf server clients and so on.

To destroy the environment run `make destroy environment=frey-lab`

## Build multiple environments
Use `make15.sh` and `destroy15.sh`as an example on how to build/destroy multiple environments at once.

## Caveats
You might have to delete the environment manually if you do not unconfigure the cloud configuration in the controller as terraform doesn't know about the services engines and will fail to destroy the environment as unkown objects are in it.