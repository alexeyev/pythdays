_The palest ink is better than the best memory._

One can 
* load one's friends' birthdates, 
* do necessary stuff using Excel or Calc or whatever,
* import modified dates as yearly events into one's calendar

with 2 bloody scripts and some sweat due to the necessity of authorization.

## load.py

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

## save.py

Well, you have to go through some bullshit to succeed.

* Create your own project via [Google Dev Console](http://console.developers.google.com).
* Get some keys and ids:
 
Client ID + client secret

`APIs & auth / Credentials > OAuth / Create new Client ID / Installed application`

Developer key (aka API key)

`APIs & auth / Credentials > Public API access / Create new Key`

* [Create a brand new calendar](https://www.google.com/calendar/). You know how to do it.

* Fill parameters at `example_credentials.py` config and rename it to `credentials.py`.

* Install `google-api-python-client`:

Execute 
```
pip install --upgrade google-api-python-client
```

* I'm not sure if we're done with it, maybe not yet: 

```python
import httplib2
from oauth2client.file import Storage
from oauth2client.client import OAuth2WebServerFlow
from oauth2client.tools import run

from credentials import *
from apiclient.discovery import build
```
Either sort it out by yourself or write to me.


Then say
```
$ python save.py imported_data_of_the_same_format.csv Europe/Moscow
```

Yes, you need a timezone from [IANA TZD](http://en.wikipedia.org/wiki/Category:Tz_database).
`Europe/Moscow` is used if no value is provided.

## Bugs, improvements

In case of trouble of whatever -- feel free to write to me or create a new issue here on GitHub.