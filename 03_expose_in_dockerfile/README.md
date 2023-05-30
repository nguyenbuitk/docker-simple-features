1. Build the Docker image:
```
docker build -t myapp .
```

2. Run a container from the built image, and map the exposed port to a host port:
```
docker run -p 8080:80 myapp
```