# Django study

## Prerequisites

- Python >= 3.7.0

## Installation

### Django installation

```bash
$ sudo apt install python-django

# django-admin startproject <proj-name>
$ django-admin startproject dtest
```

### MySQL installation (localhost)

``` bash
$ sudo apt install mysql-server mysql-client
```

#### Create user
``` bash
$ sudo mysql -u root -p

# mysql> create user '<user-name>'@'localhost' identified by '<user-password>';
mysql> create user 'xqiik' identified by '******';
```
> OK without "@'localhost'"

#### Add setting for encoding
/etc/mysql/mysql.conf.d/mysqld.cnf
``` text
character-set-server = utf8
```

#### Restart MySQL
``` bash
$ sudo systemctl restart mysql
```

#### Create Database
```sql
# mysql> create database <db-name>;
mysql> create database dtest;

# mysql> grant all on <db-name>.* to <user-name>@localhost identified by '<user-password>';
mysql> grant all on dtest.* to xqiik@localhost identified by '******';
```

### Setting Django
settings.py
``` python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': '<db-name>',
        'USER': '<user-name>',
        'PASSWORD': '<user-password>',
    }
}
:
# LANGUAGE_CODE = 'en-us'
LANGUAGE_CODE = 'ja'

# TIME_ZONE = 'UTC'
TIME_ZONE = 'Asia/Tokyo'
```
manage.py
``` python
import pymysql # append

def main():
    pymysql.install_as_MySQLdb() # append

    os.environ.setdefault('DJANGO_SETTINGS_MODULE', '<proj-name>.settings')
    :
```

### PyMySQL Installation
``` bash
$ pip install PyMySQL
```

### Start Django server
``` bash
$ python manage.py migrate
$ python manage.py createsuperuser
ユーザー名 (leave blank to use 'kurosaki'): admin
メールアドレス: kurosaki4pers@gmail.com
Password:
Password (again):
Superuser created successfully.
$ python manage.py runserver
```

## License

&copy; 2021 [Ken Kurosaki](https://github.com/quinpallet).  
This project is [MIT](https://github.com/quinpallet/django_study/blob/master/LICENSE) licensed.
