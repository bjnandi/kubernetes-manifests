# This repository for deploy python flask crud application with postgresql in kubernetes (kubeadm, kubelet, kubectl) in AWS EC2

## Deploy python flask crud application with postgresql using 'Makefile'

### Install Makefile

```
sudo apt install make
```

### Create directory in worker node
```
mkdir pg-data
```

### Update worker node IP on pv-local.yaml file

Update the `pv-local.yaml` file in nodeAffinity `values` with your worker node host name.
```
  nodeAffinity:
          values:
          - ip-172-31-11-83 # Replace withyour worker node host name.
```

### Create postgres DB pods & Deploy python app 
```
make apply
```

### Delete postgres DB pods & Deploy python app 
```
make delete
```


### Delete directory in worker node
```
sudo rm -rf pg-data
```


<br><br>
Happy learning! 💻✨ 
