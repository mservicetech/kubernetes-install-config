
# Set up Docker

### 1. Update the package list with the command:

```
sudo apt-get update

```

### 2. Install Docker with the command:

```
sudo apt-get install docker.io
```

### 3. Check the installation (and version) by entering the following:

```
docker ––version
```

### 4. Set Docker to launch at boot by entering the following:

```
sudo systemctl enable docker
```

### 5. Verify Docker is running:

```
sudo systemctl status docker
```

### To start Docker if it’s not running:

```
sudo systemctl start docker
```

### --  Repeat on all the other nodes.
