# estatio-docker

Dockerfile for [estatio](https://github.com/estatio/estatio)

## To use:
1. Install [Docker](https://www.docker.com/)

2. Make a directory to store the persistor file and copy the template from the [orginal repo](https://github.com/estatio/estatio/tree/master/estatioapp/webapp/src/main/webapp/WEB-INF), naming it persistor.properties. Configure the file to suit your needs. Example below

  ```
  isis.persistor.datanucleus.impl.javax.jdo.option.ConnectionDriverName=org.hsqldb.jdbcDriver
  isis.persistor.datanucleus.impl.javax.jdo.option.ConnectionURL=jdbc:hsqldb:mem:test
  isis.persistor.datanucleus.impl.javax.jdo.option.ConnectionUserName=sa
  isis.persistor.datanucleus.impl.javax.jdo.option.ConnectionPassword=

  ```


3. Run the container, pointing to the directory with the config file. This should now pull the image from Docker hub:
  ```
  docker run -d -p 8080:8080 \
  --name="estatio" \
  -v <path to config folder>:/config \
  --restart="always" \
  nathanthegr8/estatio-docker
  ```
  
## Port Conflicts
If you run into a port conflict trying to run on 8080 it is simple to modify the port forwarding:

```-p 8081:8080```
