---
sidebar_position: 2
---

# Installation

Jenkins installers are available for several Linux distributions.

- Debian/Ubuntu
- Fedora
- Red Hat/Alma/Rocky

This guide covers the installation of Jenkins on an Ubuntu machine.

## Prerequisites

Minimum hardware requirements:

- 256 MB of RAM
- 1 GB of drive space (although 10 GB is a recommended minimum if running Jenkins as a Docker container)

Recommended hardware configuration for a small team:

- 4GB+ of RAM
- 50 GB+ of drive space

Software requirements:

- A machine running Ubuntu 20.04 or later.
- A user account with sudo privileges.
- Java (Jenkins requires Java to run).

## Step 1: Update System Packages

First, ensure that all your system packages are up to date by running the following command:

```bash
sudo apt update && sudo apt upgrade -y
```

## Step 2 : Install Java

Jenkins requires Java to run. Install OpenJDK using the following command:

```bash
sudo apt install fontconfig openjdk-17-jre -y
```

Verify the java installation:

```bash
java -version
```

You should see output similar to:

```bash
openjdk 17.0.12 2024-07-16
OpenJDK Runtime Environment (build 17.0.12+7-Ubuntu-1ubuntu224.04)
OpenJDK 64-Bit Server VM (build 17.0.12+7-Ubuntu-1ubuntu224.04, mixed mode, sharing)
```

## Step 3 : Add Jenkins Repository

Add the Jenkins Debian package repository to your system. First, import the GPG keys:

```bash
sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
```

Then, add the Jenkins repository to the sources list:

```bash
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
```

## Step 4 : Install Jenkins

After adding the Jenkins repository, update the package list:

```bash
sudo apt update
```

now instlal jenkins:

```bash
sudo apt install jenkins -y
```

## Step 5: Start and Enable Jenkins

Once installed, start Jenkins with the following command:

```bash
sudo systemctl start jenkins
```

Enable Jenkins to start on boot:

```bash
sudo systemctl enable jenkins
```

Check the status of Jenkins to ensure it is running:

```bash
sudo systemctl status jenkins
```
