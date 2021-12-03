# Packer-ami-template
2
​
3
It is just a simple project to create an AMI that is pre-configured to host a simple HTML website
4
Description
5
​
6
HashiCorp Packer is a lightweight, open source tool for building automating machine images across multiple platforms, including AWS, Azure, and GCP. Here, we will be be building a custom AMI using Packer.
7
Requirements
8
​
9
    IAM user with administrator access to EC2.
10
    Packer
11
    Linux Operating system
12
​
13
# Installation
14
​
15
    To install packer, run the following commands to download the package
16
    
17
$ wget https://releases.hashicorp.com/packer/1.7.8/packer_1.7.8_linux_amd64.zip
18
$ unzip packer_1.7.8_linux_amd64.zip
19
$ mv packer /usr/bin/
20
​
21
​
22
    After installing Packer, verify the installation is working by checking that the packer is available:
23
​
24
$ packer
25
​
26
    To check software version run:
27
​
28
$ packer --version
29
​
30
# Usage
31
​
32
    The environment vaiables has to be set in the vaiables section of the main build file : AWS_ACCESS_KEY_ID, AWS_SECRET_ACCESS_KEY
33
​
34
    cd into the packer folder with the files from the cloned repository.
35
​
36
    Run the following commands :
37
​
38
packer init main.pkr.hcl
39
packer validate main.pkr.hcl
40
packer build main.pkr.hcl
41
​
42
This will provision the AMI in you AWS account.
43
Results
44
​
45
An AMI has been created using packer. Now, you can use the AMI to launch an EC2 instance which will have the HTML web application pre configured and ready to use.
46
​
47
