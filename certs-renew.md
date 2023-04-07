
## Renew Kubernetes TLS Certificates

By default, kubeadm generates all the certificates needed for a cluster to run. You can override this behavior by providing your own certificates.

By default, these certificates expire a year from the day of creation, and when they do, you may be faced with an error message similar to this:

```
[authentication.go:64] Unable to authenticate the request due to an error: 
[x509: certificate has expired or is not yet valid, x509: certificate has expired or is not yet valid

```
 
You can use the check-expiration subcommand to check when certificates expire:

```
kubeadm certs check-expiration

```

-  Renew certs manually

Log into the Kubernetes primary control-plane node and use the following kubeadm command:

$ kubeadm certs renew all

Then copy the new configuration with the renewed certificate to the Kubernetes configuration directory. This will allow for kubectl and other client tools which use the certificates for encryption and authentication to connect to the API again:
 
```
$ cd ~/.kube

# Archive the old config file containing the out of date certificates
$ mv config conf.archive.2021

# Copy the new configuration file created using kubeadm
$ cp /etc/kubernetes/admin.conf config

# apply permissions to your current admin user and group
$ sudo chown $(id -u):$(id -g) config
``` 

- Automatic certificate renewal

kubeadm renews all the certificates during control plane [upgrade](https://kubernetes.io/docs/tasks/administer-cluster/kubeadm/kubeadm-upgrade/).