# spring-cloud-config-2

## Background:
When server changed anything, the client may need to modify the configuration. It is to register the config-server to Eureka, so that client can acquire service from Eureka. 

## Steps:
Start up Eureka, config-server, config-client

### Eureka
![image](https://github.com/cyx441984694/spring-cloud-config-bus/blob/main/eureka.PNG)

### config-server
![image](https://github.com/cyx441984694/spring-cloud-config-bus/blob/main/server1.PNG)

### config-client
![image](https://github.com/cyx441984694/spring-cloud-config-bus/blob/main/client.PNG)

Bring down one of the spring-cloud-config-server, the client can still access.

## Reference:
http://www.ityouknow.com/springcloud/2017/05/25/springcloud-config-eureka.html
