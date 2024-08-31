# This repository for deploy python flask crud application with postgresql in kubernetes (kubeadm, kubelet, kubectl) in AWS EC2

## Install HELM

```
curl -fsSL https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash
```

## Update Repo
```
helm repo add bitnami https://charts.bitnami.com/bitnami
helm repo update
```

## Install Makefile

```
sudo apt install make
```

## Create directory in worker node
```
mkdir pg-data
```

## Update worker node IP on pv-local.yaml file

Update the `pv-local.yaml` file in nodeAffinity `values` with your worker node host name.
```
  nodeAffinity:
          values:
          - ip-172-31-11-83 # Replace withyour worker node host name.
```

## Create postgres DB pods
```
make apply
```

## Deploy python app & service
```
kubectl apply -f py-crud-app-ds.yaml
```

## Create postgres DB pods
```
make delete
```

## Delete pvc manually
```
kubectl delete  pvc data-postgresql-0
```

## Delete directory in worker node
```
sudo rm -rf pg-data/data
```


<br><br>
Happy learning! 💻✨ 
