
# Install Kubernetes



### 1. Install & Update curl:

```
sudo apt-get update && apt-get install -y apt-transport-https curl

```


### 2. Add Kubernetes Signing Key:

If the node doesn't have gnupg || gnupg1 || gnugp2 installed, need install it first ('sudo apt-get install gnupg')

```
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add

```


### 3. Add Software Repositories:

Kubernetes is not included in the default repositories. To add them, enter the following:


```
sudo apt-add-repository "deb http://apt.kubernetes.io/ kubernetes-xenial main"

```

If get add-apt-repository command not found error,  then install the update first:

sudo apt-get install software-properties-common


### 4. Install Kubernetes tools with the command:

```
sudo apt-get install kubeadm kubelet kubectl

sudo apt-mark hold kubeadm kubelet kubectl

```

### 5. Verify the installation:

```
kubeadm version
```


### --  SSH to each server node and repeat the steps above.
