This [[actuator endpoints]] will gracefully shoutdown the spring boot applicaiton, In [[production environment]] we should not kill the process like we used to do in out local. We need to shoutdown the application gracefully.

If we hit this endpoint it do multiple task before shoutdown, one of the task is It de-register itself with the [[Eureka server]].

>This is a post method url.