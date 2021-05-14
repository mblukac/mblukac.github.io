---
title: "Deploying a {plumber} API to AWS EC2 instance"
date: '2021-05-14'
permalink: /posts/2021/05/plumber_AWSEC2/
tags:
- API
- AWS EC2
- plumber
---

In the last decade, R has grown by leaps and bounds. Expansions like {Shiny} made it extremely easy to generate value with your analysis.


## Setup

1. Login to your AWS account

2. Select an RStudio Server Amazon Machine Image (AIM) from this [link](https://www.louisaslett.com/RStudio_AMI/)

  - I will proceed with the free tier option (t2.micro), click "Review and Launch"

3. Find 'Security Groups' and click "Edit security groups"

<img src="/images/api-tutorial-pic1.png" width="90%">

  - Add "HTTP"
  - Add "Custom TCP Rule", change Port Range to "8000" — this will be a way in to access your API
  - Add "Custom ICMP Rule IPv4", change Protocol "Echo Request", and add Source "0.0.0.0/0" - this will be to check whether everything works well and to troubleshoot. This can be later removed when not necessary.
  
4. SSH key pair
    
  - This is a tricky one: this creates a file that will be used to access the EC2 server from your Terminal. We will need to do this to set up some things later.
  - You can use an existing key pair if you have one (but since you are following this tutorial, it is more likely that you don't). Select "Create a new key pair" and name it (e.g. "my-plumber-key"). This will initiate a download of a new file "my-plumber-key.pem". For now you can leave it in "Downloads", but later it would be better to store it somewhere safe.
  
  <img src="/images/api-tutorial-pic2.png" width="70%">
  
  - Hit "Launch"!
  
5. Go to your [AWS console](http://console.aws.amazon.com) and find your new EC2 (running) instance. Click on the instance number (a long number looking like this: i-098a9123e1c532a123; yes, I made that up). Find a "Connect" button and click it. Open the "SSH client" tab and follow these instructions:

  - Open Terminal (or any other SSH client)
  - We need to find the "my-plumber-key.pem". I left it in Downloads, so I will type `cd Downloads`
  - Run this command: `chmod 400 my-plumber-key.pem`
  - Connect to your instance with the following command: `ssh -i "rstudio-plumber.pem" ubuntu@ec*-*-*-**-**.eu-west-*.compute.amazonaws.com`. You can directly copy this command from the AWS website:

6. Now that you are connected to your AWS EC2 instance, we need to install some missing components. The {plumber} package relies on a library called Libsodium for encryption, decryption, signatures, and password hashing. Ubuntu does not have this installed by default, so we need to download and install it:

  - Get a link to the most current stable version (at the time of the writing, it is `libsodium-1.0.17-stable.tar.gz`) on [this page](https://download.libsodium.org/libsodium/releases/). The link I will use is this [https://download.libsodium.org/libsodium/releases/libsodium-1.0.17-stable.tar.gz](https://download.libsodium.org/libsodium/releases/libsodium-1.0.17-stable.tar.gz). It might change, so make sure you adjust it.
  - Go back to terminal and run `wget https://download.libsodium.org/libsodium/releases/libsodium-1.0.17-stable.tar.gz` (substituting your link). This will download the file to your EC2 instance.
  - You can check that if it happened by running the `ls` command, which will print the contents of the current directory. It should contain a libsodium file --- e.g. `libsodium-1.0.17-stable.tar.gz`, in my case.
  - We need to extract the file by running `tar -xf libsodium-1.0.17-stable.tar.gz` (again, substitute your file name in case you are using a different version)
  - Again, you can check if there is a new folder by running `ls`. If you see it there, you can enter it by running `cd libsodium-stable`.
  - When you are in, execute the following commands: 
    1. `./configure`, 
    2. `make && make check`
    3. `sudo make install`
  - It will take a while to install. When everything finishes, run a final command `sudo apt install libsodium-dev`
  
7. Finally, we can get to R by running `sudo R` and install plumber by `install.packages("plumber")`. Yay! Try veryfing it worked by loading it in by `library(plumber)`.


  






