This [[spring actuator]] endpoint is used to publish the configuration changes to the [[message brokers]].

so that we can able to get the configuration changes in all the [[Microservice]] without the restart.

and [[refresh]] needs multiple times hitting the refresh endpoint for all the microservice, but in [[busrefresh]] we only need to hit this once all the change to the configuration are instantly got refreshed.