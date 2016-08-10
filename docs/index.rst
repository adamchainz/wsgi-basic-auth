.. WSGI Basic Auth documentation master file, created by
   sphinx-quickstart on Wed Aug 10 17:06:14 2016.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Welcome to WSGI Basic Auth's documentation!
===========================================

Really simple wsgi middleware to provide basic http auth. It is intented to
work with environment variables. This makes it simple to use in a docker 
context.

Using this module is really simple.  In Django for example edit the wsgi.py
file and add the following to the end of the file.

.. code-block:: python

  from wsgi_basic_auth import BasicAuth 
  application = BasicAuth(application) 
  
Now run docker with the env variable WSGI_AUTH_CREDENTIALS=foo:bar and you have
to authenticate with username foo and password bar. Multiple credentials are
separated with a | (pipe) character.

To exclude specific paths for healthchecks (e.g. the Amazon ELB healthchecks)
specifcy the environment variable WSGI_AUTH_EXCLUDE_PATHS=/api/healthchecks.
Here multiple paths can be separated with the ; char.


Installation 
============

You can install the latest version using pip::

    pip install wsgi-basic-auth


Options
=======

.. autoclass:: wsgi_basic_auth.BasicAuth