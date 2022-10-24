# demo-deploy

## 1. Install go-zero
```
go install github.com/zeromicro/go-zero/tools/goctl@latest
```

## 2. Make API
```
goctl api new hello
```

## 3.Project Init
```
cd hello
go mod init
go mod tidy
```

## 4.Run and Test
```
go run hello.go -f etc/hello-api.yaml
curl -i http://localhost:8888/from/you
```

## 5.Make Dockerfile
```
goctl docker -go hello.go
```

## 6.Docker build
```
docker build -t hello:v1.0 .
```

## 7.Docker run
```
docker run --rm -it -p 8888:8888 hello:v1.0
```

## 8 Docker push
```
Docker login
docker tag hello:v1.1 ******/demo-deploy:v1.0
docker push ******/demo-deploy:v1.0
```

---

## Make k8s yml
```
goctl kube deploy -name demo-deploy -namespace demo -image ******/demo-deploy:v1.0 -o demo-deploy.yaml -port 8888
```
