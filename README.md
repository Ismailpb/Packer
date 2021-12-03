# packer-ami-template

It is just a simple project to create an AMI that is pre-configured to host a simple HTML website
Description

HashiCorp Packer is a lightweight, open source tool for building automating machine images across multiple platforms, including AWS, Azure, and GCP. Here, we will be be building a custom AMI using Packer.
Requirements

    IAM user with administrator access to EC2.
    Packer
    Linux Operating system

Installation

    To install packer, run the following commands to download the package

$ wget https://releases.hashicorp.com/packer/1.7.8/packer_1.7.8_linux_amd64.zip
$ unzip packer_1.7.8_linux_amd64.zip
$ mv packer /usr/bin/

    After installing Packer, verify the installation is working by checking that the packer is available:

$ packer

    To check software version run:

$ packer --version

Usage

    The environment vaiables has to be set in the vaiables section of the main build file : AWS_ACCESS_KEY_ID, AWS_SECRET_ACCESS_KEY

    cd into the packer folder with the files from the cloned repository.

    Run the following commands :

packer init main.pkr.hcl
packer validate main.pkr.hcl
packer build main.pkr.hcl

This will provision the AMI in you AWS account.
Results

An AMI has been created using packer. Now, you can use the AMI to launch an EC2 instance which will have the HTML web application pre configured and ready to use.

