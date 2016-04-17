-- Commands
python -m venv .<project_name>
source .<project_name>/bin/activate
which python

-- Install
pip install --upgrade pip
pip install django
pip install python-decouple
pip install dj-database-url
pip install dj-static

-- Run server
python manage.py
alias manage='python $VIRTUAL_ENV/../manage.py'
manage runserver

-- Create app
django-admin startproject eventex .
cd <project_name>
manage startapp core

-- Configs
add 'eventex.core', INSTALLED_APPS settings.py
add def home(request): views.py
add url(r'^$', 'eventex.core.views.home') urls.py
add gunicorn==19.4.1 requirements.txt
add psycopg2=2.6.1 requirements.txt
add web: gunicorn eventex.wsgi --log-file - Procfile


-- Server Repositories
git clone https://github.com/luizmarceloschmitt/eventex-curso.git
git remote -v
heroku login
heroku apps:create site-sysdomotic
https://eventex-luizmarcelo.herokuapp.com/ | https://git.heroku.com/eventex-luizmarcelo.git
heroku plugins:install git://github.com/ddollar/heroku-config.git
heroku config:push
heroku config

-- Deploy
pip freeze
pip freeze > requirements.txt
touch Procfile /
touch runtime.txt /
git push heroku master --force
