# TERRAFORM

### Providers

Providers are a logical upstream of an API. They are responsible for understanding API interactions and exposing resources.

Providers are plugins that Terraform uses to create and manage resources on a specific platform (e.g. AWS, Azure, etc). Providers are analogous to libraries. They are separate from Terraform and have their own releases. 

Providers can be official or community. They have their own documentation, found in the terraform registry. 

Example config: 

```t
terraform {
  required_providers {
    # each provider requires its own argument with source and version args
    aws = {
      # source: where terraform can download the provider
      source  = "hashicorp/aws"
      # version: specifies which subset of versions the module is compatible with
      # "~>" means all versions within the major version specified, e.g. 4.1 and 4.2 but not 5.0
      version = "~> 4.0"
    }
  }
}

# Configure the AWS Provider
# the provider must exist within required_providers above
provider "aws" { 
    # the region argument (and other arguments0 is specific to the provider
  region = "us-east-1"
}

```

Configuration Syntax: 
 - can be written in .tf or .tf.json (json-compatible) formats
 - mostly just .tf
 - both are defined in a spec called HCL (Hashicorp Configuration Language)

HCL is composed of blocks and arguments:

```t

provider "aws" { # block type: provider, label: "aws"
    region = "something" # argument: region, argument value: "something"
}

```
Some block types require differing number of labels. Single line comments use # or //; multipline comments use /* ... */

