Running the app without Installing
==============================

    virutalenv  
    source  /bin/activate
    pip install -r requirements.txt
    cd  
    foreman start

 The above steps will do the following 2 things:
 - start up the web server
 - start the scheduler, with a job running at 22:30 every day for crawling the job sites.

Accessing the app
-----------------
    
    http://0.0.0.0: 

Installing the app as command line tool
=======================================
	
	python setup.py install # this will install zjobs as a command line app

  Setuping the Environemnt Config
  ---------------------------------

    export DB_HOST=  
    export DATABASE= 
    export DB_USER= 
    export DB_PASSWORD= 

   Using the app
   -------------

	zjobs  # this will start the web application and start the backend scheduler

   Accessing the app
   -----------------
    
    http://0.0.0.0: 


Reference: Setup POSTGRES and databases
====================================

  Install Postgresql Database

      sudo apt-get install postgresql

  Switch User

      sudo su postgres

  Enter the command line:

       psql

  Setup the database and its users

       postgres=# CREATE USER zjobs WITH PASSWORD 'zjobs';
       postgres=# CREATE DATABASE zjobs;
       postgres=# GRANT ALL PRIVILEGES ON DATABASE zjobs TO zjobs;

Setuping Ubuntu development dependencies
==========================================

The following development dependencies needs to be installed in order for lxml and twisted to work

     sudo apt-get install python-dev
     sudo apt-get install libffi-dev
     sudo apt-get install libssl-dev



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)