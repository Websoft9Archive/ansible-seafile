# Initial Installation

If you have completed the Seafile deployment on Cloud Platform, the following steps is for you to start use it quikly

## Preparation

1. Get the **Internet IP** on your Cloud Platform
2. Check you **[Inbound of Security Group Rule](https://support.websoft9.com/docs/faq/tech-instance.html)** of Cloud Console to ensure TCP:**80 and 9002** allowed
3. Make a domain resolution on your DNS Console if you want to use domain for Seafile

> 9002 port is used for preview and edit functions of **OnlyOffice Document Server** 

## Seafile Installation Wizard

1. Using local Chrome or Firefox to visit the URL *http://domain name* or *http://Internet IP*, you will log in interface of Seafile
   ![Seafile login page](http://libs.websoft9.com/Websoft9/DocsPicture/en/seafile/seafile-login-websoft9.png)

2. Input Seafile's username and password[(Get it)](/stack-accounts.md#seafile)
   ![Seafile console interface](http://libs.websoft9.com/Websoft9/DocsPicture/en/seafile/seafile-bk-websoft9.png)

3. Set or check your Seafile host URL（**Required, otherwise you cannot use the file upload function**）

   - SERVICE_URL：*http://Internt IP of Server*
   - FILE_SERVER_ROOT：*http://Internt IP of Server/seafhttp*

   ![Seafile console UI](https://libs.websoft9.com/Websoft9/DocsPicture/en/seafile/seafile-seturl-websoft9.png)

4. Start to use it

> More details for using Seafile, please use docs: ***[Seafile user guide](https://help.seafile.com/en/)*** and ***[Seafile Server Manual](http://manual.seafile.com/)***

## Seafile Setup Wizard

Below we are familiar with the use of Seafile through operations such as creating a library, creating files, editing files, setting permissions, and user sharing.

### Add & Edit file

The following is the steps about how to create file and edit file:

1. Login to Seafile Console, and add 【New library】and 【New file】

   ![Seafile add library](https://libs.websoft9.com/Websoft9/DocsPicture/en/seafile/seafile-addlib-websoft9.png)

   ![Seafile add file](https://libs.websoft9.com/Websoft9/DocsPicture/en/seafile/seafile-addfile-websoft9.png)

2. Edit file online by **OnlyOffice Document Server**

   ![Seafile edit file](https://libs.websoft9.com/Websoft9/DocsPicture/en/seafile/seafile-editfile1-websoft9.png)

### User management

The following is the steps about how to create user and group:

1. Click the icon of user and enter to【System Admin】, click【Add user】and【New Group】

   ![Seafile system admin](https://libs.websoft9.com/Websoft9/DocsPicture/en/seafile/seafile-system-websoft9.png)

   ![Seafile add user](https://libs.websoft9.com/Websoft9/DocsPicture/en/seafile/seafile-adduser-websoft9.png)

   ![Seafile add group](https://libs.websoft9.com/Websoft9/DocsPicture/en/seafile/seafile-addgroup-websoft9.png)

2. Set the user to a group

   ![Seafile user group](https://libs.websoft9.com/Websoft9/DocsPicture/en/seafile/seafile-addusertogroup-websoft9.png)

### Share file

The following is the steps about how to share files to other user:

1. Enter to【My Library】, click share icon

   ![Seafile share file](https://libs.websoft9.com/Websoft9/DocsPicture/en/seafile/seafile-sharefile1-websoft9.png)


2. Set permission to【Read】or【Read-Write】

   ![Seafile file share](https://libs.websoft9.com/Websoft9/DocsPicture/en/seafile/seafile-sharefile-websoft9.png)


### Edit shared file

The following is the steps about how to edit the shared files:

1. User another user to login Seafile(username: user1@websoft9)
   ![Seafile login page](https://libs.websoft9.com/Websoft9/DocsPicture/en/seafile/seafile-login1-websoft9.png)

2. Click 【Shared with me】 and edit the file you selected, then logout
   ![Seafile view shared file](https://libs.websoft9.com/Websoft9/DocsPicture/en/seafile/seafile-viewsharefile-websoft9.png)
   ![Seafile edit shared file](https://libs.websoft9.com/Websoft9/DocsPicture/en/seafile/seafile-editfile-websoft9.png)

3. Login with administrator user `me@example.com` and view the history version of file
   ![Seafile view the history version](https://libs.websoft9.com/Websoft9/DocsPicture/en/seafile/seafile-viewfileinfo1-websoft9.png)
   ![Seafile view the history version](https://libs.websoft9.com/Websoft9/DocsPicture/en/seafile/seafile-viewfileinfo-websoft9.png)

## Q&A

#### I can't visit the start page of Seafile?

Your TCP:80 of Security Group Rules is not allowed so there no response from Chrome or Firefox

#### Which database does this Seafile use?

MariaDB/MySQL on Docker

#### Why use Docker deployment for Seafile?

Is the officially recommended installation method

#### Does the support document preview and editing by default?

Yes
