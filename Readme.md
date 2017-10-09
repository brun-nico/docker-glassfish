# docker-glassfish
Enhanced Oracle Glassfish container (Java 8 and debug port exposed).
Official Oracle Galssfish container : https://github.com/oracle/docker-images/tree/master/GlassFish

## How to use it
### Build
Build standard
```
docker run --name=myGlassfish -ti -e ADMIN_PASSWORD=admin -p 4848:4848 -p 8080:8080 -p 9009:9009 nbrun/glassfish
```

Enhanced build for dev
```
docker run --network=host --name=myGlassfish -ti -e ADMIN_PASSWORD=admin -p 4848:4848 -p 8080:8080 -p 9009:9009 -v hostPathForConfig:/opt/config -v hostPathForLog:/opt/exploit nbrun/glassfish
```
This build allow :
  - ssh tunneling with option --network=host.
  - Special config for app
  - Access to log on host

### Run
```
docker start -ai myGlassfish
```

### Configuration
Add driver for database
```
docker cp myDriver.jar myGlassfish:/glassfish4/glassfish/lib/
```

## Docker Hub
https://hub.docker.com/r/nbrun/glassfish/
