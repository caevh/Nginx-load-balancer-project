# load balncer project using flask and nginx

Step 1 - getting the flask app working:
- Create a project folder e.g. load-balancer.
- Create a .py file for the hello world flask code, e.g. app.py. Note: Do not call your .py file flask.py.
- At this point you may or may not want to test the app in a virtual .env enviroment.
- Paste the code from app.py above into your app.py. 
- You now need to tell your terminal the application to work with by exporting the FLASK_APP enviroment variable. 

export FLASK_APP=app.py

flask run

- Alternative command if above doesn't work:

export FLASK_APP=app.py

python -m flask run

- You should now have a working hello world flask app.py file. 

Step 2 - Getting flask to work with a Dockerfile
