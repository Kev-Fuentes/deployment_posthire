# Deploying EC ONE EXPORTER WORKER [AWS CLOUD API]
## Deployment type
### Cloud - Ansible

## The .env file of this service is located on:
`/var/www/ec-one-exports/.env`

In this guide, you will find all the necessary steps to perform a deployment of **EC ONE EXPORTER WORKER** to a specific environment. We have to ways to do it, based on how is configured the environment.

## Production

In order to deploy this service in this environment, please follow these steps:

**step 1:** If you need to add/update environment variables, please update the environment of the application in AWS secret Manager.(*SECRET NAME*: `production/evercheck/ec-one-exports` stored in **us-east-1** in our main  EC Credentialing AWS account). If you need more information about this, please read 
[this guide](https://github.com/cebroker/ec-deployments/wiki/Update-Environment-Variables)

**step 2:** Go to [ec-deployment](https://github.com/cebroker/ec-deployments) project and within the root folder of the project run this command:

```
ansible-playbook playbooks/application_deployment.yml -i production -e app_name=ec_one_exporter_worker -t deploy 
```

If you need more information about this, please read [this guide](https://github.com/cebroker/ec-deployments/wiki/Deploy-a-service)

**step 3:** Wait for Ansible to finish the process.


## Demo

In order to deploy this service in this environment, please follow these steps:

**step 1**: 

If you need to add/update environment variables, please update the environment of the application in AWS secret Manager.(*SECRET NAME*: `demo/evercheck/ec-one-exports` stored in **us-east-1** in our main  EC Credentialing AWS account). If you need more information about this, please read 
[this guide](https://github.com/cebroker/ec-deployments/wiki/Update-Environment-Variables)

**step 2**: Go to [ec-deployment](https://github.com/cebroker/ec-deployments) project and within the root folder of the project run this command:

```
ansible-playbook playbooks/application_deployment.yml -i demo -e app_name=ec_one_exporter_worker -t deploy 
```

If you need more information about this, please read [this guide](https://github.com/cebroker/ec-deployments/wiki/Deploy-a-service)

**step 3:** Wait for Ansible to finish the process.


## Test

In order to deploy this service in this environment, please follow these steps:

**step 1**: 

If you need to add/update environment variables, please update the environment of the application in AWS secret Manager.(*SECRET NAME*: `test/evercheck/ec-one-exports` stored in **us-east-1** in our main  EC Credentialing AWS account). If you need more information about this, please read 
[this guide](https://github.com/cebroker/ec-deployments/wiki/Update-Environment-Variables)

**step 2**: Go to [ec-deployment](https://github.com/cebroker/ec-deployments) project and within the root folder of the project run this command:

```
ansible-playbook playbooks/application_deployment.yml -i test -e app_name=ec_one_exporter_worker -t deploy 
```

If you need more information about this, please read [this guide](https://github.com/cebroker/ec-deployments/wiki/Deploy-a-service)

**step 3:** Wait for Ansible to finish the process.

# Manual deploy
**step 1:** Connect via ssh to the machine like so:

 ```
ssh zcebjobs@10.21.50.105
ssh zcebjobs@10.21.50.106
 ```

**step 2:** Once connected, navigate to the root of the project:

```
cd /var/www/ec-one-exports && sh deploy.sh staging workers
```


IMPORTANT Replace the placeholder `[environment]` with one of these options: staging, demo, or production, based on the environment where you are performing the release

**step 3:** Type your Github credentials (if needed) and wait for pm2 to reload.

