How to package gcalcli in a standalone exe using cx_Freeze
==========================================================

1. download source from https://github.com/insanum/gcalcli
2. pip install cx_Freeze
3. pip install six python-dateutil parsedatetime oauth2client google-api-python-client ca_certs_locater encodings
4. move to dir where setup.py is located
5. modify setup.py to include cx_Freeze specific lines (see sample setup_cx_Freeze.py)
6. modify gcalcli\__init.py__ to include own credentials
   __API_CLIENT_ID__ = '407609566767.apps.googleusercontent.com' # __API_CLIENT_ID__ = '232867676714.apps.googleusercontent.com'
   __API_CLIENT_SECRET__ = 'opLkkvC5WUb-D_IFoxPx2Jgk' #__API_CLIENT_SECRET__ = '3tZSxItw6_VnZMezQwC8lUqy'
7. add following lines to cli.py
   # m2: specify the path to certificates (-> current dir)
   import ca_certs_locater
   ca_certs_locater.get = lambda : "cacerts.txt"
8. python setup.py build (change setup.py to other name in case) => exe should be under <main-dir>\build\<architecture>
9. copy cacerts.txt to same dir where exe is

