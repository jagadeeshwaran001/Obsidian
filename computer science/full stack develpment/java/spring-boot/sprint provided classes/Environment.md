
This is a [[spring-componet]] provided by [[spring]]. This is also like [[@Value]] but this is more secure. This is used to get values from system environmental variables.

We can directly inject this class in any of the [[spring-componet]] class.

```java
@Autowire
Environment environment;

public Stirng javaVersion() {
	return  environment.getProperty("java_home");
}

```
