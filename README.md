# terraformrer

AIM ----> Used to import all the existing resources from any cloud (aws,azure...) to local in  few seconds.

we required 2 tools
1. Terraform
2. Terraformer



WHAT IS TERRAFORMER:

• Its a free and open-source tool.

• it is used for infrastructure management.

• It allows you to import existing infrastructure from a cloud

• it can generate any resource code in less than a second.

• Its written on Go Language.



STEP 1----->  CREATING EC2 INSTANCE AND INSTALL TERRAFORM IN THAT SERVER

sudo yum install -y yum-utils shadow-utils
sudo yum-config-manager --add-repo https://rpm.releases.hashicorp.com/AmazonLinux/hashicorp.repo
sudo yum -y install terraform
aws configure

Note --> configure with aws  first with your creaditials


STEP 2----->  INSTALL TERRAFORMER IN THE SERVER

wget https://github.com/GoogleCloudPlatform/terraformer/releases/download/0.8.24/terraformer-all-linux-amd64
chmod +x terraformer-all-linux-amd64
sudo mv terraformer-all-linux-amd64 /usr/local/bin/terraformer
terraformer --version 

STEP 3---> UPDATE THE PROVIDERS FOR THE TERRAFORM

provider "aws" {
  region = "us-east-1"
}

vim main.tf>>> upload above mentioned provider details >> terraform init

STEP 4----> IMPORT THE EXISTING RESOURCES

COMMAND----> 1.terraformer import aws --resources=sg,ec2_instance,elb --regions=us-east-1 
             2.cd generated
             3.cd ec2
             4.cd statelist

 NOTE-----> resources need to be present in representd region ,otherwise not working.
            for u need to create loadbancer,ec2_instances,sg in the mentioned region.

 

 
           
       
