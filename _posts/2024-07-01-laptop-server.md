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

---
First I followed the steps outlined here:

https://docs.docker.com/desktop/install/linux-install/

---
This helped as well:

If you see the message "Unit docker.service could not be found," it likely means that Docker is not installed on your system. You can install Docker on Ubuntu by following these steps:

1. **Update your package database:**

   ```bash
   sudo apt-get update
   ```

2. **Install the required packages to allow `apt` to use a repository over HTTPS:**

   ```bash
   sudo apt-get install apt-transport-https ca-certificates curl software-properties-common
   ```

3. **Add Docker's official GPG key:**

   ```bash
   curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
   ```

4. **Add the Docker APT repository:**

   ```bash
   sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
   ```

5. **Update your package database again:**

   ```bash
   sudo apt-get update
   ```

6. **Install Docker:**

   ```bash
   sudo apt-get install docker-ce
   ```

7. **Check the Docker service status:**

   ```bash
   sudo systemctl status docker
   ```

8. **Enable Docker to start on boot:**

   ```bash
   sudo systemctl enable docker
   ```

Once installed, you can verify the installation by running:

```bash
docker --version
```

This should display the version of Docker that you have installed. After following these steps, you should be able to start and manage the Docker service without encountering the "Unit docker.service could not be found" message.

---
The trick to pull images is to model this command:

sudo docker pull linuxserver/radarr

---
I used this command to then install radarr:

sudo docker run -d \
  --name=radarr \
  -e PUID=1000 \
  -e PGID=1000 \
  -e TZ=America/New_York \
  -p 7878:7878 \
  -v /home/user/radarr/config:/config \
  -v /home/user/radarr/downloads:/downloads \
  -v /home/user/radarr/movies:/movies \
  --restart unless-stopped \
  linuxserver/radarr

---
Then I used `ip addr show` to find the server ip address. It's the one listed under `docker0` in my case.

---
Now I have radarr running as a Docker container on my laptop. Next step is to see how I can access it remotely and securely from out of the house. I also need to have the thing run 24/7 and with the screen off.

Once I get this to work for a couple of apps, then I'll upgrade. This old laptop is struggling mightily. But I don't want to waste money either, if I can't get this setup to work. 