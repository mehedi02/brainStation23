1. install Docker-Desktop and enable wsl integration from 
settings--> resources--> wsl integration
2. install minikube
Download executable from [link to minikube](https://github.com/kubernetes/minikube/releases/)
install minikube using downloaded executable
3. Create minikube cluster with 1 master and 2 worker
```bash
minikube start --nodes 3

kubectl label nodes <worker-node-1-name> disktype=ssd
kubectl label nodes <worker-node-2-name> disktype=hdd
```
4. clone this repo and navigate to Task-1 folder and each folder has its own readme file and follow that readme file

5. get nginx url to access app1 and app2
```bash
minikube service --url nginx
```
it will show the url

add **/app1** to the above url to access *app1*
add **/app2** to the above url to access *app2*