This cmt used to run the docker [[images]] as a [[Container]]. if the image is not present in local system then it search for the the image in [[DockerHub]] automatically and try to pull those.

## flags
> -d => used to run the docker in the detached mode, meaning the container is running in the background instead of the current terminal window.                                                           eg: docker run -d redis

> -p {localSystem port : container port} => used to specifty the port