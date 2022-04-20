# Lab2-ST0263

<details>
  <summary>Table of Contents</summary>
  <ol>
    <li><a href="#setup">Setup</a></li>
        <ol>
            <li><a href="#ec2">EC2</a></li>
            <li><a href="#install-docker">Install Docker</a></li>
            <li><a href="#nginx">Nginx</a></li>
        </ol>
    <li><a href="#flow">Flow</a></li>
    <li><a href="#testing">Testing</a></li>
  </ol>
</details>

## Project Objetive

The objetive of this project is to explore docker and nginx to deploy an CMS in this case Wordpress and SSL Certificated provided by Let's Encript. 

## Setup

### EC2

For this project please install any virtual machine or instance on DigitalOcean Droplet, AWS EC2, Google Cloud Compute Engine, Ibm Cloud.

In this case the machine will be created on AWS EC2.

#### Machine setup

For the EC2 instance (free tier)

#### VPC

For the domain you will need to create an elastic IP address 

[How to create Elastic IP](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/elastic-ip-addresses-eip.html)

### Install Docker

For this lab you need to install 
* Docker 
* Docker-Compose

#### Docker

To install docker please follow the steps from the oficial docker webpage

[How to install docker](https://docs.docker.com/engine/install/ubuntu/)

#### Docker-COmpose

To install docker-compose please follow the steps from the oficial docker webpage

[How to install docker-compose](https://docs.docker.com/compose/install/)

#### NOTE

Please follow the steps always on linux.

#### RUN DOCKER

When everthing is done please run this command where is located your docker-compose.yml 

```bash
sudo docker-compose up -d
```
if you wanna see the ports and running containers 

```bash
sudo docker ps
```
<img width="960" alt="image" src="https://user-images.githubusercontent.com/53051443/164322116-ee629ec8-bf6c-401d-b50e-4811de2ab7fa.png">

### Nginx

To install NGINX you need to put this commands on your machine

```bash
sudo apt install software-properties-common
sudo add-apt-repository universe
sudo apt update
sudo apt install certbot python3-certbot-nginx
```

The last command is fundamental to get the SSL certificate on your machine.

#### Setup NGINX

When you install CERTBOT let's generate the cerfiticate but first you need to adquire a domain on this case we are going to use [Freenom](https://www.freenom.com/) 

My domain is daves.tk so let's generate the certificate

```bash
sudo certbot --nginx certonly -d cheems12.tk -d ww3.cheems12.tk
```
Certbot will request you to add your personal email.

when the certificate is done it will be saved on 

```bash
/etc/letsencrypt/live/cheems12.tk/fullchain.pem
/etc/letsencrypt/live/cheems12.tk/privkey.pem
```

To renew your cert run this command

```bash
sudo certbot renew --dry-run
```

Finally run this command and edit Nginx conf file

```bash
sudo nano /etc/nginx/nginx.conf
```

## Flow


## Testing

visit the website https://cheems12.tk/ and check is your browser indicates that your connection is secure

<img width="960" alt="image" src="https://user-images.githubusercontent.com/53051443/164322405-f12fa8c7-e42f-4001-a1ab-7438eca1878a.png">
