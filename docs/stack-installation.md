# Initial Installation

If you have completed the Seafile deployment on Cloud Platform, the following steps is for you to start use it quikly

## Preparation

1. Get the **Internet IP** on your Cloud Platform
2. Check you **[Inbound of Security Group Rule](https://support.websoft9.com/docs/faq/tech-instance.html)** of Cloud Console to ensure TCP:**80 and 9002** allowed
3. Make a domain resolution on your DNS Console if you want to use domain for Seafile

> 9003 port is used for preview and edit functions of **OnlyOffice Document Server** 

## Seafile Installation Wizard

1. Using local Chrome or Firefox to visit the URL *http://domain name* or *http://Internet IP*, you will log in interface of Seafile
   ![Seafile login page](http://libs.websoft9.com/Websoft9/DocsPicture/en/seafile/seafile-login-websoft9.png)

2. Input Seafile's username and password[(Get it)](/stack-accounts.md#seafile)
   ![Seafile后台界面](http://libs.websoft9.com/Websoft9/DocsPicture/en/seafile/seafile-bk-websoft9.png)

3. Set or check your Seafile host URL（**Required, otherwise you cannot use the file upload function**）

   - SERVICE_URL：*http://Internt IP of Server*
   - FILE_SERVER_ROOT：*http://Internt IP of Server/seafhttp*

   ![Seafile console UI](https://libs.websoft9.com/Websoft9/DocsPicture/zh/seafile/seafile-seturl-websoft9.png)

4. Start to use it

> More details for using Seafile, please use docs: ***[Seafile user guide](https://help.seafile.com/en/)*** and ***[Seafile Server Manual](http://manual.seafile.com/)***

## Q&A

#### I can't visit the start page of Seafile?

Your TCP:80 of Security Group Rules is not allowed so there no response from Chrome or Firefox

#### Which database does this Seafile use?

MariaDB/MySQL on Docker

#### Why use Docker deployment for Seafile?

Is the officially recommended installation method

#### Does the support document preview and editing by default?

Yes
