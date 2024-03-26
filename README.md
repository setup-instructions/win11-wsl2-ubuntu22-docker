# win11-wsl2-ubuntu22-docker
Configuração do docker no Windows 11 WSL2 utilizando o Ubuntu 22.04.3

# Install using the apt repository

## Set up Docker's apt repository.
```bash
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

## Install the Docker packages.
```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

## Verify that the Docker Engine installation is successful by running the hello-world image.
```bash
sudo docker run hello-world  
```

# Manage Docker as a non-root user

## Create the docker group.
```bash
sudo groupadd docker
```

## Add your user to the docker group.
```bash
sudo usermod -aG docker $USER
```

## Log out and log back in so that your group membership is re-evaluated.
```bash
newgrp docker
```

## Verify that you can run docker commands without sudo.
```bash
docker run hello-world
```

# Install Compose standalone (deprecated)
## To download and install Compose standalone, run:
```bash
curl -SL https://github.com/docker/compose/releases/download/v2.26.0/docker-compose-linux-x86_64 -o /usr/local/bin/docker-compose
```
Apply executable permissions to the standalone binary in the target path for the installation.

## Test and execute compose commands using docker-compose.
```bash
sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
```

# Documentação oficial:
- https://docs.docker.com/engine/install/ubuntu/
- https://docs.docker.com/engine/install/linux-postinstall/
- https://docs.docker.com/compose/install/standalone/
- https://docs.docker.com/compose/compose-application-model/
