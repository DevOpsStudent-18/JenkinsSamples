# Exam Topics Questions

@thatonecodes

## Examtopics Terraform Associate_22 question #1

You can access state stored with the local backend by using the terraform_remote_state data source.

**A:** True

**B:** False



**Answer: A**

**Timestamp: 2023-01-14 07:14:00**

[View on ExamTopics](https://www.examtopics.com/discussions/hashicorp/view/95150-exam-terraform-associate-topic-1-question-194-discussion/)

Comments: [Stanislav4907] Selected Answer: A The terraform_remote_state data source allows you to retrieve outputs from the state of another Terraform configuration, which can be stored in a local or remote backend. To use the terraform_remote_state data source with a local backend, you would define the path to the state file in the backend configuration block of your Terraform configuration, and then use that path in the data "terraform_remote_state" block to retrieve the desired output values. [FarziWaliMarzi] Selected Answer: A https://developer.hashicorp.com/terraform/language/state/remote-state-data data "terraform_remote_state" "vpc" { backend = "local" config = { path = "..." } } # Terraform >= 0.12 resource "aws_instance" "foo" { # ... subnet_id = data.terraform_remote_state.vpc.outputs.subnet_id } # Terraform <= 0.11 resource "aws_instance" "foo" { # ... subnet_id = "${data.terraform_remote_state.vpc.subnet_id}" } [lavendran93] Selected Answer: B The terraform_remote_state data source is used to access state from a remote backend, such as S3, Azure Blob Storage, or Terraform Cloud. It does not work with the local backend. The local backend stores the state file on your local filesystem, and to access it, you need to handle it directly, not through terraform_remote_state. [master9] Selected Answer: B As asking for Local not remote state file [VSMu] Selected Answer: A Example https://developer.hashicorp.com/terraform/language/state/remote-state-data#example-usage-local-backend [Nunyabiznes] Selected Answer: B The terraform_remote_state data source is used to access state data stored in a remote backend (such as S3, GCS, or Terraform Cloud). It is not designed to access local backend state files directly. However, if you want to access data from another Terraform configuration's local state, you can use output variables and pass the values between configurations using input variables or other methods. [camps] Selected Answer: B The terraform_remote_state data source is used to access the state data from another Terraform configuration that is stored in a remote backend, not a local backend. This data source enables you to fetch the outputs of another Terraform project and use them as input variables in your current Terraform project. When using the local backend, the Terraform state is stored in a local file (usually named terraform.tfstate). This means the state is not accessible through the terraform_remote_state data source, as it is not stored remotely. [Strib] Selected Answer: A Example Usage (local Backend) https://developer.hashicorp.com/terraform/language/state/remote-state-data#example-usage-local-backend [David_C_90] Selected Answer: A I tested this and I believe this is correct. Check the link https://developer.hashicorp.com/terraform/language/state/remote-state-data#example-usage-local-backend Note that the state file must already exist and the data you will obtain is the data present on the file: if you change the terraform configuration corresponding to the state you are trying to read, you will obtain the "old" data. [khaled_razouk] Selected Answer: B I'll go with B [rotimislaw] Selected Answer: B Seems B to me [shahin_am2] B. False. According to the Terraform documentation, the terraform_remote_state data source can be used to access state data stored in a remote backend. This allows you to use output values from one Terraform configuration as input values for another configuration. However, the local backend is not considered a remote backend, because it stores state data locally on disk. Therefore, you cannot use the terraform_remote_state data source to access state stored with the local backend. [princajen] Selected Answer: B B. False. The terraform_remote_state data source is used to fetch outputs from the state of a different Terraform configuration, which is stored remotely, and use them as input for the current configuration. It is used with remote backends, not local ones. [pyro7] False. The local backend stores state locally on the same machine as the Terraform configuration files, and it is not accessible over a network connection. To access state stored in a remote backend, you need to use the terraform_remote_state data source. [Abuu] Selected Answer: A this is correct. The terraform_remote_state data source allows you to access state stored with the local backend, enabling you to share and reference state between different configurations. This is especially useful when using multiple configurations to manage different parts of the same infrastructure. [Daro_] Selected Answer: A As per below documentation https://developer.hashicorp.com/terraform/language/state/remote-state-data and example of configuration data "terraform_remote_state" "vpc" { backend = "local" config = { path = "..." } } Answer is: [ A ] [Daro_] As per below documentation https://developer.hashicorp.com/terraform/language/state/remote-state-data and example of configuration data "terraform_remote_state" "vpc" { backend = "local" config = { path = "..." } } Answer is: [ A ] [kounilasco] Selected Answer: B it is false [gekkehenk] Selected Answer: B terraform state is the right command. That can be used with "list" or "show".
----------------------------------------

## Examtopics Terraform Associate_22 question #3

You have been working in a Cloud provider account that is shared with other team members. You previously used Terraform to create a load balancer that is listening on port 80. After some application changes, you updated the Terraform code to change the port to 443.

You run terraform plan and see that the execution plan shows the port changing from 80 to 443 like you intended, and step away to grab some coffee.

In the meantime, another team member manually changes the load balancer port to 443 through the Cloud provider console before you get back to your desk.

What will happen when you terraform apply upon returning to your desk?

**A:** Terraform will fail with an error because the state file is no longer accurate.

**B:** Terraform will change the load balancer port to 80, and then change it back to 443.

**C:** Terraform will not make any changes to the Load Balancer and will update the state file to reflect any changes made.

**D:** Terraform will change the port back to 80 in your code.



**Answer: C**

**Timestamp: 2023-01-14 07:16:00**

[View on ExamTopics](https://www.examtopics.com/discussions/hashicorp/view/95151-exam-terraform-associate-topic-1-question-195-discussion/)

Comments: [gekkehenk] Selected Answer: C As the state is refreshed during the "apply" no changes will be made on the cloud. Terraform will rather update it state file. [shanker_sumit] option A. Terraform will fail with an error because the state file is no longer accurate. As person has made the changes via the console not through terraform . Hence , it give an error as changes are made outside of terraform. [camps] Selected Answer: C It's C [sribalaje] Selected Answer: C C is correct answer
----------------------------------------

## Examtopics Terraform Associate_22 question #5

In a Terraform Cloud workspace linked to a version control repository, speculative plan runs start automatically when you merge or commit changes to version control.

**A:** True

**B:** False



**Answer: A**

**Timestamp: 2023-01-16 09:02:00**

[View on ExamTopics](https://www.examtopics.com/discussions/hashicorp/view/95512-exam-terraform-associate-topic-1-question-196-discussion/)

Comments: [thure] Selected Answer: A https://developer.hashicorp.com/terraform/cloud-docs/run/modes-and-options VCS: When a workspace is connected to a VCS repository, HCP Terraform automatically starts a speculative plan when someone opens a pull request (or merge request) against the selected branch of that repository. The pull/merge request view in your VCS links to the speculative plan, and you can also find it in the workspace's run list. [Igein] Selected Answer: B Speculative plan runs in Terraform Cloud workspaces do not automatically start when you merge or commit changes to version control. They are triggered under specific circumstances: When a Pull Request (PR) is created or updated in the linked version control repository: Terraform Cloud automatically runs a speculative plan to show the impact of proposed changes before merging the PR. When a branch is pushed to the repository: Speculative plans are run for changes that are not yet applied (e.g., draft changes or PRs). [nickylake] B;speculative plan runs are automatically triggered when a pull request (PR) is opened or updated, allowing you to preview the potential impact of proposed changes before merging. However, when changes are merged or committed directly to the specified branch, Terraform Cloud initiates a standard plan and apply workflow, not a speculative plan [vortegon] Selected Answer: B pull requests start speculative plans, this occurs before a commit or merge. https://developer.hashicorp.com/terraform/cloud-docs/run/remote-operations#speculative-plans [FarziWaliMarzi] Selected Answer: A https://developer.hashicorp.com/terraform/cloud-docs/run/ui#automatically-starting-runs [princajen] Selected Answer: A It is true because Terraform Cloud can monitor the linked version control repository for changes and automatically trigger a speculative plan run in response to each commit or merge. This allows users to quickly see the expected changes that would result from the proposed change, without actually applying those changes. Speculative plan runs can be a useful tool for catching errors early in the development process and avoiding potentially costly mistakes. [InformationOverload] Selected Answer: A Whether to perform speculative plans on pull requests to the connected repository, to assist in reviewing proposed changes. Automatic speculative plans are enabled by default, but you can disable them for any workspace. https://developer.hashicorp.com/terraform/cloud-docs/workspaces/settings/vcs
----------------------------------------

## Examtopics Terraform Associate_22 question #7

You have some Terraform code and a variable definitions file named dev.auto.tfvars that you tested successfully in the dev environment. You want to deploy the same code in the staging environment with a separate variable definition file and a separate state file.

Which two actions should you perform? (Choose two.)

**A:** Copy the existing terraform.tfstate file and save it as staging.terraform.tfstate

**B:** Write a new staging.auto.tfvars variable definition file and run Terraform with the var-file=”staging.auto.tfvars” flag

**C:** Create a new Terraform workspace for staging

**D:** Create a new Terraform provider for staging

**E:** Add new Terraform code (*.tf files) for staging in the same directory



**Answer: BC**

**Timestamp: 2023-01-13 19:09:00**

[View on ExamTopics](https://www.examtopics.com/discussions/hashicorp/view/95074-exam-terraform-associate-topic-1-question-197-discussion/)

Comments: [7b5b962] B. Terraform core Terraform core is responsible for reading the configuration, generating the execution plan, and applying the changes by interacting with the providers. [starksolutions] merci . [akm_1010] Selected Answer: BC with a separate variable definition file :- Write a new staging.auto.tfvars variable definition file and run Terraform with the var-file=”staging.auto.tfvars” flag Want to deploy the same code in the staging environment with a separate state file :- Create a new Terraform workspace for staging. Workspaces isolate Terraform state. [Ni33] Selected Answer: BC B and C are correct answers. same tfstate file can be used in multiple workspaces to provision infrastructure and each workspace has its own tfvar file matching workspace prefix. [camps] Selected Answer: BC B. Write a new staging.auto.tfvars variable definition file and run Terraform with the var-file="staging.auto.tfvars" flag C. Create a new Terraform workspace for staging [ozbeyucel] Selected Answer: BC ...... [nakikoo] Correct, workspace to use same .tf configuration with a different environment such as dev, prod, test, write new stage then refer the existing .tf config
----------------------------------------

## Examtopics Terraform Associate_22 question #8

The ________ determines how Terraform creates, updates, or deletes resources.

**A:** Terraform configuration

**B:** Terraform core

**C:** Terraform provider

**D:** Terraform provisioner



**Answer: C**

**Timestamp: 2023-01-13 19:11:00**

[View on ExamTopics](https://www.examtopics.com/discussions/hashicorp/view/95075-exam-terraform-associate-topic-1-question-198-discussion/)

Comments: [Manguu] Selected Answer: C "What" = config "How" = provider [gekkehenk] Selected Answer: C The question specifically states "how". The provider is the only component of Terraform that know HOW to create, update, delete a resource, as it knows all the specifics. [7b5b962] B. Terraform core Terraform core is responsible for reading the configuration, generating the execution plan, and applying the changes by interacting with the providers. [Stanislav4907] Selected Answer: C The Terraform provider determines how Terraform creates, updates, or deletes resources. Providers are responsible for translating Terraform configurations into API requests that manipulate resources in the target environment. Each provider implements the necessary operations for a specific type of infrastructure, such as AWS, Azure, or Google Cloud Platform. When Terraform applies a configuration, it reads the provider information from the configuration and uses it to interact with the target environment. The provider then manages the lifecycle of the resources by creating, updating, or deleting them as needed. Note that while the Terraform configuration defines the desired state of the resources, and the Terraform core is responsible for managing the planning and execution of changes, it is ultimately the provider that determines how those changes are implemented in the target environment. [camps] Selected Answer: C C. Terraform provider [Atila50] Selected Answer: A https://developer.hashicorp.com/terraform/language/resources/behavior [rotimislaw] Selected Answer: C as gekkehenk wrote, it's C [princajen] Selected Answer: C The Terraform provider determines how Terraform interacts with a specific API or service provider to create, update, or delete resources. The provider translates Terraform configuration files into API requests, and then interacts with the API to manage resources on the service provider. [crickmeister] C. Terraform provider determines how Terraform creates, updates, or deletes resources. A provider is responsible for understanding API interactions and exposing resources. Providers can represent physical resources like compute instances, or abstract resources like DNS records. A provider is responsible for translating the Terraform configuration into API calls to the underlying service, and for handling the response from the service. The Terraform configuration specifies which provider to use for each resource block. The provider block itself specifies the configuration necessary to connect to the API of a particular service, such as credentials or endpoint information. [agmesas] Selected Answer: C C, provider = how, .tf = what [Abuu] Selected Answer: A The Terraform configuration is the main input for Terraform, defining the desired state of the resources in the infrastructure. It is the definition of how Terraform should create, update, or delete resources in order to reach the desired state. [dkd123] Terraform config determines what , Provider determines how. Answer should be provider. [ozbeyucel] Selected Answer: A correct is A [Abuu] Selected Answer: A State file should be included; because The State File determines how Terraform creates, updates, or deletes resources. The state file is a JSON file that is used to persistently store all the resources created by Terraform. It stores the state of the resources, as well as their properties, so that Terraform knows what actions to take on the next run. [Abuu] Applying a Terraform configuration is the process of creating, updating, and destroying real infrastructure objects in order to make their settings match the configuration. https://developer.hashicorp.com/terraform/language/resources/behavior [Agil09] Selected Answer: A correct is A [Zeppoonstream] Selected Answer: A A. Terraform configuration The Terraform configuration determines how Terraform creates, updates, or deletes resources. It is written in HashiCorp Configuration Language (HCL) and it includes the resources that will be managed by Terraform, their properties, and the dependencies between them. The configuration is read by the Terraform core and used to generate an execution plan that is then passed to the Terraform provider to make the necessary changes to the infrastructure. [resnef] Selected Answer: A terraform config file [nakikoo] correct .tf configuration file determine whether to take action, delete/apply/ etc
----------------------------------------

## Examtopics Terraform Associate_56 question #2

It is _________ to change the Terraform backend from the default “local” backend to a different one after performing your first terraform apply.

**A:** mandatory

**B:** optional

**C:** impossible

**D:** discouraged



**Answer: B**

**Timestamp: 2024-11-20 23:23:00**

[View on ExamTopics](https://www.examtopics.com/discussions/hashicorp/view/151731-exam-terraform-associate-topic-1-question-355-discussion/)

Comments: [AStark1080] This should be B [siheom] Selected Answer: B vote B
----------------------------------------

## Examtopics Terraform Associate_56 question #4

A child module can always access variables declared in its parent module.

**A:** True

**B:** False



**Answer: B**

**Timestamp: 2024-11-19 04:29:00**

[View on ExamTopics](https://www.examtopics.com/discussions/hashicorp/view/151601-exam-terraform-associate-topic-1-question-356-discussion/)

Comments: [CloudJordao] Selected Answer: B The correct answer is: B. False. A child module cannot automatically access variables declared in its parent module. You need to explicitly pass the variables from the parent module to the child module. [ayrtonjohn] Selected Answer: B false false [sankalp122] B. False The child module would not have access to the variables of the parent module.
----------------------------------------

## Examtopics Terraform Associate_56 question #6

What value does the Terraform Cloud/Terraform Enterprise private module registry provide over the public Terraform Module Registry?

**A:** The ability to share modules with public Terraform users and members of Terraform Enterprise Organizations

**B:** The ability to tag modules by version or release

**C:** The ability to restrict modules to members of Terraform Cloud or Enterprise organizations

**D:** The ability to share modules publicly with any user of Terraform



**Answer: C**

**Timestamp: 2022-04-24 15:04:00**

[View on ExamTopics](https://www.examtopics.com/discussions/hashicorp/view/74324-exam-terraform-associate-topic-1-question-36-discussion/)

Comments: [vitasac] Selected Answer: C for sure C [tipzzz] Selected Answer: C Terraform Cloud's private registry works similarly to the public Terraform Registry and helps you share Terraform providers and Terraform modules across your organization. It includes support for versioning and a searchable list of available providers and modules. [anand0310] Selected Answer: C Private registry is meant for restricting access to just the organization's teams [hoangphan] Selected Answer: C of course C [samimshaikh] Selected Answer: C the question has the word private registry "over" the public C. The ability to restrict modules to members of Terraform Cloud or Enterprise organizations The Terraform Cloud/Terraform Enterprise private module registry provides the ability to restrict modules to members of specific Terraform Cloud or Enterprise organizations. This allows organizations to control access to and usage of modules, keeping them private within the organization. Option C correctly describes this capability. [Yhorm] sometime I wonder whether whomever picked the 'correct' answers just picked an alternative at random [Bere] Selected Answer: C The private module registry in Terraform Cloud and Terraform Enterprise is a way to distribute Terraform modules within your organization. The public Terraform Module Registry, on the other hand, is open to everyone. Here is an example of how you might use a module from a private module registry: module "vpc" { source = "app.terraform.io/example_corp/vpc/aws" version = "1.0.0" // ...other arguments... } Here is an example of how you might use a module from the public Terraform Module Registry: module "vpc" { source = "terraform-aws-modules/vpc/aws" version = "2.77.0" // ...other arguments... } [Shane_C] Selected Answer: C Come on guys, it's C [Ni33] Selected Answer: C C is the correct answer [Faaizz] Selected Answer: C Only C makes sense here [camps] Selected Answer: C C. The ability to restrict modules to members of Terraform Cloud or Enterprise organizations. The private module registry in Terraform Cloud/Terraform Enterprise provides an additional level of control and security over the public Terraform Module Registry. Unlike the public registry, the private registry allows organizations to restrict module access to only members of their Terraform Cloud or Enterprise organization. This ensures that sensitive infrastructure code is not accidentally or intentionally shared with unauthorized users. [camps] Selected Answer: C C. The ability to restrict modules to members of Terraform Cloud or Enterprise organizations. The Terraform Module Registry is a public repository of Terraform modules that can be used by anyone using Terraform. The Terraform Cloud/Terraform Enterprise private module registry provides additional functionality for organizations that want to create and manage their own private modules. The private module registry provides several benefits over the public Terraform Module Registry, including: The ability to restrict modules to members of Terraform Cloud or Enterprise organizations: This allows organizations to control who has access to their private modules and prevent unauthorized access. The ability to tag modules by version or release: This makes it easy to manage and track changes to modules over time. The ability to manage module dependencies: This allows organizations to manage and version the dependencies of their private modules. Integration with Terraform Cloud or Enterprise workspaces: This allows organizations to seamlessly use their private modules in their Terraform Cloud or Enterprise workspaces. [Power123] Answer is C [alexsandroe] Selected Answer: C C is correct [Bere] Selected Answer: C https://developer.hashicorp.com/terraform/cloud-docs/registry Private Registry Terraform Cloud's private registry works similarly to the public Terraform Registry and helps you share Terraform providers and Terraform modules across your organization. It includes support for versioning and a searchable list of available providers and modules. https://developer.hashicorp.com/terraform/cloud-docs/registry#private-providers-and-modules Private Providers and Modules Private providers and private modules are hosted on an organization's private registry and are only available to members of that organization. In Terraform Enterprise, private modules are also available to other organizations that are configured to share modules with that organization. [mendelthegreat] C is the correct answer DUH [legendary7] C - is the correct answer. D- is simply the advantage of Public registry over Private registry. It is the opposite of what the question asks [yuvifose] Selected Answer: C The answer should be C [Eltooth] Selected Answer: C C is correct answer. [fabiomlop] Selected Answer: C It's a private registry, therefore you can make it private LOL [Parthasarathi] Selected Answer: C It should be C [temp111] Answer is C
----------------------------------------

## Examtopics Terraform Associate_56 question #8

Which task does terraform init not perform?

**A:** Sources all providers present in the configuration and ensures they are downloaded and available locally

**B:** Connects to the backend

**C:** Sources any modules and copies the configuration locally

**D:** Validates all required variables are present



**Answer: D**

**Timestamp: 2022-05-29 09:56:00**

[View on ExamTopics](https://www.examtopics.com/discussions/hashicorp/view/76384-exam-terraform-associate-topic-1-question-37-discussion/)

Comments: [elvancedonzy] Selected Answer: D D is correct [SilentH] Selected Answer: D Finally ExamTopics got 1 right! [anand0310] Selected Answer: D D is correct, validation is not performed by init command [DarrylNg] Selected Answer: D D is correct. You can test it out in a sample tf file. Init command goes through even if some variable that another resource is referencing is missing. [Bere] Selected Answer: D terraform init performs several initialization steps to prepare your Terraform working directory to be used with Terraform commands. However, it does not validate whether all required variables are present in the configuration or provided through another method. That validation happens during the terraform plan or terraform apply stage. terraform init does: 1. Download and installs the necessary provider plugins. 2. Setup backend for storing state. 3. Download and install modules [Ni33] I think A is the correct answer. [Ni33] Selected Answer: A A is the correct answer. [camps] Selected Answer: D D. Validates all required variables are present. terraform init is a command that initializes a new or existing Terraform configuration. When you run terraform init, Terraform performs several tasks to set up the configuration for use, including: Sources all providers present in the configuration and ensures they are downloaded and available locally Connects to the backend, if one is configured, and performs any necessary setup steps Sources any modules referenced in the configuration and copies their contents locally Initializes the backend configuration and performs any necessary setup steps [Power123] Ans is C. init doesn't validate all variables are present [bwahdi] why isn't it A? [Burakko] Selected Answer: D terraform plan or apply does "validates all required variables are present" [flaviu888] yes, should be D [Eltooth] Selected Answer: D D is correct answer. [Ahmad_Terraform] yes INIT does not validate variables [habros] Looks like C to me
----------------------------------------

## Examtopics Terraform Associate_56 question #9

You have declared a variable called var.list which is a list of objects that all have an attribute id.
Which options will produce a list of the IDs? (Choose two.)

**A:** { for o in var.list : o => o.id }

**B:** var.list[*].id

**C:** [ var.list[*].id ]

**D:** [ for o in var.list : o.id ]



**Answer: BD**

**Timestamp: 2022-05-02 20:47:00**

[View on ExamTopics](https://www.examtopics.com/discussions/hashicorp/view/75092-exam-terraform-associate-topic-1-question-38-discussion/)

Comments: [bigboi23] Selected Answer: BD https://www.terraform.io/language/expressions/splat A splat expression provides a more concise way to express a common operation that could otherwise be performed with a for expression. [Bere] Selected Answer: BD Here's an example: Assume you have the following variable declaration: variable "users" { default = [ { id = "id1" name = "name1" }, { id = "id2" name = "name2" }, { id = "id3" name = "name3" } ] } You can retrieve the list of IDs in your Terraform configuration using either of these options: output "users_splat" { value = var.users[*].id } output "users_for" { value = [for user in var.users : user.id] } Both these outputs will produce the same list of IDs: ["id1", "id2", "id3"]. [anand0310] Selected Answer: BD BD for sure [vibzr2023] Apart from B and D , C is also correct > [for o in var.list : o.id] [ "1", "2", "3", ] [zimomar] Selected Answer: BD BD for sure [ndiichie] Answer is BD. https://developer.hashicorp.com/terraform/language/expressions/splat [srajvanshi] https://developer.hashicorp.com/terraform/language/expressions/splat B and D [krishna2802] Selected Answer: BD https://www.terraform.io/language/expressions/splat [Ni33] Selected Answer: AB A and B is the correct answer [AzRNoob] he correct options that will produce a list of the IDs are B and D: Option B, var.list[*].id, uses the splat operator [*] to iterate over all elements of the var.list list and then accesses the id attribute of each object. The result is a list of all the id values. Option D, [ for o in var.list : o.id ], uses a list comprehension to iterate over each object in the var.list list and create a new list that contains only the id attribute of each object. [camps] Selected Answer: BD B. var.list[*].id and D. [ for o in var.list : o.id ]. To produce a list of IDs from a list of objects with an id attribute, you can use either of the following options: var.list[*].id: This uses the [*] wildcard to select all elements of the var.list list, and the .id syntax to select the id attribute of each element. This will produce a list of IDs. [ for o in var.list : o.id ]: This uses a for expression to iterate over each element of var.list, selecting the id attribute of each element. This will produce a list of IDs. [Power123] The splat and interpolation. Ans is B & D [thor7] Selected Answer: BD B and D are correct, checked them. Reference: https://developer.hashicorp.com/terraform/language/expressions/for [Mal_8] Selected Answer: BD BD. Tried each expression [sahara99] Selected Answer: BD A is wrong as the question asked which one creates a "list" [Tanacet] Selected Answer: BD The splat and interpolation-style [Mohammed52] Selected Answer: BD B and D is corrrect [InformationOverload] Selected Answer: BD B and D is correct [niccsm] Definitely D not A https://developer.hashicorp.com/terraform/language/expressions/for [asudhin] Selected Answer: BD It is B&D [nick7513] Selected Answer: BD B&D are correct both [for o in var.list : o.id] This is equivalent to the following splat expression: var.list[*].id [najslejdi] Selected Answer: BD B & D are correct [yuvifose] Selected Answer: BD B and D. {} are not lists but dicts/maps/objects [Eltooth] Selected Answer: BD B and D are correct answers. https://www.terraform.io/language/expressions/splat [BlackZeros] Selected Answer: BD b and d seems correct [Zam88] Selected Answer: BD BD correct [fsdgrtsdfcjmu] I choose BD [petliura] B, D - straight from the documentation: https://www.terraform.io/language/expressions/splat [ItaloVinodi] Selected Answer: BD I'm wrong sorry according to documentation https://www.terraform.io/language/expressions/for BD is the right [ItaloVinodi] Selected Answer: AB I think AB is correct also looking at brackets [Parthasarathi] Selected Answer: AB AB is correct [rajje] https://www.terraform.io/language/expressions/splat [dumbu] AB is correct as D is already list and it has for loop inside a list, which is not required [vitasac] Selected Answer: BD BD for sure [koneba1309] Selected Answer: BD B is splat, and D is for in expression
----------------------------------------

## Examtopics Terraform Associate_2 question #10

Which of the following arguments are required when declaring a Terraform output?

**A:** sensitive

**B:** description

**C:** default

**D:** value



**Answer: D**

**Timestamp: 2022-09-01 19:59:00**

[View on ExamTopics](https://www.examtopics.com/discussions/hashicorp/view/79120-exam-terraform-associate-topic-1-question-103-discussion/)

Comments: [Nunyabiznes] Selected Answer: D The only required argument when declaring a Terraform output is the value argument, which specifies the value of the output: ``` output "example" { value = "example output value" } ``` The description argument is optional and can be used to provide additional information about the output: ``` output "example" { value = "example output value" description = "An example output" } ``` [Ni33] Selected Answer: D DDDDDDDDD [Power123] D is correct [nakikoo] Selected Answer: D https://developer.hashicorp.com/terraform/language/values/outputs [Gaby999] yes, correct answer is D [Burakko] Selected Answer: D There has to be a value for sure.
----------------------------------------

## Examtopics Terraform Associate_2 question #11

Your risk management organization requires that new AWS S3 buckets must be private and encrypted at rest. How can Terraform Enterprise automatically and proactively enforce this security control?

**A:** With a Sentinel policy, which runs before every apply

**B:** By adding variables to each TFE workspace to ensure these settings are always enabled

**C:** With an S3 module with proper settings for buckets

**D:** Auditing cloud storage buckets with a vulnerability scanning tool



**Answer: A**

**Timestamp: 2022-09-01 09:43:00**

[View on ExamTopics](https://www.examtopics.com/discussions/hashicorp/view/78962-exam-terraform-associate-topic-1-question-104-discussion/)

Comments: [camps] Selected Answer: A A. With a Sentinel policy, which runs before every apply. Terraform Enterprise can enforce security controls through the use of Sentinel policies. Sentinel is a policy as code framework that integrates with Terraform Enterprise and can be used to enforce specific security controls. In this case, the Sentinel policy could check that all new S3 buckets are set to be private and encrypted at rest and prevent the Terraform apply from proceeding if the buckets do not meet this requirement. This ensures that the security control is automatically and proactively enforced every time Terraform makes changes to the infrastructure. [selvaraj133ece] Answer, B only. They want to keep the S3 bucket private. So, it will be a different state file. [Rohit000003] Selected Answer: A As per terraform document [Ni33] Selected Answer: A AAAAAAAAAAA [Power123] A is correct [Nunyabiznes] Selected Answer: A import "tfplan" # Ensure all new S3 buckets are private and encrypted at rest deny[msg] { resources := tfplan.module_paths["aws_s3_bucket"] not all_true([ for r in resources: r.attributes.acl == "private" and r.attributes.server_side_encryption_configuration.0.rule.0.apply_server_side_encryption_by_default.0.sse_algorithm == "AES256" ]) msg := "All new S3 buckets must be private and encrypted at rest" } [SilentMilli] Selected Answer: A Terraform Enterprise provides the ability to enforce security controls through Sentinel policies, which are a form of policy as code. Sentinel policies allow you to define and enforce organizational or regulatory policies by creating a set of rules that run before each Terraform operation. [Ame2222] A is correct [Daro_] Selected Answer: A yes A Corrct [seif1993] yes A Corrct [RVivek] Selected Answer: A Sentinel policy is the best way to manage multiple workspaces [bora4motion] Selected Answer: A I go with A. [Burakko] Selected Answer: A With a Sentinel policy for sure. [mav3r1ck] A. Reference: https://docs.hashicorp.com/sentinel/intro/what https://medium.com/hashicorp-engineering/enforcing-aws-s3-security-best-practice-using-terraform-sentinel-ddcd181ff4b7
----------------------------------------

## Examtopics Terraform Associate_2 question #12

Most Terraform providers interact with ____________.

**A:** API

**B:** VCS Systems

**C:** Shell scripts

**D:** None of the above



**Answer: A**

**Timestamp: 2022-09-02 18:39:00**

[View on ExamTopics](https://www.examtopics.com/discussions/hashicorp/view/79483-exam-terraform-associate-topic-1-question-105-discussion/)

Comments: [Hizumi] Answer is A. Terraform relies on plugins called "providers" to interact with cloud providers, SaaS providers, and other APIs, as per: https://www.terraform.io/language/providers [Boomboy_420] Selected Answer: A A is the right answer [debabrata6983] Selected Answer: A Provider plugin abstracts the API interaction with the cloud provider. [SairamObili] it s API Answer is A [IK912] A is the answer [Power123] A is correct [seif1993] Selected Answer: A yes for A [donathon] Selected Answer: A A is the answer
----------------------------------------

## Examtopics Terraform Associate_2 question #13

terraform validate validates that your infrastructure matches the Terraform state file.

**A:** True

**B:** False



**Answer: B**

**Timestamp: 2022-09-01 11:55:00**

[View on ExamTopics](https://www.examtopics.com/discussions/hashicorp/view/79014-exam-terraform-associate-topic-1-question-106-discussion/)

Comments: [RVivek] Selected Answer: B Validate only checks the syntax http://man.hubwiz.com/docset/Terraform.docset/Contents/Resources/Documents/docs/commands/validate.html [babgad] Selected Answer: B False B Validate runs checks that verify whether a configuration is syntactically valid and internally consistent, regardless of any provided variables or existing state. It is thus primarily useful for general verification of reusable modules, including correctness of attribute names and value types. It is safe to run this command automatically, for example as a post-save check in a text editor or as a test step for a re-usable module in a CI system https://developer.hashicorp.com/terraform/cli/v1.1.x/commands/validate [Busi57] Selected Answer: B false B Validate only checks the syntax [Busi57] False B [Ni33] Selected Answer: B B is the correct answer. Terraform plan validates desired state with current state configuration. [Power123] False , B is correct [adouban] Selected Answer: B B is correct [0ptimus] Selected Answer: B B because Terraform validate only checks for syntax error or so [bora4motion] Selected Answer: B It's more of a syntax thing. [Burakko] Selected Answer: B False, terraform validate has nothing to do with the state file. [Uma10] Selected Answer: B The terraform validate command validates the configuration files in a directory, referring only to the configuration and not accessing any remote services such as remote state, provider APIs, etc. Validate runs checks that verify whether a configuration is syntactically valid and internally consistent, regardless of any provided variables or existing state. It is thus primarily useful for general verification of reusable modules, including correctness of attribute names and value types. Source: https://www.terraform.io/cli/commands/validate
----------------------------------------

## Examtopics Terraform Associate_2 question #14

What does terraform import allow you to do?

**A:** Import a new Terraform module

**B:** Use a state file to import infrastructure to the cloud

**C:** Import provisioned infrastructure to your state file

**D:** Import an existing state file to a new Terraform workspace



**Answer: C**

**Timestamp: 2022-09-01 20:04:00**

[View on ExamTopics](https://www.examtopics.com/discussions/hashicorp/view/79122-exam-terraform-associate-topic-1-question-107-discussion/)

Comments: [Ni33] Selected Answer: C Yes, C is the correct answer. [Power123] C is correct [bora4motion] Selected Answer: C I go with C [Burakko] Selected Answer: C %100 true
----------------------------------------

