- We need to ensure that the one codebase for one [[Microservice]].This will give flexibility and reduce dependency within cross function team.
- It is unnecessary to re-build the codebase for each environment-specific deployment. Instead any factor that vary between [[deployment]], such as configuration settings, should be maintained externally from the application codebase.


>If we have any code common then we need to either create a new library or jar or separate common microservice.