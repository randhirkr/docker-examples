# docker-examples
Docker examples

###Pre-requisites:
* docker
* aws cli - required only if images are being pushed to aws lightsail service
* lightsailctl plugin - install this using brew ( https://brew.sh/ ) - required only if images are being pushed to aws lightsail service

`brew install aws/tap/lightsailctl`


For httpd amazon linux based container, clone the project and run below commands:
```
cd httpd-docker-amazon-linux
docker build -t ran-httpd-app .
docker tag ran-httpd-app:latest ran-httpd-app:1.0.0
docker run -t -i -d  -p 80:80 ran-httpd-app
docker images
```

For hello world ubuntu based docker container, clone the project and run below commands:
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
