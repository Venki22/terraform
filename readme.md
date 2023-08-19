### There are various types of tools that can allow you to deploy infrastructure as code:
- Terraform
- CloudFormation
- Heat
- Ansible
- SaltStack
- Chef,Puppet and others

### Configuration Management VS Infrastructure Orchestration
Ansible, Chef, Puppet are configuration management tools which means that they are 
primarily designed to install and manage software on existing servers.

Terraform, CloudFormation are the infrastructure orchestration tools which basically 
means they can provision the servers and infrastructure by themselves.

Configuration Management tools can do some degree of infrastructure provisioning, but 
the focus here is that some tools are going to be better fit for certain type of tasks.

### Terraform:
-  Supports multiple platforms, has hundreds of providers.
- Simple configuration language and faster learning curve.
-  Easy integration with configuration management tools like Ansible.
-  Easily extensible with the help of plugins

### Document - Terraform Downloads Page

### Terraform Code
https://github.com/zealvora/terraform-beginner-to-advanced-resource

https://registry.terraform.io/browse/providers

### Note:
- The core concepts, standard syntax remains similar across all providers.
- If you learn the basics, you should be able to work with all providers easily.

### terraform destroy
### Approach 1 - Destroy ALL
terraform destroy allows us to destroy all the resources that are created within the folder.

### Approach 2 - Destroy Some
terraform destroy with -target flag allows us to destroy specific resource.
The -target option can be used to focus Terraform's attention on only a subset of 
resources.

### Approach 3 - Destroy Some
comment block of code and raise destroy command

**Combination of : Resource Type + Local Resource Name**
**terraform destroy -target aws_instance.web-instance**

### Desired & Current State
Terraform tries to ensure that the deployed infrastructure is based on the desired state.
If there is a difference between the two, terraform plan presents a description of the 
changes necessary to achieve the desired state

### You can override that behavior by adding the -upgrade option when you run terraform init
**terraform init -upgrade**

- Variable file name:terraform.tfvars
- We can pass custom varialbe file using below command.
**terraform plan -var-file="custom-variable-file.tfvars"**
- terraform init
- terraform plan
- terraform plan -out=path
- terraform refresh
- terraform plan -refresh=false
- terraform plan -refresh=false -target=resource-name
- terraform plan -target=resource-name
- terraform apply
- terraform destroy
- terraform destroy -target
- terraform validate
- terraform fmt
- terraform -auto-approve
- terraform taint (or) terrafrom apply -replace
- terraform output variable-name
- terraform refresh
- terraform console



**terrafrom graph**
```
  https://graphviz.org/download/
  yum install graphviz -y
  vi graph.dot
  paste the content of terraform graph output
  cat graph.dot | dot -Tsvg > graph.svg
  cat graph.svg
  Open graph.dot file from window explre to see image.
```

**meta-argument**
```
resource..{
        lifecycle {
          ignore_changes = [tags,instance_type]
        }
}

resource..{
        lifecycle {
          ignore_changes = all
        }
}

resource..{
        lifecycle {
          create_before_destroy = true
        }
}

resource..{
        lifecycle {
          prevent_destroy = true
        }
}
```


