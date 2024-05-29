Discovery Service

* Whenever we configure Discovery service in an application it will manage all the host and port of that application and registers it
* Whenever a client makes a call to server side discovery service helps providing the host details of that particular app


*eureka.client.fetch-registry=false -> This property will make eureka server to not to search for another discovery client for registries.
 If we don't use this when we have only one eureka server it constantly looks for every 30s for another client for registry and end up failure

*implementation 'org.springframework.cloud:spring-cloud-starter-netflix-eureka-server' -> We have added this jar and internally it has
a sub jar which is spring-cloud-starter-netflix-eureka-client this jar is used for fetching registry from different eureka servers and maintain sync.
If we have multiple instnace of same applications on different zones which is registered with differnt eureka server then these eureka server makes itself as client and looks for other discovery service to fetch their registers



*eureka.client.register-with-eureka=false -> this property will help not to register the discovery service itself


*@EnableEurekaServer - helps to create a Marker bean. 
*Whenever we have @EnableEurekaServer annotation upon application starts it triggers  EurekaServerMarkerConfiguration class 
*EurekaServerMarkerConfiguration this class helps to create a bean for marker class
*Once the marker bean is available  and  EurekaServerAutoCOnrfiguration triggers it checks whether the bean is created or not
*once the bean is availble this EurekaServerAutoCOnrfiguration setups eureka server based on a bean called marker which is in EurekaServerMarkerConfiguration class

