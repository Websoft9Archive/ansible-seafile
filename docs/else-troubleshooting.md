# Troubleshooting

We collect the most common troubleshooting of using aaPanel for your reference:

> Many troubleshooting is closely related to the Server, if you can confirm troubleshooting is related to Cloud Platform, please refer to [Cloud Platform Documentation](https://support.websoft9.com/docs/faq/tech-instance.html)

#### Database service could not be started?

Insufficient disk space, insufficient memory, and configuration file errors can make database service could not be started  

It is recommended to first check through the command.

```shell
# restart mysql service
systemctl restart mysql

# view disk space
df -lh

# view memory rate
free -lh 
```

#### Seafile upload file error?

You should set the your correct Seafile host after deployment, otherwise you can't upload any files

   - SERVICE_URL：*http://Internet IP of Server*
   - FILE_SERVER_ROOT：*http:/Internet IP of Server/seafhttp*

   ![Seafile Host settings](https://libs.websoft9.com/Websoft9/DocsPicture/zh/seafile/seafile-seturl-websoft9.png)