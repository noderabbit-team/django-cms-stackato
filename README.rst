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

    $ cd ~/projects
    
    $ git clone git://github.com/kencochrane/django-cms-stackato.git
    
    $ cd django-cms-stackato
    
6. Deploy the project to stackato
---------------------------------

    $ stackato push myblog
    
7. Initialize the database (optional)
-------------------------------------

Should happen automatically at deployment see stackato.yml file for more details.

    $ stackato run myblog python mycms/manage.py syncdb --noinput
    
8. Run south migrations (optional)
----------------------------------

Should happen automatically at deployment see stackato.yml file for more details.
*I had to run more then once since it was killed the first time. Maybe it took too long?*

    $ stackato run myblog python mycms/manage.py migrate --noinput
    
9. Collect the static files (optional)
--------------------------------------

Should happen automatically at deployment see stackato.yml file for more details.

    $ stackato run myblog python mycms/manage.py collectstatic --noinput
    
10. Create the django admin account
-----------------------------------

Make sure you replace the variables with your values.

    $ stackato run myblog python mycms/manage.py createsuperuser --username=admin --email=admin@example.com --noinput
    
11. Change the password for the admin user
------------------------------------------

Pick a more secure password then the example I have here. 
(notice it is changepassword2 not changepassword)

    $ stackato run myblog python mycms/manage.py changepassword2 admin secret123P@ssw0rd!

12. Open up the url in your browser
-----------------------------------

When you open up the URL that you picked when you deployed in your browser you should find the DjangoCMS pony welcome page. If not, try debugging using some of the tips below.

------------------------
Other Useful Information
------------------------

Starting an application if it isn't running
-------------------------------------------

    $ stackato start myblog
    
Restarting an application
-------------------------

    $ stackato restart myblog
    
Stopping an application
-----------------------

    $ stackato stop myblog

Updating application after it is already deployed
-------------------------------------------------

    $ stackato update myblog
    
Find out how many instances you have running
--------------------------------------------

    $  stackato stats myblog
    
Find out which apps you have installed, and their status
--------------------------------------------------------

    $ stackato apps

Find out what logs you have for your applications
-------------------------------------------------

    $ stackato files myblog logs

Viewing logs for your app
-------------------------
    
    $ stackato logs myblog --all
    
Running cat on a particular log file
------------------------------------
    
    $ stackato run myblog cat ../logs/myapp-err.log
    
-----
Links
-----
- My Blog post describing these steps in more detail: http://KenCochrane.net
- Stackato Client command reference: http://docs.stackato.com/commands.html#command-ref-client
- stackato.yml reference: http://docs.stackato.com/client.html#configure-stackato-yml
- Stackato quick start guide: http://docs.stackato.com/quick-start.html
- Stackato Sandbox Ground Rules, Content Policy and Quotas: http://docs.stackato.com/sandbox.html
- ActiveState Account page: https://account.activestate.com/
- pip : http://www.pip-installer.org/
- git : http://git-scm.com/


My other articles related to PAAS:
----------------------------------
- `My Experiences with ep.io <http://kencochrane.net/blog/2011/04/my-experiences-with-epio/>`_ 
- `AppHosted.com Django Hosting Service Review <http://kencochrane.net/blog/2011/05/apphosted-com-django-hosting-review/>`_ 
- `My Day in Gondor.io <http://kencochrane.net/blog/2011/04/my-day-gondorio/>`_
- `Deploying my Django application to DotCloud.com <http://kencochrane.net/blog/2011/04/deploying-my-django-application-to-dotcloud/>`_
- `DjangoZoom.com Review <http://DjangoZoom.com>`_
- `Django hosting roundup <http://kencochrane.net/blog/2011/06/django-hosting-roundup-who-wins/>`_
- `Installing DjangoCMS on Heroku in 13 easy steps <http://kencochrane.net/blog/2011/12/installing-djangocms-on-heroku-in-13-easy-steps/>`_
- `Installing DjangoCMS on dotCloud in 12 easy steps <http://kencochrane.net/blog/2011/12/installing-djangocms-dotcloud-12-easy-steps/>`_
- `Developers guide to Running Django Applications on Heroku <http://kencochrane.net/blog/2011/11/developers-guide-for-running-django-apps-on-heroku/>`_
- `Installing a Django application on Red Hat's OpenShift PAAS <http://kencochrane.net/blog/2012/01/installing-django-application-on-openshift/>`_