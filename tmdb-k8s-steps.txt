# Pre-requistes
AWS subscription

## Preperation Instructions

This implementaion is for 1 Master and 1 Worker (if reuqired more that 1 worker, please change variable "worker_instance_count" in variables.tf file to the required number of workers)  
### Create EC2 instance

### Create IAM user
    Create new user 
    Attach policy (Administrator access) 
    Once user is created --> Create Access key --> CLI
### login to your EC2 instance 
### Configure AWS CLI
    
    sudo su
    aws configure 
    provide the Access Key (from the the created user Access key)
    provide the secrect key (from the the created user Access key)
   
### Install Git
    
    yum install git -y
    
### Clone the Terrform repository
    https://github.com/Abd2024May/Terraform.git
### Install Ansible
    
    pip3 install ansible
    
### Update ansible path
   
    echo "export PATH=$PATH:/usr/local/bin/" >> ~/.bashrc
    source ~/.bashrc
   
### Install Terraform
   
    sudo yum install -y yum-utils
    sudo yum-config-manager --add-repo https://rpm.releases.hashicorp.com/AmazonLinux/hashicorp.repo
    sudo yum -y install terraform
   
## Deployment environment Instructions
### Change the directory to cloned git repository
### chmod 400 k8s
### run terraform init
### run terraform apply -auto-approve 

## Deployment application Instructions

Once deployment is finished we will get the Master and Workers puplic IPs
login to the Master node using the private key (k8s) which is avaialable in the repository
   
    ssh -i k8s ubuntu@MasterIP
    sudo su
    kubectl apply -f deployment-service.yaml
    
## Verify the deployment
    kubectl get pods
    http://NodeIP:32000


## Clean the environment
### run terraform destroy -auto-approve 
