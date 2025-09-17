[[spring actuator]] is used for metrics and monitoring system.

It is also used to refresh the [[spring configuration]] without the server restart.

if the [[actuators]] dependency added and the mangement.endpoint are exposed then we can able to see all the [[actuators]] endpoint list in this url

`host:port/actuator`

ref for [[application.properties or application.yml]] for [[actuators]]

```yaml
management:
	endpoints:
		web:
			exposure:
				//include: refresh
				include "*" //to list all end point

```