# Terraform - Resources

## CLI Cheatsheet

A quick copy and paste based on the Terraform Docker tutorial deploying a NGNIX container.

* `terraform init` - Initialise the project, which downloads a plugin called a `provider` that lets Terraform interact with Docker.

* `terraform fmt` - Format the Terraform configuration files
* `terraform validate` - Validate the Terraform configuration files
* `Terraform plan` - Show what Terraform will do before it does it
* `terraform plan -out=planfile` - Create a plan file with plan

* `terraform apply` - Provision the server container with apply
* `terraform apply <planfile>` - Apply a specific plan file with apply
* `terraform apply -var container_name=ExampleNginxContainer2` - override the default value of the `container_name` variable with apply

* `terraform show` - Show the state of a resource
* `terraform state list` - List the resources in the state file with state list
* `terraform state show docker_container.nginx` - Show the state of the NGINX server container with state show
* `terraform state rm docker_container.nginx` - Remove the NGINX server container from the state file with state rm
* `terraform state mv docker_container.nginx docker_container.nginx2` - Rename the NGINX server container in the state file with state mv

* `terraform destroy` - Destroy all resources in the state file

* `terraform output` - Show the output values from the Terraform configuration with output (apply apply and if you have outputs)
* `terraform graph` - Creates a visual representation of a configuration or a set of planned changes

## Resources

* https://developer.hashicorp.com/terraform/tutorials/certification - Main Study Guide

* https://developer.hashicorp.com/terraform/tutorials/certification-associate-tutorials-003 -Associate Tutorial List (003)

* https://developer.hashicorp.com/terraform/tutorials/docker-get-started - Get Started with TF and Docker