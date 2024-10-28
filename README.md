# Terraform_VPC-Creation

Terraform is an IAAS code service used for infrastructure creation.
It uses Hasicorp configuration language to automate tasks

**Advantages of terraform** :  1.time saving 2.reproduction of infra  3.migration is easy  4.tracking and version control

Difference between ansible and terraform : 
Terraform used to create new IAAS in cloud.  Ansible used in both existing and create new IAAS in both cloud and onpremises.

**Description :**
In this project we are going to create a vpc,subnet and resources using terraform code. We have to use aws linux server to execute terraform code.

Step 1:  **Create AWS Ec2 linux server** 
Go to aws ec2 -> click launch ec2->select ami as amazon linux2 ami ->select instance type as t2.micro->allow port 22 ->create new keypair to connect ec2->leave remaining by default and click launch.

Step 2 : **Create role for ec2 to access vpc and another ec2**
Go to aws console->click iam -> click create role -> select ec2-> attach full vpc access,ec2 access permissions-> click create.

Step 3 : **Attach the role to your ec2 linux server**
Go to aws console->select ec2->click instances->click your ec2 server->click attach role->select above created role->click save.

Step 4 : **Login EC2 and download terraform in ec2**
Login ec2 using putty and type below commands
wget <download link for terrafrom in linux>
ls -lrt
apt install unzip
unzip <name of terraform zip file>
ls -lrt
mv terraform /usr/local/bin
terraform version

Step 5 : **Execute terraform code in linux server**

vi myterraformcode.tf   (create a new terraform file)
<copy the attached terraform code and paste>
terraform init    (to iitialize terraform)
terraform plan    (to check what are created after executing code)
terraform apply   (to execute terraform code)

Now go to your aws console and you can see resources are created.

**Note :**
After executing terraform code terraform.tfstate file is automatically create inside the current directory.It contains full details of resources in our terraform code. When you modify something on your code and apply it on cloud, terraform will look into the state file, and compare the changes made in the code from that state file and the changes to the infrastructure based on the state file.

Terraform is immutable. If you edit your code and reapply means it will not edit existing terraform.tfstate file. It will create new file and delete existing code file.  To avoid this we can manually change in aws console and use terraform refresh and terraform import commands to update terraform.tfstate file.

The terraform destroy command is used to terminate all resources managed by a specific Terraform configuration.
