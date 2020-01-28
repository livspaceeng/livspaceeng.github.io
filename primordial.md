# Primordial 

A template for making a standalone frontend in v2.

## Introduction
If you are looking for MFE's this is not the right place. This doc explains how to setup a standalone frontend with authentication and api integration for the v2 suite of frontend apps in livspace. The app you create by following this guide will be deployed on firebase under its own domain name. You might run some mfe's inside it if you want to. 

## Getting started
Clone the repository, and make sure you checkout the `trimdown` branch.
```bash
git clone https://gautam1168@bitbucket.org/livspaceeng/primordial.git
git checkout trimdown
npm i
npm run serve
```

Visit [link](http://localhost:8000/login)

## Making changes

1. You should not push to this repository. Instead you should create your own repository and change the remote to point to that. Or just delete the `.git` folder to have a fresh history.
2. You must change the config.json file in the public folder. It would look like this:
```json
{
     "redirectUri": "http://localhost:8000/redirect",
     "clientId": "PRIMORDIAL",
     "openIdConnectUrl": "https://auth.dev.livspace.com",
     "baseUrl": "https://axle.dev.livspace.com",
     "socket": {
         "hostname": "api.dev.livspace.com",
         "path": "/livhome-socket-service/socketcluster/",
         "port": 8080
     },
     "headers": {
         "leadservice": {
             "api-key": "xyzCg7TJMZ8mIPKWjzA5P7HG6obAayMS98jdGV2v"
         }
     }
 }
 ```
 You should go to [bouncer](http://bouncer.dev.livspace.com) and create a new application for your project. In that application you must choose the authentication type to be `None` and put in the redirection link as `http://localhost:8000/redirect`. Once this is done replace the `clientId` in the above snippet with the name of the project you created.

 **WARNING: Do not put any private keys in the config.json file above! This is going to be publically available**

 # Coming soon
 1. How to deploy the app on firebase
 2. Guide on the component library
 For now refer to the [ec-app](https://bitbucket.org/livspaceeng/canvasmonorepo/src/master/packages/ec-app/) for guidance if stuck.
