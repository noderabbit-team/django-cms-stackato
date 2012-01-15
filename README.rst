======================
Django CMS on Stackato
======================

This git repository helps you get up and running quickly w/ a Django CMS installation
on `ActiveState Stackato <http://www.activestate.com/cloud>`_.  The Django project name used in this repo is 'mycms'
but you can feel free to change it.  Right now the backend is mysql.

-------------------
Running on Stackato
-------------------

1. Register for an account
--------------------------

Go to http://community.activestate.com/stackato and register

2. Install the client
---------------------

There are a few different options, follow the steps outlined here. http://docs.stackato.com/quick-start.html#stackato-client-setup

3. Register your client to the cloud
------------------------------------

    $ stackato target api.sandbox.activestate.com
    
    > Successfully targeted to [https://api.sandbox.activestate.com]
    
4. Login to stackato
--------------------

    $ stackato login
    
    > Successfully logged into [https://api.sandbox.activestate.com]
    
5. Download this github repo
----------------------------

    cd ~/projects
    
    git clone git://github.com/kencochrane/django-cms-stackato.git
    
6. Deploy the project to stackato
---------------------------------

    stackato push myblog
    

    