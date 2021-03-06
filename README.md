# splunk-toolbox

## Version 1.2.0
A better wrapper around the Splunk ITSI Rest API and Splunk Core API for anyone feeling the pain
[Python PyPi PIP package](https://pypi.org/project/splunk-toolbox/)
[Github Repository](https://github.com/gnubyte/splunk-toolbox)


## Intended Runtime & Required Packages

** Python V3.x
** see requirements.txt for requirements

## Installation in python 3

Installation via pip

If pip3 is your default python package installer on the path (for most it references python2's version of pip...)
```
pip install splunk_toolbox
```

If that fails, check your `pip --version` to see which version of python it is using

Additionally try:

```
pip3 install splunk_toolbox
```

## Version table
 - 1.0.0 initial PoC/format
 - 1.1.0 added Post update to ITSI Notable Event Group
 - 1.1.1 bugfix & clarification of requirements for post_update_to_notable_event_group
 - 1.1.2 added handler for status code interpretation to post update to notable event group
 - 1.2.0 added splunk retrieve search jobs and save them as XML to the toolbox

Intended to solve stability issues produced by the product itself.


## Splunk Toolbox Bio

This is a wrapper around the ITSI API. Where the ITSI API is not 
functioning, we are using sftp calls instead or core API.

## Example Uses



#### Retrieve active search jobs from ITSI
```
from splunk_toolbox import splunkInstance

splunk_server = splunkInstance(authPass='mypass')
splunk_server.retrieve_search_jobs(recordSearches=1)
```


#### Post updates to ITSI Notable Event Group


```
from splunk_toolbox import splunkInstance


splunk_server = splunkInstance(authPass='mypass')
payload ={"status":"5"}
splunk_server.post_update_to_notable_event_group(payload=payload, )
```


#### Retrieve all Splunk Core Searches on a given server

if record Searches == 1, a file with the name `recordedSearches.xml` will be generated and saved with todays date and time

```
from splunk_toolbox import splunkInstance

splunk_server = splunkInstance(host='someIP', authPass='PASS')
splunk_server.retrieve_configured_saved_searches(recordSearches=1)
```

