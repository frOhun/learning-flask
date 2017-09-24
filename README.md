
1)  mkproject -p python2 learning-flask 
 75  pip install flask
 76  heroku login
 77  ll
 78  pip install flask-wtf flask_sqlalchemy
   89  git init
   90  git status
   91  git add routes.py
   92  gs
   93  git status
   94  git add README.md static/ templates/
   95  git status
   96  git commit -m "Initial commit"
   97  git remote add origin https://github.com/frOhun/learning-flask.git
   98  git push -u origin master
   99  pip install gunicorn
  100  pip freeze > requirements.txt
  102  heroku create 
  103  git add Profile requirements.txt
  104  git commit -m "Heroku config"
  107  git add Procfile
  119  git commit -m "Heroku config"
  120  git push heroku master
  121  heroku open
  122  git push origin master
  123  git status
  124  git add routes.py templates/*.html
  125  git status
  126  git commit -m "About page"
  127  git push origin master
  130  git push heroku master
  
  131  heroku create 
  132  git push heroku master
  133  pip freeze > requirements.txt
  134  git add Procfile
  135  git push heroku master
  136  git status
  137  git commit -m "Heroku config"
  138  git status
  139  git push heroku master
  129  heroku open
  
  145* sudo -u postgres createuser fft
  150* sudo -u postgres psql
  151* psql -d learningflask

#------------------- CREATE DB -------------------------------
(learning-flask) dev/learning-flask [master] » sudo -u postgres createuser fft        
(learning-flask) dev/learning-flask [master] » psql                           
psql: FATAL:  database "fft" does not exist
(learning-flask) dev/learning-flask [master] » _rake db:create learningflask
_rake:8: no matches found: (--system,-g)--system[using system wide (global) rakefiles (usually ~/.rake/*.rake)]
(learning-flask) dev/learning-flask [master] » _rake db:create              
_rake:8: no matches found: (--system,-g)--system[using system wide (global) rakefiles (usually ~/.rake/*.rake)]
(learning-flask) dev/learning-flask [master] » man psql 
(learning-flask) dev/learning-flask [master] » sudo -u postgres psql          
psql (9.5.8)
Type "help" for help.

postgres=# create database learningflask;
CREATE DATABASE
postgres=# \q
(learning-flask) dev/learning-flask [master] » psql -d learningflask        


learningflask=> CREATE TABLE users (
uid serial PRIMARY KEY,
firstname VARCHAR(100) not null,
lastname VARCHAR(100) not null,
email VARCHAR(120) not null unique,
pwdhash VARCHAR(100) not null
);
CREATE TABLE
learningflask=> insert into users (firstname, lastname, email, pwdhash) VALUES ('Ferenc', 'Forrai', 'ferenc.forrai@gmail.com', 'learning-flask');
INSERT 0 1
learningflask=> select * from users
learningflask-> ;
 uid | firstname | lastname |          email          |    pwdhash     
-----+-----------+----------+-------------------------+----------------
   1 | Ferenc    | Forrai   | ferenc.forrai@gmail.com | learning-flask
(1 row)

#-------------------  -------------------------------


