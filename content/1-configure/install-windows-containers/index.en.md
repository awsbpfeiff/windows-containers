---
title: "Installing Windows Containers"
weight: 2
---

To interface with containers on Windows, we will utilize Docker.  Docker is an open platform for developing, shipping, and running applications. Docker enables you to separate your applications from your infrastructure so you can deliver software quickly. With Docker, you can manage your infrastructure in the same ways you manage your applications. By taking advantage of Docker’s methodologies for shipping, testing, and deploying code quickly, you can significantly reduce the delay between writing code and running it in production.

Let’s begin the installation.  You will need a couple components installed on your lab host and we will deploy these using PowerShell.  

*  Log into your lab host and open an Administrative PowerShell session.  Run the following:

```powershell
Install-Module -Name DockerMsftProvider -Repository PSGallery -Force
```

* *Enter Y* to download all components

```powershell
Install-Package -Name docker -ProviderName DockerMsftProvider -Verbose
```

* **Enter A** as the source is listed as untrusted
    * **Note:** This will download the binaries for the docker engine, *Enable the Native Containers feature in Windows*, and install the Docker Provider.  
>   ![](/static/images/install-docker.png)
* You will see two core files being referenced

```powershell
C:\Program Files\docker\docker.exe << This is the Docker Client. 
C:\Program Files\docker\dockerd.exe << This is the Docker Engine. 
```

* Restart your lab host to complete the *Windows Containers* feature install

```powershell
Restart-Computer -Force
```

* Log into your lab host and open an Administrative PowerShell session. Verify Docker is running:
  
```powershell
Get-Service docker
```

> ![](/static/images/docker-service.png)

* Next run the following to see details about the version of Docker you are running:

```powershell
docker version
```

> ![](/static/images/docker-version.png)

* You can now access the Docker host remotely

> [Remote Management for Docker Host](https://docs.microsoft.com/en-us/virtualization/windowscontainers/management/manage_remotehost)

* These options you likely won't configure regularly but it is good to know they exist - Docker Daemon startup options:

> [Docker d startup options](https://docs.docker.com/engine/reference/commandline/dockerd/)

