# Packer Azure ARM

## Create a resource group

```shell
az group create -n myResourceGroup -l eastus
```

Sample output:

```json
{
  "id": "/subscriptions/234bda31-0fde-31de-b81e-f123adg51cba/resourceGroups/myResourceGroup",
  "id": "/subscriptions/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/resourceGroups/myResourceGroup",
  "location": "eastus",
  "managedBy": null,
  "name": "myResourceGroup",
  "properties": {
    "provisioningState": "Succeeded"
  },
  "tags": null,
  "type": "Microsoft.Resources/resourceGroups"
}
```

## Create a service principal

```shell
az ad sp create-for-rbac --query "{ client_id: appId, client_secret: password, tenant_id: tenant }"
```

Sample output:

```json
{
  "client_id": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
  "client_secret": "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx",
  "tenant_id": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
}
```

## Get your Azure subscription id

```shell
az account show --query "{ subscription_id: id }"
```

Sample output:

```json
{
  "subscription_id": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
}
```

## Fill the template

These values need to be changed in `ubuntu.json`.

- client_id
- client_secret
- tenant_id
- subscription_id

## Build the image

```shell
packer build ubuntu.json
```

This will take a bit of time, show a lot of output, some green, some red.
