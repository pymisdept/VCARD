# Vcard(HRNC) Application Document

## Environment

###Development Environmet:
1. Python 3.8.10
2. ssh tool (putty/xshell/...)
3. ftp tool (FileZilla/xftp/...)

###Production Environment
####SSH & FTP: 
1. IP: 10.1.1.134 Port: 22
2. Username: xensetech
3. Password: xt@WEB01

####Install Requirements for Python
 `pip install -r requirements.txt`

####BT Panel
http://10.1.1.134:8888/b2957081
username: makgvtxp
password: 343c3940

This Panel is a easy way to manage web server (Nginx)

####Supervisor
Supervisor is a managment tool for process. For this project, supervisor is used to run the django program in background process.
There are some useful command:

    sudo su
    supervisorctl -c /etc/supervisord.conf start vcard //start the program
    supervisorctl -c /etc/supervisord.conf stop vcard //stop the program
    supervisorctl -c /etc/supervisord.conf restart vcard //restart the program
    vim /etc/supervisord.conf //edit the config file for supervisor (May need to learn about how to use vim first)

###Code Structure

```
├─data.xlsx
├─manage.py    //manage file for django
├─requirements.txt
├─vcard
|   ├─asgi.py
|   ├─code.png
|   ├─sample.vcf
|   ├─settings.py
|   ├─urls.py   //controller for the vcard project
|   ├─views.py  //view for the vcard project
|   ├─wsgi.py
|   ├─__init__.py
|   └─__pycache__
|
├─templates
|     └index.html //indext html file
├─static    //folder for static files
|   ├─favicon.ico
|   ├─logo.png
|   ├─logo.svg
|   ├─sample.xlsx
|   ├─script.js
|   └style.css
```

### About code
There is one difference between the version in production environment and source code.
For the settings.py file in source code, there is such a variable

    STATICFILES_DIRS = (os.path.join(BASE_DIR,'static'),)

But in the production environmen, as we are using supervisor to handle the process, the variable need to be modified as 

    STATICFILES_DIRS = os.path.join(BASE_DIR,'static')

I don't know why and I just know it will work :)