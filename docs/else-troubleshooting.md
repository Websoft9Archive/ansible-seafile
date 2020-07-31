# Troubleshooting

We collect the most common troubleshooting of using RabbitMQ for your reference:

> Instance troubleshooting is closely related to the Instance provider that is Cloud Platform, refer to [Cloud Platform Documentation](https://support.websoft9.com/docs/faq/tech-instance.html)

#### How can I use the logs?

You can find the keywords **Failed** or **error** from the logs directory: `/data/logs`  

You can also use docker command to check error logs: 
```
docker logs seafile
docker logs seafile-mysql
```

#### Seafile upload file error?

You should set the your correct Seafile host after deployment, otherwise you can't upload any files

   - SERVICE_URL：*http://Internet IP of Server*
   - FILE_SERVER_ROOT：*http:/Internet IP of Server/seafhttp*
   
   ![Seafile Host settings](https://libs.websoft9.com/Websoft9/DocsPicture/zh/seafile/seafile-seturl-websoft9.png)