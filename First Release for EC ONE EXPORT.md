## API KEYS

1. Create API Keys in AUTH


### NOTE
1. You can use POSTMAN application to create the api keys 
2. Replace **AUTH_DNS** for the URL of the **AUTH API**

1.1 Create Applications

```
METHOD: POST
URL: [AUTH_DNS]/applications   
Authorization: Basic Api Keys the Auth in live
Body: {
   "code":"econeexports",
   "name":"ec-one-exports",
   "url": "https://exporter.evercheck.com/api/v1"
   "description":"ec-one-exports"
}
```

1.2 Create Api Keys

```
METHOD: POST
URL: [AUTH_DNS]/applications/econeexports/apiKeys
Authorization: Basic Api Keys the Auth 
Body:{
  "description":"ec-one-exports",
  "type":"READ"
}
```

1.3 Find Api Keys Created

```
METHOD: GET
URL: [AUTH_DNS]/applications
Authorization: Basic Api Keys the Auth 

```


## DEPLOY API

1. go to the machine of **ec-one-exports API**
2. go to the project folder with the command: `cd /var/www/ec-one-exports`
3. clone this repo `https://github.com/cebroker/ec-one-exports.git`
4. create  `.env` file **in project root**
5. open the `.env` file with a text editor like **nano**: `nano .env`
6. add the following lines and add its values:

```
EC_NODE_ENV='environment'

## ORACLE
ORACLE_CONNECTION_STRING=
ORACLE_USER=
ORACLE_PASSWORD=

## AWS Secret manager
AWSENDPOINT=
AWSREGION=us-east-1
AWSSECRETNAME=[SECRET NAME GENERATED]

## AWS SECRET KEYS
AWSACCESSKEY=[Copy value from API-V2 WORKERS ]
AWSSECRETKEY=[Copy value from API-V2 WORKERS]
FIREBASE_DATABASE_URL=[Copy value from API-V2 WORKERS]

## REDIS
REDIS_URL=[URL Redis]
REDIS_PORT=[Port URL] 
REDIS_AUTH=
REDIS_PASSWORD=
ARENA_APP_PORT=4000

## AUTH_API
AUTH_URL= [URL Auth Environment]
AUTH_APPLICATION_KEY=[KEY Auth Environment]
AUTH_APPLICATION_SECRET=[SECRET Auth Environment]
API_KEY_FILENAME=api_keys.json

## EXPORTER_API
BASE_URL=https://exporter.evercheck.com/api/v1
EXPORTER_KEY= [Generated CREATE API KEYS]
EXPORTER_SECRET= [Generated CREATE API KEYS]

## MONGO_DB
WALLET_MONGO_HOST=[URL Conexion Mongo Wallet Environment]
WALLET_MONGO_DB_NAME=[Database wallet Name]

ADOPTION_REPORT_QUEUE_LIMIT_SANDBOXED=2


## MESSAGES_CENTER_APPS
MESSAGING_URL= [URL Message Center Environment]
MESSAGING_CLIENT_ID= [Copy value from API-V2 WORKERS]
MESSAGING_CLIENT_SECRET= [Copy value from API-V2 WORKERS]
 
## STORAGE
STORAGE_V2_URL= [URL Storage Environment]
STORAGE_V2_URL_API_KEY= [Key Storage Environment]
STORAGE_V2_URL_API_SECRET= [Secret Storage Environment]

## METRICS
METRICS_HOST= [URL Metrics Environment]
METRICS_PORT= [Port Metrics Environment]
METRICS_JOB_NAME=ec-one-exports
METRICS_INSTANCE= [Ip local machine]
ENABLE_METRICS=1
```

7. run the command 

```
sh deploy.sh (production|demo|staging) api

```


## DEPLOY JOBS

1. go to the machine of **ec-one-exports JOBS**
2. go to the project folder with the command: `cd /var/www/ec-one-exports`
3. clone this repo `https://github.com/cebroker/ec-one-exports.git`
4. create `temp` directory **in project root**
5. create  `.env` file **in project root**
6. open the `.env` file with a text editor like **nano**: `nano .env`
7. add the following lines and add its values:

```
EC_NODE_ENV='environment'

## ORACLE
ORACLE_CONNECTION_STRING=
ORACLE_USER=
ORACLE_PASSWORD=

## AWS Secret manager
AWSENDPOINT=
AWSREGION=us-east-1
AWSSECRETNAME=[SECRET NAME GENERATED]

## AWS SECRET KEYS
AWSACCESSKEY=[Copy value from API-V2 WORKERS ]
AWSSECRETKEY=[Copy value from API-V2 WORKERS]
FIREBASE_DATABASE_URL=[Copy value from API-V2 WORKERS]

## REDIS
REDIS_URL=[URL Redis]
REDIS_PORT=[Port URL] 
REDIS_AUTH=
REDIS_PASSWORD=
ARENA_APP_PORT=4000

## AUTH_API
AUTH_URL= [URL Auth Environment]
AUTH_APPLICATION_KEY=[KEY Auth Environment]
AUTH_APPLICATION_SECRET=[SECRET Auth Environment]
API_KEY_FILENAME=api_keys.json

## EXPORTER_API
BASE_URL=https://exporter.evercheck.com/api/v1
EXPORTER_KEY= [Generated CREATE API KEYS]
EXPORTER_SECRET= [Generated CREATE API KEYS]

## MONGO_DB
WALLET_MONGO_HOST=[URL Conexion Mongo Wallet Environment]
WALLET_MONGO_DB_NAME=[Database wallet Name]

ADOPTION_REPORT_QUEUE_LIMIT_SANDBOXED=2


## MESSAGES_CENTER_APPS
MESSAGING_URL= [URL Message Center Environment]
MESSAGING_CLIENT_ID= [Copy value from API-V2 WORKERS]
MESSAGING_CLIENT_SECRET= [Copy value from API-V2 WORKERS]
 
## STORAGE
STORAGE_V2_URL= [URL Storage Environment]
STORAGE_V2_URL_API_KEY= [Key Storage Environment]
STORAGE_V2_URL_API_SECRET= [Secret Storage Environment]

## METRICS
METRICS_HOST= [URL Metrics Environment]
METRICS_PORT= [Port Metrics Environment]
METRICS_JOB_NAME=ec-one-exports
METRICS_INSTANCE= [Ip local machine]
ENABLE_METRICS=1
```

8. run the command 

```
sh deploy.sh (production|demo|staging) jobs

```

9. run the command in just one of machine.

```
pm2 start arena.js --log-date-format "YYYY-MM-DD HH: mm : ss" || PM2_ERROR = true
