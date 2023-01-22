# recipe-app-api
dockeer hub, log in before running job

create github project, public, add readme file, add .gitignore choose python, 
create repository

cd /udemy, git clone https://github.com/jonrynn/recipe-app-api.git

To create docker hub token to use with GitHub:
docker hub, go to jonrynn, account settings, security, create an access token with name recipe-app-api, generate, copy token

go back to github project, settings, secrets and variables, actions, new secret

first secret has name DOCKERHUB_USER, value  of user of docker hub, jonrynn, click add secret, go to actions secrets page, click on new reposity secret, then add a new secret DOCKERHUB_TOKEN, secret is copied token, add secret, should see two secrets.  This lets us log in to dockeer hub as authenticated user so don't worry about limits on docker hub.

to set up docker to use django:
cd recipe-app-api
create requirements.txt in vscode
 create dockerfile
 create .dockerignore file
 create empty app directory that was used in dockerfile

 to create docker container, docker build . (in root, recipe-app-api)
 now, create docker-compose.yml in root
 so now can use docker-compose build instead of docker build .
 add flake8 as linting tool, docker-compose run --rm app sh -c "flake8"
 for linting, create requirements.dev.txt
 add .flake8 config file in app folder
 to run flake8, docker-compose run --rm app sh -c "flake8"
 to run django, docker-compose run --rm app sh -c "django-admin startproject app ."
 to run new django project, to see on browser, docker-compose up, then go to 127.0.1.1:8000

 for github actions, create .github/workflows/checks.yml

for testing, python manage.py test

need to install postgres handler, which is a mess, because we need specific dependencies
in order to compile psycop2 or whatever, first update dockerfile, then requirements.txt,
then docker-compose build to rebuild the whole thing

update settings.xml for postgres and add import os, then create core app
docker-compose run --rm app sh -c "python manage.py startapp core"

 for setup in aws:
 check for docker
 after git clone, docker-compose build, then docker-compose run --rm app sh -c "django-admin startproject app .", look on browser
 add core to installed_apps in settings.py
 in core, set up management/commands directory -- any py files here will be
 used by django when you call manage.py, eg wait_for_db

look at his link to docker to install on linux
for AWS, go to this page to install Docker: 
[https://docs.docker.com/engine/install/ubuntu/](https://docs.docker.com/engine/install/ubuntu/#install-using-the-convenience-script)
use the convenience script, 
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh

to install docker-compose, using https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-compose-on-ubuntu-20-04
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker-compose --version






