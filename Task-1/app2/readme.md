```bash
cd src/laravel-8.6.5
docker image build -t <docker_id>/<image_name>:<tag> .
docker push <docker_id>/<image_name>:<tag>

cd app2/deploy
kubectl apply -f .
```