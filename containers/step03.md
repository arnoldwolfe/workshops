# Simple App Containerization hands-on lab with Docker 
## Lifecycle of a container

Images of containers are immutable.  (i.e. when you start a container, and make file modifications, it does not modify the original image.)  However, you can create a new image based off of the modified container.

The `commit` command provides an easy and useful way to debug and iteratively perfect your container. When you iterate over a container configuration with `commit`, take good notes and incorporate the changes you want to keep in the Dockerfile used to manage your image in a documented and maintainable way.

### Start and modify a Ubuntu container 
Start an Ubuntu Container:
```
docker run -it ubuntu /bin/bash
```
(Note: If this command fails in Docker for Windows, try `docker run -it ubuntu //bin/bash` or `winpty docker run -it ubuntu //bin/bash`.)

Make a change to the container and exit
```
touch /tmp/foo
ls /tmp/foo
```

Notice the file
```
exit
```

Start the container again
```
docker run -it ubuntu /bin/bash
ls /tmp/foo
```

### Now we will start a new image of Ubuntu and save it.
Start an Ubuntu Container:
```
docker run -it ubuntu /bin/bash
```

Make a change to the container and exit
```
touch /tmp/foo
ls /tmp/foo
exit
```

IN A NEW WINDOW, with the container still running:
```
docker ps -a | head -2
docker diff <Container ID>
```

Commit the container
```
docker commit <Container ID> ubuntu-foo
```

List Images
```
docker images
```

Notice the new ubuntu-foo image

Run the container
```
docker run -it ubuntu-foo /bin/bash
ls /tmp/foo
```

Now the file exists


## Lab Navigation
1. [Lab Overview](./index.md)
1. [Installing Docker locally](./step01.md)
1. [Running a simple app in a Docker container locally](./step02.md)
1. [Lifecycle of a container](./step03.md) *<-- You are here*
1. [Creating and running Docker images using a Dockerfile](./step04.md)
1. [Defining and running multi-container Docker applications using Docker compose](./step05.md)
1. [Running CAT Sample App locally](./step06.md)

[Back to Index](../../index.md)
