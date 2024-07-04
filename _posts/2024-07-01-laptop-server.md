---
layout: post
title: DGK Self Hosted - The Jump Off
---
After yet another email to describe the increased price of a subscription service, I decided to self host a few things. 

For this project, I'll use an old laptop that is kicking around. 

**OS**
- Ubuntu

**Apps**
- Actual Budget - since YNAB seems to increase their prices on a yearly basis
- Arr suite
- Overseerr
- [Calibre / Readarr](https://academy.pointtosource.com/containers/ebooks-calibre-readarr/)

**OS Install**
- Grab a USB stick
- Download Ubuntu Desktop iso
- Download Balena Etcher
- Flash the iso to the USB
- Boot the laptop from USB

https://cyberhost.uk/5-minute-server-setup/

---
I prompted HuggingChat for help with the initial setup, and here's what it spit back:

What a great idea! Running a self-hosted server on your Ubuntu laptop with Docker is a fantastic way to have control over your data and applications. I'd be happy to help you set it up.

Here's a step-by-step guide to get you started:

**Prerequisites:**

1. Your Ubuntu laptop is connected to a network (e.g., your home network or a VPN).
2. You have a basic understanding of Docker and Linux.

**Step 1: Install Docker on your Ubuntu laptop**

Open a terminal on your Ubuntu laptop and run the following commands:
```
sudo apt update
sudo apt install docker.io
sudo systemctl start docker
sudo systemctl enable docker
```
This will install Docker and start the service.

**Step 2: Pull the Docker image for your desired application**

Choose an application you want to run, such as Nextcloud, Plex, or GitLab. Find the official Docker image for that application on Docker Hub. For example, let's use Nextcloud:
```
docker pull nextcloud
```
This will download the Nextcloud Docker image.

**Step 3: Run the Docker container**

Create a new container from the pulled image:
```
docker run -d --name nextcloud \
  -p 8080:80 \
  -v /path/to/nextcloud/data:/var/www/html \
  nextcloud
```
Here:

* `-d` runs the container in detached mode.
* `--name nextcloud` gives the container a name.
* `-p 8080:80` maps port 8080 on your laptop to port 80 in the container.
* `-v /path/to/nextcloud/data:/var/www/html` mounts a volume for data persistence.

**Step 4: Configure your application**

Access your application by visiting `http://localhost:8080` in your web browser. You'll need to configure the application, such as setting up an admin account and configuring any necessary settings.

**Step 5: Expose your application to the outside world**

To access your application remotely, you'll need to forward the port from your router to your laptop. This process varies depending on your router model, so you may need to consult your router's documentation.

As an alternative, you can use a reverse proxy like Nginx or Apache to expose your application. This is a more secure and flexible approach, but it requires additional setup.

**Step 6: Secure your setup**

Make sure to:

* Use strong passwords and authentication for your application.
* Limit access to your application by configuring firewall rules or using a VPN.
* Regularly update your Docker image and application to ensure you have the latest security patches.

That's it! You now have a self-hosted server running on your Ubuntu laptop with a Dockerized application. You can access your application remotely by visiting `http://your-laptop-ip:8080` (replace `your-laptop-ip` with your laptop's IP address).

If you encounter any issues or have further questions, feel free to ask!