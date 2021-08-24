# GBM-AWS-ELB-Cloudformation 
Creation of an elastic load balancer using AWS Cloudformation. Two EC2 instances are configured inside the loadbalancer, which display a sample app.

# Pre-requisites
- **AWS Account**: If you don't have an account set up, you can click the following [link] (https://www.google.com/aclk?sa=L&ai=DChcSEwiGgPC8p8jyAhUIKIYKHVqYD_4YABABGgJ2dQ&ae=2&sig=AOD64_1iTlBXbvjnjNFp_r9eqOe9SXhZvg&q&adurl&ved=2ahUKEwj97-m8p8jyAhXrQzABHePbAP8Q0Qx6BAgDEAE)
- **AWS Credentials**: You need an *aws access key* and a *aws secret key* in order to communicate with AWS. Click the following [link] (https://docs.aws.amazon.com/powershell/latest/userguide/pstools-appendix-sign-up.html) for more information.
- **AWS CLI**: You should have aws-cli setup in your system in order to replicate the following repository. More info [here] (https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html)
- **Ansible (Optional)**: More info on installation [here] (https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html) 
- **Ansible Tower (Optional)**: More info on installation [here] (https://docs.ansible.com/ansible-tower/latest/html/quickinstall/index.html) 
- **SSH Key Pair**: You can create the key pair using Ansible and launching the create\_keypair\_playbook.yml
# Options for Deployment
This repository includes the necessary files to deploy the Cloudformation stack in a few ways.

## Option 1: Cloudformation Exclusively
The user can use the template file **vpc.yml** file alongside with **parameters.json** to deploy the Cloudformation stack via the CLI. Note that you can update the **parameters.json** file to the values/names which you prefer.
```
aws cloudformation create-stack \
    --stack-name initial config \ 
    --template-body file://vpc.yml \
    --parameters file://parameters.json \
    --capabilities CAPABILITY_IAM \
    --region us-east-1
```

## Option 2: Cloudformation and Ansible through CLI
First, make sure to include/modify your variables in the vars.yml file. Afterwards you cant deploy the Cloudformation template using the **deploy\_vpc\_playbook.yml**. 

## Option 3: Cloudformation and Ansible through Ansible Tower
Add a survey to your job template to include all the variables in the vars.yml file. Afterwards you can use the **tower\_deploy\_vpc\_playbook.yml** to deploy the Cloudformation template.

# Credits
This repository is based on and was referenced from https://github.com/gglm92/aws-ansible-elb
