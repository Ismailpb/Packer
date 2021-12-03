# How to create an AMI(Amzon Machine Image) using Packer
Actually Packer is a open source tool for creating identical machine images for supporting multiple platforms.

# Requirements

1.Need to install Packer.

2.IAM user with administrator access (For EC2).

3.We need to choose an existing AMI on Amazon to use as your base image.

# Installation Process

1.At first we need to install Packer in our local machine.
Since my local machine is running with Linux OS, so I choose the Linux Package from https://www.packer.io/downloads

$ wget https://releases.hashicorp.com/packer/1.7.8/packer_1.7.8_linux_amd64.zip

$ unzip packer_1.7.8_linux_amd64.zip

$ mv packer /usr/bin

2.Once the packer installation completed, You can verify whether the packer is installed in your local machine or not by using the below command

 $ packer --version
 
 +++++++++
 
 packer --version
1.7.8

 +++++++++
 
 #  How to Use
- The environment variables has to be set in the variables section of the main build file : AWS_ACCESS_KEY_ID, AWS_SECRET_ACCESS_KEY

- cd into Packer folder  from the cloned repository.
- Create a file name "main.pkr.hcl(you need to choose the file extension as pkr.hcl) and put the source codes.
- Once the codes were written, run the below commands


   $packer init main.pkr.hcl
   
   $packer validate main.pkr.hcl
   
   $packer build main.pkr.hcl

This creates a new EC2 instance based on source_ami, install softwares, stops the instance, creates an AMI based on the new instance, and then terminates the EC2 instance.

 # Result
 
 You can use the below command to validate the file.
 
  #packer validate main.pkr.hcl
 
The configuration is valid.

Once the file is validated, you can build the file using

 #packer build main.pkr.hcl

Sample results

