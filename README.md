# REquirements
- If installing on Ubuntu20 which has no python2.7 you need to install python2.7 and set it to be default python version
- FOllow instructions :
  https://stackoverflow.com/questions/61981156/unable-to-locate-package-python-pip-ubuntu-20-04
  https://stackoverflow.com/questions/17309288/importerror-no-module-named-requests?rq=1
- Install all the pip modules that are required for shinken
   1   │ CherryPy
   2   │ pycurl
   3   │ importlib
   4   │ pbr
   5   │ bottle
   6   │ pymongo
   7   │ passlib
   8   │ requests
- pip install shinken or if you install from source you can do  python setup.py install
- start shinken using the docs
- configure webui2 module based onthe docs
- Logs are not in human readble format so you will need to use following perl hack
perl -pe's/([(\d.)]+)/localtime $1/e;'

Default port for shinken is 7767

Refer:
https://www.howtoforge.com/tutorial/server-monitoring-with-shinken-on-ubuntu-16-04/
https://www.unixmen.com/install-shinken-debian/

Step 2: COnfigure snmp on hosts that needs to be monitored:
centos: https://kifarunix.com/install-and-configure-snmp-on-centos-8/
windows: https://www.sysnettechsolutions.com/en/enable-snmp-on-windows-10/


Step 3: Graphite:
ubuntu: 
https://computingforgeeks.com/how-to-install-and-configure-graphite-on-ubuntu-18-04/
centos:
https://www.vultr.com/docs/how-to-install-and-configure-graphite-on-centos-7

 install graphite-web graphite-carbon
 install mariadb-server mariadb-client

 Once mariadb is installed secure mysql install
 ```sudo mysql_secure_installation

 By Default mariadb will use unix_socket based authentication thus any user in the local machine will have mariadb access, however in order to change that to password based you need to login into mariadb as follows and update the authentication plugin
 ```sudo mysql -u root 

```
 ALTER USER root@localhost IDENTIFIED VIA mysql_native_password;
 SET PASSWORD = PASSWORD('foo');

 Ref: https://mariadb.com/kb/en/authentication-plugin-unix-socket/
 TO revert:
 ```UPDATE mysql.user SET plugin = '' WHERE plugin = 'unix_socket';
```FLUSH PRIVILEGES;

https://stackoverflow.com/questions/43379892/mariadb-cannot-login-as-root

Install following packages:

sudo apt-get install python-MySQLdb build-essential python-dev libmysqlclient-dev

sudo PYTHONPATH=/opt/graphite/webapp/ django-admin.py migrate --settings=graphite.settings --run-syncdb
https://github.com/graphite-project/graphite-web/issues/2391
