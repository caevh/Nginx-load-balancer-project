# load balancer project using flask and Nginx

Step 1 - getting the flask app working:
- Create a project folder e.g. load-balancer.
- Create a .py file for the hello world flask code, e.g. app.py. Note: Do not call your .py file flask.py.
- At this point you may, or may not, want to test the app in a virtual .env environment.
- Paste the code from app.py above into your app.py. 
- You now need to tell your terminal the application to work with by exporting the FLASK_APP environment variable. 

export FLASK_APP=app.py

flask run

- Alternative command if above doesn't work:

export FLASK_APP=app.py

python -m flask run

- You should now have a working hello world flask app.py file.



Step 2 - Getting flask to work with a Dockerfile 
- Create a requirements.txt file and input flask. This will be used by the docker file to import flask. 
- create a file called Dockerfile and input the following.

FROM python:3 # using the "python:3" image

COPY . /app  #Copies our current folder, '.', into our container folder '/app'

WORKDIR /app  #It then sets '/app' as our working directory.

RUN pip install -r requirements.txt  #We install our requirements from the .txt file with pip install. 

CMD ["flask", "run", "--host=0.0.0.0"]  #We then give it the "flask run" command along with "--host=0.0.0.0", this makes it publicly available.

- These should be the only 3 files you will need. Dockerfile, app.py, and requirements.txt.
- Now at the terminal run the following commands in the same place your project is located. 

note: if the following commands don't work due to permissions, run sudo in front of them.

docker build -t my_docker_flask:latest .  #Building an image with the tag (--tag, -t) my_docker_flask:latest that includes everything in the current directory, '.'.

docker images ls # Allows us to see the image we just created. 

docker run -p 5000:5000 my_docker_flask:latest  # "-p" specifies the port its is running on. In our Dockerfile we specified "host='0.0.0.0'", so we need to specify which port when using the flask run. 

Your app should now be running in the docker container, accessible at http://0.0.0.0:5000/.  
