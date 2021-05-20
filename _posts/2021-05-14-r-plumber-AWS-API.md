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

You start by logging into your [AWS account](http://console.aws.amazon.com). Once in, you select an RStudio Amazon Machine Image (AIM) from this [link](https://www.louisaslett.com/RStudio_AMI/). You are free to chose any, but it's more efficient to choose based on your geography.

Once in AWS, you have to select the machine you want to run it on. AWS EC2 has free tier option called _t2.micro_, and that's the one I will be using here. Click __Review and Launch__.

In the next step, we need to modify the options how we will be able to access the instance. Find 'Security Groups' and click __Edit security groups__. We will add a couple of gates that we will use to connect to the instance:

  - Add "HTTP"
  - Add "Custom TCP Rule", change Port Range to "8000" — this will be a way in to access your API
  - Add "Custom ICMP Rule IPv4", change Protocol "Echo Request", and add Source "0.0.0.0/0" - this will be to check whether everything works well and to troubleshoot. This can be later removed when not necessary.

<p align="center">
<img src="/images/api-tutorial-pic1.png" width="100%">
</p>

You can confirm your selections and move further. You will be asked about a _SSH key pair__. This is a tricky one: This window creates a file that will be used to access the EC2 server from your Terminal. We will need to do this to set up some things later. You can use an existing key pair if you have one (but since you are following this tutorial, it is more likely that you don't). Select __Create a new key pair__ and name it (e.g. "my-plumber-key"). This will initiate a download of a new file "my-plumber-key.pem". For now you can leave it in "Downloads" (if you are on Mac), but later it would be better to store it somewhere safe. Hit __Launch__!
  
  <img src="/images/api-tutorial-pic2.png" width="70%">
  
Now that your instance is successfully running, we need to log in via Terminal and install some missing pieces that will allow us to run an API on R and expose it to the world. Go to your [AWS console](http://console.aws.amazon.com) and find your new EC2 (running) instance. Click on the instance number (a long number looking like this: i-098a9123e1c532a123... yes, I made that up). Find a __Connect__ button and click it. Open the __SSH client__ tab and follow these instructions:

  - Open Terminal (or any other SSH client)
  - We need to find the "my-plumber-key.pem" that you downloaded above. I left it in Downloads, so I will type `cd Downloads`
  - Run this command: `chmod 400 my-plumber-key.pem`
  - Connect to your instance with the following command looking like this one: `ssh -i "rstudio-plumber.pem" ubuntu@ec*-*-*-**-**.eu-west-*.compute.amazonaws.com`. You can either manually adjust the command and fill in * based on your public address or you can directly copy this command from the AWS website in the SSH section that we previously opened.
  
Now that you are connected to your AWS EC2 instance, we need to install some missing components. The {plumber} package relies on a library called `Libsodium` for encryption, decryption, signatures, and password hashing. Ubuntu does not have this installed by default, so we need to download and install it. Hang in there, I know it is messy, but you are very close! Follow these steps:

  - Get a link to the most current stable version (at the time of the writing, it is `libsodium-1.0.17-stable.tar.gz`) on [this page](https://download.libsodium.org/libsodium/releases/). The link I will use is this [https://download.libsodium.org/libsodium/releases/libsodium-1.0.17-stable.tar.gz](https://download.libsodium.org/libsodium/releases/libsodium-1.0.17-stable.tar.gz). It might change, so make sure you adjust it.
  - Go back to terminal and run `wget https://download.libsodium.org/libsodium/releases/libsodium-1.0.17-stable.tar.gz` (substituting your link). This will download the file to the hard drive of your EC2 instance.
  - You can check that if it happened correctly by running the `ls` command, which will print the contents of the current directory. It should contain a libsodium file --- e.g. `libsodium-1.0.17-stable.tar.gz`, in my case.
  - The file we downloaded is compressed, so we need to extract it by running `tar -xf libsodium-1.0.17-stable.tar.gz` (again, substitute your file name in case you are using a different version).
  - Again, you can check if there is a new folder by running `ls`. If you see it there, you can enter it by running `cd libsodium-stable`.
  - When you are in, execute the following commands: 


`./configure`
`make && make check`
`sudo make install`


  - It will take a while to install. When everything finishes, run a final command `sudo apt install libsodium-dev`. Now you are locked and loaded to do some R magic 🪄
  
Now we need to get into R and install {plumber}. We do this by `sudo R` and install plumber by `install.packages("plumber")`. Watch closely that you get any errors here. If the installation of Libsodium failed, you'll see errors. And yay :raised_hands:! Verify it worked by loading the package by running `library(plumber)`.








