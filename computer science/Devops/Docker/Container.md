[[Container]] is a running environment for an [[images]]
[[Docker]] container is a way to package application with all the necessary dependencies and configuration.

container makes portability easy and makes deployment easy.

There are many publicly available container which can be pulled from the [[DockerHub]]

Containers are madeup of layers of [[images]]

> container has its own virtual [[linux]] file system internally 

> By default there is no data persistence in the container, if we restart the container then all the data will be erased. This can be fix using [[docker volume]]

In most of the case [[alphine]] linux is the base image of the container in docker, because it is very lightweight [[linux]]

![[Pasted image 20250320223747.png]]