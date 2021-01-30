# spring-cloud-config-eureka-bus

## Background:
Two features:
1. It is to register the config-server to Eureka, so that client can acquire service from Eureka.</br>
2. When change the properties, you don't need to restart config-server and config-client. 

## Steps:
Start up Eureka, config-server 2 instances- the seond one with port 8003, config-client

### Eureka
![image](https://github.com/cyx441984694/spring-cloud-config-bus/blob/main/eureka.PNG)

### config-server
![image](https://github.com/cyx441984694/spring-cloud-config-bus/blob/main/server1.PNG)

### config-client
![image](https://github.com/cyx441984694/spring-cloud-config-bus/blob/main/client.PNG)

Bring down one of the spring-cloud-config-server, the client can still access.

Change the neoconfig-dev.properties at the github side.
Post a request to http://localhost:8001/actuator/bus-refresh
refresh the page of http://localhost:8001/neoconfig/dev, http://localhost:8002/hello. They all get updated.
Check the log: get http://localhost:8001/actuator/httptrace
'''
{"traces":[{"timestamp":"2021-01-30T11:37:50.390398700Z","principal":null,"session":null,"request":{"method":"POST","uri":"http://localhost:8001/actuator/httptrace","headers":{"content-length":["0"],"host":["localhost:8001"],"connection":["Keep-Alive"],"cache-control":["no-cache"],"accept-encoding":["gzip,deflate"],"accept":["*/*"],"user-agent":["Apache-HttpClient/4.5.6 (Java/1.8.0_152-release)"]},"remoteAddress":null},"response":{"status":405,"headers":{"Allow":["GET"]}},"timeTaken":1},{"timestamp":"2021-01-30T11:37:41.205089100Z","principal":null,"session":null,"request":{"method":"POST","uri":"http://localhost:8001/actuator/bus-refresh","headers":{"content-length":["0"],"host":["localhost:8001"],"connection":["Keep-Alive"],"cache-control":["no-cache"],"accept-encoding":["gzip,deflate"],"accept":["*/*"],"user-agent":["Apache-HttpClient/4.5.6 (Java/1.8.0_152-release)"]},"remoteAddress":null},"response":{"status":204,"headers":{}},"timeTaken":3171},{"timestamp":"2021-01-30T11:37:42.481792900Z","principal":null,"session":null,"request":{"method":"GET","uri":"http://LAPTOP-VNBE4BVJ:8001/neoconfig/dev/master","headers":{"host":["LAPTOP-VNBE4BVJ:8001"],"connection":["keep-alive"],"accept":["application/json"],"user-agent":["Java/11.0.1"]},"remoteAddress":null},"response":{"status":200,"headers":{"Transfer-Encoding":["chunked"],"Date":["Sat, 30 Jan 2021 11:37:43 GMT"],"Content-Type":["application/json;charset=UTF-8"]}},"timeTaken":1372},{"timestamp":"2021-01-30T11:37:27.303636600Z","principal":null,"session":null,"request":{"method":"POST","uri":"http://localhost:8001/actuator/bus-trace","headers":{"content-length":["0"],"host":["localhost:8001"],"connection":["Keep-Alive"],"cache-control":["no-cache"],"accept-encoding":["gzip,deflate"],"accept":["*/*"],"user-agent":["Apache-HttpClient/4.5.6 (Java/1.8.0_152-release)"]},"remoteAddress":null},"response":{"status":405,"headers":{"Allow":["GET"]}},"timeTaken":20}]}
'''

## Reference:
http://www.ityouknow.com/springcloud/2017/05/25/springcloud-config-eureka.html
