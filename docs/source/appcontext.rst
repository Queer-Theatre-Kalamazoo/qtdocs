Application Context
======
.. _appcontext:


.. epigraph:: Here I will demonstrate one solution to a problem I frequently encountered: circular imports. For this example we will be using Flask-Mail, but the process should remain the same for any extension that needs an object to be initialized to the application context.

.. tip:: The following assumes a typical application factory pattern is being used. See https://hackersandslackers.com/flask-application-factory/\.

***************
Solution
***************

``__init__.py``
.. code-block:: python

  def init_app():
  	app = Flask(__name__)
    
    # Create objects before initializing them
    mail = Mail()
    
    # Give all the things to app
    with app.app_context():
    
    	# Initialize all the things
    	mail.init_app(app)
        .....
        
        # Make all the things accessible from current_app.thing
        app.mail = mail
        
        return app
