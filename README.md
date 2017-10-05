
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
  # https://arcane-caverns-87919.herokuapp.com/
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


# ERROR

raceback (most recent call last):
  File "/home/fft/.virtualenvs/learning-flask/lib/python2.7/site-packages/flask/app.py", line 1997, in __call__
    return self.wsgi_app(environ, start_response)
  File "/home/fft/.virtualenvs/learning-flask/lib/python2.7/site-packages/flask/app.py", line 1985, in wsgi_app
    response = self.handle_exception(e)
  File "/home/fft/.virtualenvs/learning-flask/lib/python2.7/site-packages/flask/app.py", line 1540, in handle_exception
    reraise(exc_type, exc_value, tb)
  File "/home/fft/.virtualenvs/learning-flask/lib/python2.7/site-packages/flask/app.py", line 1982, in wsgi_app
    response = self.full_dispatch_request()
  File "/home/fft/.virtualenvs/learning-flask/lib/python2.7/site-packages/flask/app.py", line 1614, in full_dispatch_request
    rv = self.handle_user_exception(e)
  File "/home/fft/.virtualenvs/learning-flask/lib/python2.7/site-packages/flask/app.py", line 1517, in handle_user_exception
    reraise(exc_type, exc_value, tb)
  File "/home/fft/.virtualenvs/learning-flask/lib/python2.7/site-packages/flask/app.py", line 1612, in full_dispatch_request
    rv = self.dispatch_request()
  File "/home/fft/.virtualenvs/learning-flask/lib/python2.7/site-packages/flask/app.py", line 1598, in dispatch_request
    return self.view_functions[rule.endpoint](**req.view_args)
  File "/home/fft/dev/learning-flask/routes.py", line 30, in signup
    db.session.commit()
  File "/home/fft/.virtualenvs/learning-flask/lib/python2.7/site-packages/sqlalchemy/orm/scoping.py", line 157, in do
    return getattr(self.registry(), name)(*args, **kwargs)
  File "/home/fft/.virtualenvs/learning-flask/lib/python2.7/site-packages/sqlalchemy/orm/session.py", line 906, in commit
    self.transaction.commit()
  File "/home/fft/.virtualenvs/learning-flask/lib/python2.7/site-packages/sqlalchemy/orm/session.py", line 461, in commit
    self._prepare_impl()
  File "/home/fft/.virtualenvs/learning-flask/lib/python2.7/site-packages/sqlalchemy/orm/session.py", line 441, in _prepare_impl
    self.session.flush()
  File "/home/fft/.virtualenvs/learning-flask/lib/python2.7/site-packages/sqlalchemy/orm/session.py", line 2177, in flush
    self._flush(objects)
  File "/home/fft/.virtualenvs/learning-flask/lib/python2.7/site-packages/sqlalchemy/orm/session.py", line 2297, in _flush
    transaction.rollback(_capture_exception=True)
  File "/home/fft/.virtualenvs/learning-flask/lib/python2.7/site-packages/sqlalchemy/util/langhelpers.py", line 66, in __exit__
    compat.reraise(exc_type, exc_value, exc_tb)
  File "/home/fft/.virtualenvs/learning-flask/lib/python2.7/site-packages/sqlalchemy/orm/session.py", line 2261, in _flush
    flush_context.execute()
  File "/home/fft/.virtualenvs/learning-flask/lib/python2.7/site-packages/sqlalchemy/orm/unitofwork.py", line 389, in execute
    rec.execute(self)
  File "/home/fft/.virtualenvs/learning-flask/lib/python2.7/site-packages/sqlalchemy/orm/unitofwork.py", line 548, in execute
    uow
  File "/home/fft/.virtualenvs/learning-flask/lib/python2.7/site-packages/sqlalchemy/orm/persistence.py", line 156, in save_obj
    base_mapper, states, uowtransaction
  File "/home/fft/.virtualenvs/learning-flask/lib/python2.7/site-packages/sqlalchemy/orm/persistence.py", line 279, in _organize_states_for_save
    states):
  File "/home/fft/.virtualenvs/learning-flask/lib/python2.7/site-packages/sqlalchemy/orm/persistence.py", line 1105, in _connections_for_states
    connection = uowtransaction.transaction.connection(base_mapper)
  File "/home/fft/.virtualenvs/learning-flask/lib/python2.7/site-packages/sqlalchemy/orm/session.py", line 294, in connection
    return self._connection_for_bind(bind, execution_options)
  File "/home/fft/.virtualenvs/learning-flask/lib/python2.7/site-packages/sqlalchemy/orm/session.py", line 392, in _connection_for_bind
    conn = self._parent._connection_for_bind(bind, execution_options)
  File "/home/fft/.virtualenvs/learning-flask/lib/python2.7/site-packages/sqlalchemy/orm/session.py", line 403, in _connection_for_bind
    conn = bind.contextual_connect()
  File "/home/fft/.virtualenvs/learning-flask/lib/python2.7/site-packages/sqlalchemy/engine/base.py", line 2112, in contextual_connect
    self._wrap_pool_connect(self.pool.connect, None),
  File "/home/fft/.virtualenvs/learning-flask/lib/python2.7/site-packages/sqlalchemy/engine/base.py", line 2151, in _wrap_pool_connect
    e, dialect, self)
  File "/home/fft/.virtualenvs/learning-flask/lib/python2.7/site-packages/sqlalchemy/engine/base.py", line 1465, in _handle_dbapi_exception_noconnection
    exc_info
  File "/home/fft/.virtualenvs/learning-flask/lib/python2.7/site-packages/sqlalchemy/util/compat.py", line 203, in raise_from_cause
    reraise(type(exception), exception, tb=exc_tb, cause=cause)
  File "/home/fft/.virtualenvs/learning-flask/lib/python2.7/site-packages/sqlalchemy/engine/base.py", line 2147, in _wrap_pool_connect
    return fn()
  File "/home/fft/.virtualenvs/learning-flask/lib/python2.7/site-packages/sqlalchemy/pool.py", line 387, in connect
    return _ConnectionFairy._checkout(self)
  File "/home/fft/.virtualenvs/learning-flask/lib/python2.7/site-packages/sqlalchemy/pool.py", line 766, in _checkout
    fairy = _ConnectionRecord.checkout(pool)
  File "/home/fft/.virtualenvs/learning-flask/lib/python2.7/site-packages/sqlalchemy/pool.py", line 516, in checkout
    rec = pool._do_get()
  File "/home/fft/.virtualenvs/learning-flask/lib/python2.7/site-packages/sqlalchemy/pool.py", line 1138, in _do_get
    self._dec_overflow()
  File "/home/fft/.virtualenvs/learning-flask/lib/python2.7/site-packages/sqlalchemy/util/langhelpers.py", line 66, in __exit__
    compat.reraise(exc_type, exc_value, exc_tb)
  File "/home/fft/.virtualenvs/learning-flask/lib/python2.7/site-packages/sqlalchemy/pool.py", line 1135, in _do_get
    return self._create_connection()
  File "/home/fft/.virtualenvs/learning-flask/lib/python2.7/site-packages/sqlalchemy/pool.py", line 333, in _create_connection
    return _ConnectionRecord(self)
  File "/home/fft/.virtualenvs/learning-flask/lib/python2.7/site-packages/sqlalchemy/pool.py", line 461, in __init__
    self.__connect(first_connect_check=True)
  File "/home/fft/.virtualenvs/learning-flask/lib/python2.7/site-packages/sqlalchemy/pool.py", line 651, in __connect
    connection = pool._invoke_creator(self)
  File "/home/fft/.virtualenvs/learning-flask/lib/python2.7/site-packages/sqlalchemy/engine/strategies.py", line 105, in connect
    return dialect.connect(*cargs, **cparams)
  File "/home/fft/.virtualenvs/learning-flask/lib/python2.7/site-packages/sqlalchemy/engine/default.py", line 393, in connect
    return self.dbapi.connect(*cargs, **cparams)
  File "/home/fft/.virtualenvs/learning-flask/lib/python2.7/site-packages/psycopg2/__init__.py", line 130, in connect
    conn = _connect(dsn, connection_factory=connection_factory, **kwasync)
OperationalError: (psycopg2.OperationalError) fe_sendauth: no password supplied