# Many-Docker-Composes
holds docker-compose and supporting files for many infrastructures that goes together
Each folder is a sub-project of sorts to start a specific stack with docker-compose.

# elk+nginx
This subproject is configured to start Elastic Search, Kibana and NGInx to proxy request to those two.

## Notes:
+ Elastic maps a volume under the current directory for holding elastic data.
+ Kibana is configure by mapping the kibana.yml as a volume.
+ NGInx serves any files under ./www
+ NGInx loads its configuration (and the proxy_pass) from the ./conf/nginx.conf file.
+ nginx.conf uses the container names to map its proxy_pass to elastic and kibana.
+ kibana has specific configuration on kibana.yml to set the basePath and a specific rewrite to abide by that basePath.

# kafka
This subproject stands up basic kafka containers:
+ zookeeper
+ kafka
+ schema-registry
+ kafka rest

# kafka-connect
This subproject stands up the kafka connect broker and a UI 