linux-ami.amazon-ebs.Webserver-VM: output will be in this color.
    linux-ami.amazon-ebs.Webserver-VM:
    linux-ami.amazon-ebs.Webserver-VM: Dependencies Resolved
    linux-ami.amazon-ebs.Webserver-VM:
    linux-ami.amazon-ebs.Webserver-VM: ================================================================================
    linux-ami.amazon-ebs.Webserver-VM:  Package                Arch      Version                   Repository     Size
    linux-ami.amazon-ebs.Webserver-VM: ================================================================================
    linux-ami.amazon-ebs.Webserver-VM: Installing:
    linux-ami.amazon-ebs.Webserver-VM:  git                    x86_64    2.32.0-1.amzn2.0.1        amzn2-core    126 k
    linux-ami.amazon-ebs.Webserver-VM:  httpd                  x86_64    2.4.51-1.amzn2            amzn2-core    1.3 M
    linux-ami.amazon-ebs.Webserver-VM: Installing for dependencies:
    linux-ami.amazon-ebs.Webserver-VM:  apr                    x86_64    1.7.0-9.amzn2             amzn2-core    122 k
    linux-ami.amazon-ebs.Webserver-VM:  apr-util               x86_64    1.6.1-5.amzn2.0.2         amzn2-core     99 k
    linux-ami.amazon-ebs.Webserver-VM:  apr-util-bdb           x86_64    1.6.1-5.amzn2.0.2         amzn2-core     19 k
    linux-ami.amazon-ebs.Webserver-VM:  emacs-filesystem       noarch    1:27.2-4.amzn2.0.1        amzn2-core     67 k
    linux-ami.amazon-ebs.Webserver-VM:  generic-logos-httpd    noarch    18.0.0-4.amzn2            amzn2-core     19 k
    linux-ami.amazon-ebs.Webserver-VM:  git-core               x86_64    2.32.0-1.amzn2.0.1        amzn2-core    4.8 M
    linux-ami.amazon-ebs.Webserver-VM:  git-core-doc           noarch    2.32.0-1.amzn2.0.1        amzn2-core    2.7 M
    linux-ami.amazon-ebs.Webserver-VM:  httpd-filesystem       noarch    2.4.51-1.amzn2            amzn2-core     24 k
    linux-ami.amazon-ebs.Webserver-VM:  httpd-tools            x86_64    2.4.51-1.amzn2            amzn2-core     88 k
    linux-ami.amazon-ebs.Webserver-VM:  mailcap                noarch    2.1.41-2.amzn2            amzn2-core     31 k
    linux-ami.amazon-ebs.Webserver-VM:  mod_http2              x86_64    1.15.19-1.amzn2.0.1       amzn2-core    149 k
    linux-ami.amazon-ebs.Webserver-VM:  perl-Error             noarch    1:0.17020-2.amzn2         amzn2-core     32 k
    linux-ami.amazon-ebs.Webserver-VM:  perl-Git               noarch    2.32.0-1.amzn2.0.1        amzn2-core     43 k
    linux-ami.amazon-ebs.Webserver-VM:  perl-TermReadKey       x86_64    2.30-20.amzn2.0.2         amzn2-core     31 k
    linux-ami.amazon-ebs.Webserver-VM:
    linux-ami.amazon-ebs.Webserver-VM: Transaction Summary
    linux-ami.amazon-ebs.Webserver-VM: ================================================================================
    linux-ami.amazon-ebs.Webserver-VM: Install  2 Packages (+14 Dependent packages)
    linux-ami.amazon-ebs.Webserver-VM:
    linux-ami.amazon-ebs.Webserver-VM: Total download size: 9.6 M
    linux-ami.amazon-ebs.Webserver-VM: Installed size: 43 M
    linux-ami.amazon-ebs.Webserver-VM: Downloading packages:
    linux-ami.amazon-ebs.Webserver-VM: --------------------------------------------------------------------------------
    linux-ami.amazon-ebs.Webserver-VM: Total                                               27 MB/s | 9.6 MB  00:00
    linux-ami.amazon-ebs.Webserver-VM: Running transaction check
    linux-ami.amazon-ebs.Webserver-VM: Running transaction test
    linux-ami.amazon-ebs.Webserver-VM: Transaction test succeeded
    linux-ami.amazon-ebs.Webserver-VM: Running transaction
    linux-ami.amazon-ebs.Webserver-VM:   Installing : apr-1.7.0-9.amzn2.x86_64                                    1/16
    linux-ami.amazon-ebs.Webserver-VM:   Installing : apr-util-bdb-1.6.1-5.amzn2.0.2.x86_64                       2/16
    linux-ami.amazon-ebs.Webserver-VM:   Installing : apr-util-1.6.1-5.amzn2.0.2.x86_64                           3/16
    linux-ami.amazon-ebs.Webserver-VM:   Installing : git-core-2.32.0-1.amzn2.0.1.x86_64                          4/16
    linux-ami.amazon-ebs.Webserver-VM:   Installing : git-core-doc-2.32.0-1.amzn2.0.1.noarch                      5/16
    linux-ami.amazon-ebs.Webserver-VM:   Installing : httpd-tools-2.4.51-1.amzn2.x86_64                           6/16
    linux-ami.amazon-ebs.Webserver-VM:   Installing : generic-logos-httpd-18.0.0-4.amzn2.noarch                   7/16
    linux-ami.amazon-ebs.Webserver-VM:   Installing : mailcap-2.1.41-2.amzn2.noarch                               8/16
    linux-ami.amazon-ebs.Webserver-VM:   Installing : 1:perl-Error-0.17020-2.amzn2.noarch                         9/16
    linux-ami.amazon-ebs.Webserver-VM:   Installing : httpd-filesystem-2.4.51-1.amzn2.noarch                     10/16
    linux-ami.amazon-ebs.Webserver-VM:   Installing : mod_http2-1.15.19-1.amzn2.0.1.x86_64                       11/16
    linux-ami.amazon-ebs.Webserver-VM:   Installing : httpd-2.4.51-1.amzn2.x86_64                                12/16
    linux-ami.amazon-ebs.Webserver-VM:   Installing : 1:emacs-filesystem-27.2-4.amzn2.0.1.noarch                 13/16
    linux-ami.amazon-ebs.Webserver-VM:   Installing : perl-TermReadKey-2.30-20.amzn2.0.2.x86_64                  14/16
    linux-ami.amazon-ebs.Webserver-VM:   Installing : perl-Git-2.32.0-1.amzn2.0.1.noarch                         15/16
    linux-ami.amazon-ebs.Webserver-VM:   Installing : git-2.32.0-1.amzn2.0.1.x86_64                              16/16
    linux-ami.amazon-ebs.Webserver-VM:   Verifying  : apr-util-1.6.1-5.amzn2.0.2.x86_64                           1/16
    linux-ami.amazon-ebs.Webserver-VM:   Verifying  : perl-TermReadKey-2.30-20.amzn2.0.2.x86_64                   2/16
    linux-ami.amazon-ebs.Webserver-VM:   Verifying  : httpd-2.4.51-1.amzn2.x86_64                                 3/16
    linux-ami.amazon-ebs.Webserver-VM:   Verifying  : apr-util-bdb-1.6.1-5.amzn2.0.2.x86_64                       4/16
    linux-ami.amazon-ebs.Webserver-VM:   Verifying  : git-core-doc-2.32.0-1.amzn2.0.1.noarch                      5/16
    linux-ami.amazon-ebs.Webserver-VM:   Verifying  : perl-Git-2.32.0-1.amzn2.0.1.noarch                          6/16
    linux-ami.amazon-ebs.Webserver-VM:   Verifying  : 1:emacs-filesystem-27.2-4.amzn2.0.1.noarch                  7/16
    linux-ami.amazon-ebs.Webserver-VM:   Verifying  : httpd-filesystem-2.4.51-1.amzn2.noarch                      8/16
    linux-ami.amazon-ebs.Webserver-VM:   Verifying  : git-2.32.0-1.amzn2.0.1.x86_64                               9/16
    linux-ami.amazon-ebs.Webserver-VM:   Verifying  : git-core-2.32.0-1.amzn2.0.1.x86_64                         10/16
    linux-ami.amazon-ebs.Webserver-VM:   Verifying  : 1:perl-Error-0.17020-2.amzn2.noarch                        11/16
    linux-ami.amazon-ebs.Webserver-VM:   Verifying  : apr-1.7.0-9.amzn2.x86_64                                   12/16
    linux-ami.amazon-ebs.Webserver-VM:   Verifying  : mailcap-2.1.41-2.amzn2.noarch                              13/16
    linux-ami.amazon-ebs.Webserver-VM:   Verifying  : generic-logos-httpd-18.0.0-4.amzn2.noarch                  14/16
    linux-ami.amazon-ebs.Webserver-VM:   Verifying  : mod_http2-1.15.19-1.amzn2.0.1.x86_64                       15/16
    linux-ami.amazon-ebs.Webserver-VM:   Verifying  : httpd-tools-2.4.51-1.amzn2.x86_64                          16/16
    linux-ami.amazon-ebs.Webserver-VM:
    linux-ami.amazon-ebs.Webserver-VM: Installed:
    linux-ami.amazon-ebs.Webserver-VM:   git.x86_64 0:2.32.0-1.amzn2.0.1         httpd.x86_64 0:2.4.51-1.amzn2
    linux-ami.amazon-ebs.Webserver-VM:
    linux-ami.amazon-ebs.Webserver-VM: Dependency Installed:
    linux-ami.amazon-ebs.Webserver-VM:   apr.x86_64 0:1.7.0-9.amzn2
    linux-ami.amazon-ebs.Webserver-VM:   apr-util.x86_64 0:1.6.1-5.amzn2.0.2
    linux-ami.amazon-ebs.Webserver-VM:   apr-util-bdb.x86_64 0:1.6.1-5.amzn2.0.2
    linux-ami.amazon-ebs.Webserver-VM:   emacs-filesystem.noarch 1:27.2-4.amzn2.0.1
    linux-ami.amazon-ebs.Webserver-VM:   generic-logos-httpd.noarch 0:18.0.0-4.amzn2
    linux-ami.amazon-ebs.Webserver-VM:   git-core.x86_64 0:2.32.0-1.amzn2.0.1
    linux-ami.amazon-ebs.Webserver-VM:   git-core-doc.noarch 0:2.32.0-1.amzn2.0.1
    linux-ami.amazon-ebs.Webserver-VM:   httpd-filesystem.noarch 0:2.4.51-1.amzn2
    linux-ami.amazon-ebs.Webserver-VM:   httpd-tools.x86_64 0:2.4.51-1.amzn2
    linux-ami.amazon-ebs.Webserver-VM:   mailcap.noarch 0:2.1.41-2.amzn2
    linux-ami.amazon-ebs.Webserver-VM:   mod_http2.x86_64 0:1.15.19-1.amzn2.0.1
    linux-ami.amazon-ebs.Webserver-VM:   perl-Error.noarch 1:0.17020-2.amzn2
    linux-ami.amazon-ebs.Webserver-VM:   perl-Git.noarch 0:2.32.0-1.amzn2.0.1
    linux-ami.amazon-ebs.Webserver-VM:   perl-TermReadKey.x86_64 0:2.30-20.amzn2.0.2
    linux-ami.amazon-ebs.Webserver-VM:
    linux-ami.amazon-ebs.Webserver-VM: Complete!
