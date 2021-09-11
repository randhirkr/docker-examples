# docker-examples
Docker examples

###Pre-requisites:
docker
aws cli
lightsailctl plugin - install this using brew ( https://brew.sh/ ) /n
`brew install aws/tap/lightsailctl`


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

First create container service on AWS Lightsail and push container image to lightsail container service:
```
aws lightsail push-container-image --region us-east-1 --service-name <container service name> --label hello-world-app --image hello-world-image:latest
```

Reference:
https://lightsail.aws.amazon.com/ls/docs/en_us/articles/amazon-lightsail-install-software
https://aws.amazon.com/getting-started/hands-on/lightsail-containers/?trk=gs_card
