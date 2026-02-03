# lsy

Go-zero REST 微服务示例（K8s 友好），内置健康检查与简单 `items` CRUD（内存存储）。

## Features
- go-zero REST server
- `/healthz` 与 `/readyz`
- 内存版 `items` CRUD
- Dockerfile + K8s Deployment/Service/HPA + ConfigMap

## Endpoints
- `GET /healthz`
- `GET /readyz`
- `GET /items`
- `POST /items`
- `GET /items/:id`
- `PUT /items/:id`
- `DELETE /items/:id`

## Local Run
```bash
go run ./main.go -f etc/items-api.yaml
```

## Example
```bash
curl -X POST http://localhost:8888/items \
  -H 'Content-Type: application/json' \
  -d '{"name":"demo","description":"hello"}'

curl http://localhost:8888/items
```

## Docker
```bash
docker build -t items-api:latest .

docker run --rm -p 8888:8888 items-api:latest
```

## K8s
```bash
kubectl apply -f k8s/configmap.yaml
kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml
kubectl apply -f k8s/hpa.yaml
```
