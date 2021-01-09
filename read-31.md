## <span style = "color : red"> Docker</span>

 is really just Linux containers which are a type of virtualization.

* recent years Linux containers, also known as “containerization,” has become increasingly popular. For most applications, a virtual machine provides far more resources than are needed and a container is more than sufficient.

> This, fundamentally, is what ***Docker** is. A way to implement Linux containers!

>> **EXAMPLE**:An analogy we can use here is that of homes and apartments. Virtual Machines are like homes: stand-alone buildings with their own infrastructure including plumbing and heating, as well as a kitchen, bathrooms, bedrooms, and so on. Docker containers are like apartments: they share common infrastructure like plumbing and heating, but come in various sizes that match the exact needs of an owner.

1. Install Docker 
2. check the version by:
```
$ docker --version
Docker version 19.03.5, build 633a0ea
```
3.  ```docker info ```
It will contain a lot of output but focus on the top lines which show we now have 1 container which is stopped and 1 image.
4. ```$ docker image ls```
5. ```$ docker container ls -la```
> why do we need ls -la here instead of ls?.

The answer is because the container is stopped! Only running containers will appear with docker container ls.

## Images and Containers
**An image** is a snapshot in time of what a project contains.

**A container** is a running instance of the image.
![image](https://erick.matsen.org/public/images/docker-stages.png)


>A baking analogy we can use here is as follows:

* <span style =" color: green"> A Dockerfile </span>is the recipe for a cake
*  <span style =" color: green"> An image </span>is a snapshot of the recipe at a given time
* <span style =" color: green">A docker-compose.yml </span>says how to make the cake
And the container is the actual, baked cake.

## Image Layers
Every image is made up of one or more image layers. The base layer is often a flavor of Linux, like alpine. When we built the image for python:3.7-alpine this image had the id b2c276538711. But that image depended on five other images which were visible while building it: 
like:
```
c9b1b535fdd9: Pull complete
2cc5ad85d9ab: Pull complete
```
Image layering and it exists for two main reasons:
* First, each image layer is immutable–unchanged–like a git commit. This helps ensure consistency when two developers build the same image. 

* The second reason is performance. Docker caches the steps in a Dockerfile to speed up subsequent builds. When a change is made to a step, all steps following it will be executed from scratch.

* For this reason, **order matters**
 *in a Dockerfile. Typically you want to put code that won’t change often at the top and code that will change at the end.*
## The important takeaways from this tutorial are this:

* Docker is a way to run Linux containers
* Containers are a lightweight alternative to Virtual Machines
* Dockerfile is a list of instructions for creating an image
* Images are made up of one or more layers
* Containers are a running instance of an image
* docker-compose.yml controls how to run the container
* Containers are stateless and ephemeral in nature. We can link the local filesystem via volumes but things become more complex with databases (which we didn’t cover here).
