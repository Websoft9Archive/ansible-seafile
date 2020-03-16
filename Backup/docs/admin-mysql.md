# MySQL

Seafile deployment package includes MySQL, refer to these steps to use it:

1. Use the SSH to connect your Server of Seafile, then run the command `docker ps` to list all containers
  ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/awx/awx-getcontainerid-websoft9.png)

2. Get the container ID of MySQL, and use the following command to login **seafile-mysql** container

   ```
   docker exec -it true 2ca9ad211678 /bin/bash
   ```
3. You can use any MySQL commands if you have connect to **seafile-mysql** container successfully

> Websoft9 provide *[PostgreSQL guide](https://support.websoft9.com/docs/postgresql/admin-phppgadmin.html)* for more useful skills of PostgreSQL, includes: modify password, create user, import/export data, enable or disable remote visit, log configuation and so on.