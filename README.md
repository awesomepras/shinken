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


Refer:
https://www.howtoforge.com/tutorial/server-monitoring-with-shinken-on-ubuntu-16-04/
https://www.unixmen.com/install-shinken-debian/
