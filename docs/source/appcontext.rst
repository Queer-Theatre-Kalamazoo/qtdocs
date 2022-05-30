Application Context
======
.. _appcontext:


.. epigraph:: Here I will demonstrate one solution to a problem I frequently encountered: circular imports. For this example we will be using Flask-Mail, but the process should remain the same for any extension that needs an object to be initialized to the application context.

.. note:: The following assumes a typical application factory pattern is being used. See https://hackersandslackers.com/flask-application-factory/\.

***************
Solution
***************

``__init__.py``

.. code-block:: python

  def init_app():
  	app = Flask(__name__)
    
    # Config block
    
    mail = Mail() # Create objects before initializing them
    
    with app.app_context(): # Give all the things to app
    
    	mail.init_app(app) # Initialize all the things
      app.mail = mail # Make all the things accessible from current_app.thing
      
      return app
        
``otherfile.py``

.. code-block:: python

    from flask import current_app
    from flask_mail import Message
    
    message = Message('Subject', 'Recipients')
    message.body = 'Body'
    message.html = 'HTML Body'
    
    current_app.mail.send(message)
