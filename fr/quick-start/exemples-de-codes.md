---
title: exemples-de-codes
description: 
published: true
date: 2024-10-31T14:45:29.845Z
tags: 
editor: markdown
dateCreated: 2024-10-24T13:15:45.199Z
---

# Exemples de codes

### Quick Start

Une connexion via Python est nécessaire pour visualiser cet exemple :
```python
#!/usr/bin/python
# -- coding:Utf-8 --

import sys
import requests
import json

srv = "v3.oceansystem.com"
prt = 443
token = None

def send_recv_post(data, met):
    headers = {'Content-Type': 'application/json'}
    r = requests.post(f"https://{srv}:{prt}/ocean-3.0.0/restapi/{met}", json=data, headers=headers)
    print(r.text)
    print(r.content)
    print(r.json())
    print(r.status_code)
    return r

def getToken():
     # preparation de la requete auth
    oceanuser = "XXXXXXX"
    oceanpass = "XXXXXXX"
    token = None
    dataToSend = {"login": oceanuser, "password": oceanpass}
    
    r = send_recv_post(dataToSend, "auth/authenticate2")
    
    if r.status_code == 200:
        dataJson = r.json()
        print(dataJson['token'])
        token = dataJson['token']
        return True
    else:
        token = None
        return False

if getToken():
    print("Connected")
```
