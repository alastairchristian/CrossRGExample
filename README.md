# CrossRGExample

An example of an ARM Template with nested template to allow deployment of resources to separate resource groups. The accompanying blog post is avaialble at [alastairchristian.com](https://alastairchristian.com/arm-templates-deploy-to-multiple-resource-groups-with-nested-templates-44665588e3e3?sk=a1a520ce72cfdbd6390d15349c2f92f8).

## Deploying the Example

The template deploys an App Service Plan to one resource group and an App Service to a second. To deploy the example you will require an Azure Subscription. You will also need to create the 2 resource groups (the template does not do this and requires them to already exist). You can create a resource group from the Azure CLI as follows:

```
az group create -l southafricanorth -n your-rg-name
```

replacing southafricanorth with your preferred region and your-rg-name with your own resource group name. 

You will then need to modify the parameters.json file to specify values for:
* the name of the App Service Plan
* the name of the App Service
* the name of the resource group you wish to deploy the App Service in.

Once the parameters have been set, you can deploy the resource from the Azure CLI with a command such as:

```
az group deployment create \
--name NewDeployment \
--resource-group your-rg-1-name \
--template-file deploy.json \
--parameters parameters.json
```

where your-rg-1-name is the name of the resource group you want to deploy the App Service Plan to.

