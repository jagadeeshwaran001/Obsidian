The cloud-native architecture combines software components that development teams use to build and run scalable cloud-native applications. The [[CNCF]] lists immutable infrastructure, microservices, declarative APIs, containers, and service meshes as the technological blocks of cloud-native architecture. 

### **[[Immutable infrastructure]]**

Immutable infrastructure means that the servers for hosting cloud-native applications remain unchanged after deployment. If the application requires more computing resources, the old server is discarded, and the app is moved to a new high-performance server. By avoiding manual upgrades, immutable infrastructure makes cloud-native deployment a predictable process. 

### **[[Microservice]]s**

Microservices are small, independent software components that collectively perform as complete cloud-native software. Each microservice focuses on a small, specific problem. Microservices are loosely coupled, which means that they are independent software components that communicate with each other. Developers make changes to the application by working on individual microservices. That way, the application continues to function even if one microservice fails. 

### **[[API]]**

[Application Programming Interface (API)](https://aws.amazon.com/what-is/api/) is a method that two or more software programs use to exchange information. Cloud-native systems use APIs to bring the loosely coupled microservices together. API tells you what data the microservice wants and what results it can give you, instead of specifying the steps to achieve the outcome. 

### **[[Service mesh]]**

Service mesh is a software layer in the cloud infrastructure that manages the communication between multiple microservices. Developers use the service mesh to introduce additional functions without writing new code in the application. 

### **[[Container]]s**

Containers are the smallest compute unit in a cloud-native application. They are software components that pack the microservice code and other required files in cloud-native systems. By containerizing the microservices, cloud-native applications run independently of the underlying operating system and hardware. This means that software developers can deploy cloud-native applications on premises, on cloud infrastructure, or on hybrid clouds. Developers use containers for packaging the microservices with their respective dependencies, such as the resource files, libraries, and scripts that the main application requires to run.

#### ****Benefits of containers****

Some benefits of containers include:

- You use fewer computing resources than conventional application deployment
- You can deploy them almost instantly
- You can scale the cloud computing resources your application requires more efficiently