The [[Microservice]]s [[Backing services]] is a external service which support the functionality of our microservice like [[SMTP]], [[FTP]] server or [[Kafka]] server.

we need to inject those services [[credentials]] using external [[configuration]]. 

Consider a situation where we have different url for accessing the database for different environments. In this case we don't need to make any changes to the code. we need to inject all the required configuration through the external [[configuration]] **after that the application does need a restart to any of the configuration changes**.  