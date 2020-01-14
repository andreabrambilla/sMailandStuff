# sMailandStuff
A web application to test various web features ....

## Features

- oAuth2 and OICD against Azure AD
- Reading email from o365 Graph
- Expose various token related information for user/session
- Exploring cookie beaviour for displaying last time visited on a few pages

## Install and run locally

* Clone repository
* Do `npm install`
* Create `Application registration` in Azure AD
* Update configuration in `./config/config.js`
* Export the following config into the local environment variables 
```
export NODE_ENV=development
export CLIENTSECRET=""
export PORT=3000
export TENANTID=""
export CLIENTID=""
```

* Run application using `npm start`

## Docker

* Build: `docker build -t smailandstuff .`
* Run:

```
docker run -p 3000:3000  \
    --env TENANTID="$TENANTID" \
    --env CLIENTID="$CLIENTID" \
    --env CLIENTSECRET="$CLIENTSECRET" \
    smailandstuff
```

## Cloud Deployment

### Radix

Radix lives at https://www.radix.equinor.com

* Examine and update `./radixconfig.yaml`
* (Apply for access to the Radix playground)
* Create new application in the Radix Playground
* Inject the CLIENTSECRET using the Radix Web Console

(Current version of code uses memory to as session store. This will not scale beyond one app instance and it will leak memory. This set-up is not recommended for ***real*** production scenarios)
