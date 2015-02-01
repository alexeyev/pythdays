The palest ink is better than the best memory.

One can 
* load one's friends' birthdates, 
* do necessary stuff using Excel or Calc or whatever,
* import modified dates as yearly events into one's calendar
with 2 bloody scripts.

# load.py

This is what you may need:
```python
import json
from urllib2 import *
```

So you call
```
$ python load.py 1
```
and you get `1.csv` with all birthdays one can grab via open API. Enjoy.

# save.py

Well, you have to go through some bullshit to succeed.

Firstly, create your own project via [Google Dev Console](http://console.developers.google.com).

Secondly, get some keys and ids:
## APIS & auth / Credentials > OAuth / Create new Client ID / Installed application
## APIS & auth / Credentials > Public API access / Create new Key

Thirdly, [create a brand new calendar](https://www.google.com/calendar/). You know how to do it.

Then fill parameters at `example_credentials.py` config and rename it to `credentials.py`.

Yet more stuff to be done:

Execute whichever you like. Either
```
easy_install --upgrade google-api-python-client
```
or
```
pip install --upgrade google-api-python-client
```

I'm not sure if we're done with it, maybe not yet: 

```python
import httplib2
from oauth2client.file import Storage
from oauth2client.client import OAuth2WebServerFlow
from oauth2client.tools import run

from credentials import *
from apiclient.discovery import build
```

Then say
```
$ python save.py imported_data_of_the_same_format.csv Europe/Moscow
```

Yes, a timezone from [IANA TZD](http://en.wikipedia.org/wiki/Category:Tz_database).

PROFIT!