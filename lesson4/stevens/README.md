# Start a Django project

pi@raspberrypi:~ $ django-admin startproject stevens

pi@raspberrypi:~ $ cd stevens

pi@raspberrypi:~/stevens $ ls

manage.py  stevens

# Start a Django app

pi@raspberrypi:~/stevens $ python3 manage.py startapp myapp

pi@raspberrypi:~/stevens $ ls

manage.py  myapp  stevens

# Create MySQL database

pi@raspberrypi:~ $ sudo mysql -u root -p

Enter password: PASSWORD

MariaDB [(none)]> use mysql

MariaDB [mysql]> select user, host from mysql.user;

MariaDB [mysql]> create user pi@localhost identified by 'PASSWORD';

MariaDB [mysql]> show databases;

MariaDB [mysql]> create database stevens;

MariaDB [mysql]> grant all privileges on stevens.* to pi@localhost;

MariaDB [mysql]> quit

# Edit settings.py in ~/stevens/stevens

# Follow ~/iot/lesson4/stevens/settings.txt

# Remember to change PASSWORD for MySQL user

pi@raspberrypi:~/stevens $ cd stevens

pi@raspberrypi:~/stevens/stevens $ nano settings.py

# Copy urls.py to ~/stevens/stevens

pi@raspberrypi:~/stevens/stevens $ cp ~/iot/lesson4/stevens/urls.py .

pi@raspberrypi:~/stevens/stevens $ cd ..

# Copy admin.py, models.py, and views.py to ~/stevens/myapp

pi@raspberrypi:~/stevens $ cd myapp

pi@raspberrypi:~/stevens/myapp $ cp ~/iot/lesson4/stevens/admin.py .

pi@raspberrypi:~/stevens/myapp $ cp ~/iot/lesson4/stevens/models.py .

pi@raspberrypi:~/stevens/myapp $ cp ~/iot/lesson4/stevens/views.py .

# Copy index.html and static files

pi@raspberrypi:~/stevens/myapp $ mkdir static templates

pi@raspberrypi:~/stevens/myapp $ cd templates

pi@raspberrypi:~/stevens/myapp/templates $ mkdir myapp

pi@raspberrypi:~/stevens/myapp/templates $ cd myapp

pi@raspberrypi:~/stevens/myapp/templates/myapp $ cp ~/iot/lesson4/stevens/index.html .

pi@raspberrypi:~/stevens/myapp/templates/myapp $ cd ~/stevens/myapp/static

pi@raspberrypi:~/stevens/myapp/static $ cp ~/iot/lesson4/stevens/favicon.ico .

pi@raspberrypi:~/stevens/myapp/static $ mkdir myapp

pi@raspberrypi:~/stevens/myapp/static $ cd myapp

pi@raspberrypi:~/stevens/myapp/static/myapp $ cp ~/iot/lesson4/stevens/*css .

pi@raspberrypi:~/stevens/myapp/static/myapp $ cp ~/iot/lesson4/stevens/*js .

pi@raspberrypi:~/stevens/myapp/static/myapp $ cd ~/stevens

# After the first time, skip these three steps if no changes

pi@raspberrypi:~/stevens $ python3 manage.py makemigrations myapp

pi@raspberrypi:~/stevens $ python3 manage.py migrate

pi@raspberrypi:~/stevens $ python3 manage.py createsuperuser

Username (leave blank to use 'pi'):

Email address: EMAIL_ADDRESS

Password: PASSWORD

Password (again): PASSWORD

Superuser created successfully.

pi@raspberrypi:~/stevens $ python3 manage.py runserver

# Open the Chromium browser on Raspberry Pi via VNC Viewer

# Go to http://127.0.0.1:8000/admin

# Login with Django administration username (pi) and password

# Click temperature data to add 

# Date and time in YYYY-MM-DD HH:MM:SS

# Temperature in Fahrenheit

# Latitude 40.7451

# Longitude -74.0255

# Click SAVE

# View app at http://127.0.0.1:8000