==> linux-ami.amazon-ebs.Webserver-VM: Created symlink from /etc/systemd/system/multi-user.target.wants/httpd.service to /usr/lib/systemd/system/httpd.service.
==> linux-ami.amazon-ebs.Webserver-VM: Cloning into 'support'...
==> linux-ami.amazon-ebs.Webserver-VM: Stopping the source instance...
    linux-ami.amazon-ebs.Webserver-VM: Stopping instance
==> linux-ami.amazon-ebs.Webserver-VM: Waiting for the instance to stop...
==> linux-ami.amazon-ebs.Webserver-VM: Creating AMI linux-demo-app from instance i-0a84b26fc430cc6b5
    linux-ami.amazon-ebs.Webserver-VM: AMI: ami-0d5b1c049abfa1194
==> linux-ami.amazon-ebs.Webserver-VM: Waiting for AMI to become ready...
==> linux-ami.amazon-ebs.Webserver-VM: Skipping Enable AMI deprecation...
==> linux-ami.amazon-ebs.Webserver-VM: Terminating the source AWS instance...
==> linux-ami.amazon-ebs.Webserver-VM: Cleaning up any extra volumes...
==> linux-ami.amazon-ebs.Webserver-VM: No volumes to clean up, skipping
==> linux-ami.amazon-ebs.Webserver-VM: Deleting temporary security group...
==> linux-ami.amazon-ebs.Webserver-VM: Deleting temporary keypair...
Build 'linux-ami.amazon-ebs.Webserver-VM' finished after 3 minutes 17 seconds.

==> Wait completed after 3 minutes 17 seconds

==> Builds finished. The artifacts of successful builds are:
--> linux-ami.amazon-ebs.Webserver-VM: AMIs were created:
ap-south-1: ami-0d5b1c049abfa1194

# Validate Result

 Once it completed, log into the AWS console >> EC2 >> Images >> AMIs. From there verify the newly created AMI is listed or not.

 If it is listed, you can use that AMI to launch an Instance with sample website.
