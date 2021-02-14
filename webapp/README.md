# #NotTheOnlyOne WebApp

This is based on flask-base:
https://github.com/hack4impact/flask-base

## Notes

* Need to write your own config.py! See the sample config.py included
* You will need a config.env - example one below (USER_* is for the first user that is not an admin):
```
SECRET_KEY=<addsomething here>
MAIL_USERNAME=SendgridUsername
MAIL_PASSWORD=SendgridPassword
ADMIN_EMAIL=<addsomething here>
ADMIN_PASSWORD=<addsomething here>
DATABASE_URL=data-dev.sqlite
FLASK_CONFIG=development
ADMIN_FIRSTNAME=<addsomething here>
ADMIN_LASTNAME=<addsomething here>
USER_EMAIL=<addsomething here>
USER_FIRSTNAME=<addsomething here>
USER_LASTNAME=<addsomething here>
USER_PASSWORD=<addsomething here>
```

Also need to setup
 >>> import nltk
  >>> nltk.download('stopwords')

and


  >>> import nltk
  >>> nltk.download('punkt')

## Setup and running

Install conda (if needed):

```bash
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
```

Setup conda env and python modules:

```bash
conda create -n ntoo -c conda-forge python=3 redis mysqlclient pymysql
conda activate ntoo
pip install -r requirements.txt
```

Setup db with initial data:

```bash
python manage.py recreate_db && python manage.py setup
```

Run:

```bash
honcho start -e config.env -f Local

or 

python manage.py runserver -h 0.0.0.0

or

conda activate ntoo
gunicorn --bind 0.0.0.0:5000 wsgi 

```
