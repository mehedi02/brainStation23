```bash
cd deploy
minikube service list
```
get *app1* and *app2* service url
change line **51** and **55** in **nginx_deployment.yaml**
and add *app1 service url* in **location /app1** section with **trailing slash(/)** **important**
and add *app2 service url* in **location /app2** section with **trailing slash(/)** **important**
```bash
kubectl apply -f .
```