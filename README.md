# docker-examples
Docker examples

For hello world container:
```
cd hello-world-container
```

Build the image:
```
docker build -t hello-world-image .
```

Verify the image:
```
docker images --filter reference=hello-world-image
```

Run the container:
```
docker container run -d -p 8080:80 --name hello-world-app hello-world-image:latest
```
verify the container:
```
docker ps
docker container ls -a
```

cleanup the container:
```
docker container rm <ContainerName> --force
docker container rm hello-world-app --force
```
