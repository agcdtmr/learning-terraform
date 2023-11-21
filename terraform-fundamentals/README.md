# terraform-fundamentals

Terraform is an infrastructure as code (IaC) tool that enables to define and provision infrastructure resources in a declarative way.

What is declarative?

In this project about [Terraform Fundamentals](https://www.azurecitadel.com/terraform/fundamentals/), I dive deep into:

- [x] Initialise: Use `terraform init` to initialise a terraform environment, downloading providers and modules.
- [x] Format: Create a variables.tf and main.tf. Use `terraform fmt` to automatically format the files.
- [x] Validate: Use `terraform validate` to confirm that the files are syntactically and logically sound. Add a new variable to variables.tf.
- [x] Plan: Start working with terraform.tfvars to specify variable values and then use `terraform plan` to display the actions that Terraform will take.
- [x] Apply: Apply the configuration to create resources and then examine the state file.
- [ ] Adding resources: Use the azurerm documentation to add a resource to the configuration.
- [ ] Locals and outputs: Use locals and functions to generate a unique value, and add a couple of outputs.
- [ ] Managing state: Common lifecycle management areas that deal with state with refresh, ignore, move and taint.
- [ ] Importing resources: Step through an example of importing an existing resource into Terraform.
- [ ] Destroy: Short lab to tear down the environment.



## Prerequisites

- Azure account
- Azure subscription
- Cloud Shell

I decided to use the Azure portal cloud shell instead, as it has a built-in bash where I can use the terraform commands without needing to install Terraform locally.

From the image below I've learn that when using the cloud shell I need to assign it to a resource group, storage account and a file share.
![](https://github.com/agcdtmr/terraform-fundamentals/blob/main/images/Screenshot%202023-10-11%20104644.png)

## Helpful links

- https://www.azurecitadel.com/
- https://www.azurecitadel.com/terraform/fundamentals/adding_resources/#azure-container-instance

## Initialise

- create a provider.tf in Cloud Shell. Specifying the azurerm provider and its required configuration.
- use the `terraform init` command to download the azurerm provider locally (In Terraform, a provider is a plugin that allows Terraform to interact with a specific cloud or infrastructure platform. For Azure, the azurerm provider is used to define and manage Azure resources.)
- why do i need to initialise terraform

Initializing Terraform is a necessary step before you can use it to create, modify, or manage infrastructure. 

Provider Installation: When you write Terraform configurations, you specify which providers you will be using (e.g., AWS, Azure, Google Cloud, etc.) and their versions. The initialization process downloads the specified providers and any required plugins locally, ensuring that Terraform can interact with your chosen cloud or infrastructure platform.

Module Installation: If you're using modules in your Terraform configurations, the terraform init command will download the modules you reference in your code.

Backend Configuration: Terraform allows you to configure backends for storing the state of your infrastructure. State is a critical part of Terraform's functionality as it keeps track of the resources Terraform manages. During initialization, you can configure the backend you want to use, whether it's a local file, remote storage, or a service like AWS S3 or Azure Blob Storage.

Validation: Terraform performs a validation of your configuration files during initialization. It checks for syntax errors, required variables, and any missing dependencies in your code. This helps catch errors early in the process.

Locking and State Configuration: Terraform uses a state file to keep track of the current state of your infrastructure. Initialization helps configure state locking, which prevents concurrent modifications from multiple users to avoid conflicts.

Plugin Validation: Terraform validates that the installed provider plugins match the configurations in your code. This helps ensure that your code is compatible with the installed providers and their versions.

Consistency and Reproducibility: Initializing Terraform creates a consistent and reproducible environment for managing your infrastructure. By explicitly downloading the required providers and modules, it ensures that every team member and environment is working with the same codebase.

Security: By downloading only the required providers and plugins, Terraform can verify the authenticity and integrity of the downloaded code, enhancing security.

In summary, running terraform init is a crucial step in setting up your Terraform environment, preparing it to work with your infrastructure configurations, and ensuring that you have the necessary dependencies installed and validated before any actual changes are made to your infrastructure.

![](https://github.com/agcdtmr/terraform-fundamentals/blob/main/images/Screenshot%202023-10-11%20151744.png)
![](https://github.com/agcdtmr/terraform-fundamentals/blob/main/images/Screenshot%202023-10-11%20151853.png)


## Format

- Create a variables.tf and main.tf.
- Use `terraform fmt` to automatically format the files or to tidy them up.
- The format used within Terraform files is called HashiCorp Configuration Language or HCL for short.

![](https://github.com/agcdtmr/terraform-fundamentals/blob/main/images/Screenshot%202023-10-11%20153809.png)
![](https://github.com/agcdtmr/terraform-fundamentals/blob/main/images/Screenshot%202023-10-11%20155302.png)
![](https://github.com/agcdtmr/terraform-fundamentals/blob/main/images/Screenshot%202023-10-11%20155535.png)
![](https://github.com/agcdtmr/terraform-fundamentals/blob/main/images/Screenshot%202023-10-11%20155547.png)


## Validate

- Use `terraform validate` to confirm that the files are syntactically and logically sound. Add a new variable to variables.tf.

💪 Challenge: Update the configuration to match the requirements below.

- [x] Create a new variable named location
- [x] Default the value to West Europe
- [x] Add a description for the variable: Azure region
- [x] Update the resource group to use the location variable
- [x] Format and validate your files

![](https://github.com/agcdtmr/terraform-fundamentals/blob/main/images/Screenshot%202023-10-12%20114900.png)



## Plan

- create a terraform.tfvars
- specify the value for location
- use `terraform plan` to display the actions that Terraform will take
- display a plan
- Terraform plan is like a blueprint for building or changing things in the digital world. Imagine you want to create a virtual house, like in a video game. You need a plan to know where to put the walls, doors, and windows, right? Terraform does the same thing, but for setting up or changing computer resources like servers, databases, and networks.
- When you use Terraform to create a plan, it checks your instructions (code) and tells you what it's going to do before actually doing it. It shows you the steps it will take, such as creating or deleting resources, and any potential problems it might encounter. This helps you review and understand the changes before you apply them, kind of like reviewing a blueprint before building your virtual house. It's a way to catch mistakes and make sure everything goes smoothly when making changes to your digital infrastructure.

![](https://github.com/agcdtmr/terraform-fundamentals/blob/main/images/Screenshot%202023-10-12%20121635.png)

## Apply

- apply configuration `terraform apply`
- create the resource group
- List the resources in the state file `terraform state list`
- Display the attributes for a resource `terraform state show azurerm_resource_group.basics`
- view the state file `jq . < terraform.tfstate`

![](https://github.com/agcdtmr/terraform-fundamentals/blob/main/images/Screenshot%202023-10-12%20124312.png)
![](https://github.com/agcdtmr/terraform-fundamentals/blob/main/images/Screenshot%202023-10-12%20124512.png)
![](https://github.com/agcdtmr/terraform-fundamentals/blob/main/images/Screenshot%202023-10-12%20124529.png)

## Adding resources

- browse the aka.ms/terraform documentation
- add a resource to create an Azure Container Instance
- plan and apply the change

**If no updates I'm learning [Azure Networking](https://github.com/agcdtmr/azure-networking/tree/main)**

More Challenge: Deploy [Azure Networking](https://github.com/agcdtmr/azure-networking/tree/main) using Terraform
