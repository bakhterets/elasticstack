# elastic-stack
This example Docker Compose configuration demonstrates components of the Elastic Stack, nginx reverse proxy and nginx-ldap-auth module.
## Description
Instruction for set up nginx configuration file and nginx-ldap-auth:
      https://github.com/nginxinc/nginx-ldap-auth
### Docker and docker-compose:
copy docker-compose.yml file and nginx-ldap-auth directory and run: 
`docker-compose up -d`
***
Please, read notes for production and defaults:

    https://www.elastic.co/guide/en/elasticsearch/reference/7.3/docker.html#_notes_for_production_use_and_defaults
    
      mkdir esdatadir
      chmod g+rwx esdatadir
      chgrp 1000 esdatadir
* By default, Elasticsearch runs inside the container as user elasticsearch using uid:gid 1000:1000.
One exception is Openshift, which runs containers using an arbitrarily assigned user ID. Openshift will present persistent volumes with the gid set to 0 which will work without any adjustments.
If you are bind-mounting a local directory or file, ensure it is readable by this user, while the data and log dirs additionally require write access. A good strategy is to grant group access to gid 1000 or 0 for the local directory. As an example, to prepare a local directory for storing data through a bind-mount
* As a last resort, you can also force the container to mutate the ownership of any bind-mounts used for the data and log dirs through the environment variable TAKE_FILE_OWNERSHIP. In this case, they will be owned by uid:gid 1000:0 providing read/write access to the Elasticsearch process as required.
