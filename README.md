# Kubernestes

## kubernetes bash-completion
install 
bash-completion is provided by many package managers
```sh
apt-get install bash-completion
```
```sh
kubectl completion bash
cd .kube/
kubectl completion bash > kubetl.sh
```
## Kubernetes pod
A pod is a group of one or more containers,within shared storage and network resources and specification for how to run the containers.

kubectl pod
```sh
kubectl get po/pod/pods
```
kubectl create
```sh
kubectl create -f <file.yml> --dry-run
```
kubectl apply
```sh
kubectl apply-f <file.yml>
```
Delete All pods
```sh
kubectl delete pod --all
```
Kubectl Explain
```sh
kubectl explain pods |less
kubectl explain ReplicaController |less
```
Kubectl Describe
```sh
kubectl describe pod <pod name>
kubectl describe pod <pod name> | less
```
Kubectl Delete
```sh
kubectl delete <Resourcestype>  <Resourscesname>
kubectl delete pod <pod name>
kubectl delete pod <podfile.yml>
```
## kubectl label
```sh
kubectl label pod <pod name> <environment name>=<name>
kubectl label pod nginx env1=test
```
kubectl Overwrite label
```sh
kubectl label --overwrite <pod name> <environment name>=<name>
```
Multiple pod label add
```sh
kubectl label pods --all status=abc
```
kubectl label delete
```sh
kubectl label pod <pod name> <environment name> -
kubectl label pod nginx env-
```
All labels show 
```sh
kubectl get pods --show-labels
```
## Environment Variable in Pod's Container
```sh 
kubectl apply -f <file.yml>
kubectl get pod -o wide
docker container exec -it <container id> env
```
Run command in pod's container 
```sh
kubectl exec nginx env
kubectl exec nginx -c nginx
docker container exec -it <c id> bash
kubectl exec nginx -it bash
kubectl exec nginx -c nginx -it bash 
```
 Kubernetes ----> Cluster Ip
```sh
kubectl apply -f <file.yml>
kubectl expose pod < podName> --port=8000 --target-port=80 --name service1
kubectl get service/svc
```
## Node port
```sh
kubectl expose pod < podName> --type=NodePort --port=8000 --target-port=80 --name service1
```
## ReplicationController
```sh
kubectl explain rc 
kubectl get rc -w
kubectl describe rc replicationcontroller
```

ReplicationController Delete
```sh
kubectl delete rc <replication name>
```
Replication Controller Scaling
```sh
kubectl scale rc --replicas=number <relication Name>
 Ex: kubectl scale rc --replicas=4 nginx
 kubectl edit rc nginx
 kubectl replace -f b.yml
```
# Kubernetes Namespaces
Viewing namespaces
```sh 
kubectl get namespaces
kubectl get ns
```
Namespace resources Support and Unsupport
```sh
kubectl api-resources
kubectl api-resources | grep -i pod
kubectl api-resources | grep -i nodes
kubectl api-resources | grep -i volume
```
Namespace Create 
```sh
kubectl create namespace <insert-namespace-name-here>
kubectl apply -f <file.yml>
```
Deleting a namespace
```sh
kubectl delete namespaces <insert-some-namespace-name>
```
Namespace pod
```sh
kubectl apply -f <file.yml> --namespace <Namespace name>
```
Viewing the namespace pod
```sh
kubectl get pods -n <Namespace name>
```
All namespace pod view
```sh
kubectl get pods  --all-namespaces
```
Namespace Pod delete
```sh
kubectl delete pod <pod name> -n <namespace name>
```
```sh
kubectl explain --recursive pod
```
# Config Map
A ConfigMap is an API object used to store non-confidential data in key-value pairs. Pods can consume ConfigMaps as environment variables, command-line arguments, or as configuration files in a volume.

A ConfigMap allows you to decouple environment-specific configuration from your container images, so that your applications are easily portable.

Create config Map
```sh
kubectl create cm <cm name> --from-literal=database_ip="192.168.0.4"
kubectl describe cm cm1
```
Viewing  the congfig map
```sh
kubectl get cm
```
Configmap with from-env-file
```sh
vi env.sh
vim env.sh
cat env.sh
````
Create a config Map
```sh
kubectl create cm  <congig map Name> --from-env-file=env.sh
kubectl create cm <congig map Name>  --from-file=env.sh
```
Describe
```sh
kubectl describe cm fromfilecm
```
