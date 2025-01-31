---
title: swagger
description: 
published: true
date: 2024-10-31T15:21:51.175Z
tags: 
editor: markdown
dateCreated: 2024-10-31T15:21:48.107Z
---

# Swagger

### Quick Start

## 1. Authenticate

Before accessing any service, an authentication phase is required at the following link:

```
/restapi/auth/authenticate2
```

![](authenticate2.jpg)

To authenticate, simply:

1. Expand the link,
2. Click on the "Try it out" button in the top right corner,
3. Enter your login/password in the "body" field as follows:

![](authenticate2_2.jpg)

Then, to validate the authentication, click on the "Execute" button at the bottom of the screen.

Once authentication is successful, the following screen appears:

The parts to consider are:

- **Curl**: allows you to execute the service directly using the console without going through the web interface.
- **Response body**: contains the token generated during the invocation of this service, which can also be generated using the command above.

## 2. Add the "Modify Header" Extension

*To test from your browser*

This section explains how to use the generated token to continue using our web services from a browser.  
First, you need to download a "Modify Header" extension for your browser.  
(For our example, we will use the Firefox browser, and the download link is: https://addons.mozilla.org/fr/firefox/addon/modify-headers/)  
To verify that the plugin has been added to the browser, this icon should appear in the top right corner of the browser.

![](quickStart-swagger-2-icon.png)

Once the extension is added, click on "Open Modify Headers" and enter the following information:

1. **X-Auth-Token**
2. The token retrieved previously.

![](quickStart-swagger-3-headers-notes.jpg)

*Note: After entering these parameters for the first time, each time you authenticate or after the token expires, you need to generate a new token by reconnecting and modifying the header, then clicking on "Edit".*

## 3. Build a Request

A request to the REST API includes the basic element shown in the table below and may also contain specific parameters:

| Element | Example/Value | Description |
| --- | --- | --- |
| **Base URL** | https://v3.oceansystem.com/ocean-3.0.0/apidocs | Production environment |
| **Specific URL (extension of the base URL)** | /restapi/materiel |  |
| **Resource** | /list/positionBetween | Specify request details via query parameters |
| **Format** | Supported formats: • JSON |  |
| **Token** | &token={token} | Replace with your unique token |
