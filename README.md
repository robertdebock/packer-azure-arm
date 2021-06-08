# Packer Azure ARM

## Create a resource group

```shell
az group create -n myResourceGroup -l eastus
```

Sample output:

```json
{
  "id": "/subscriptions/27c6a60b-0aed-4e75-a7ea-f5cf2e49f89e/resourceGroups/myResourceGroup",
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
  "client_id": "93b1395d-51b5-4947-857b-88752561b267",
  "client_secret": "Bk348AjfsdD.sdflkj2_lkdjf2junNANai",
  "tenant_id": "58eabf40-fc5f-4a00-99d1-391ffa593deb"
}
```

## Get your Azure subscription id

```shell
az account show --query "{ subscription_id: id }"
```

Sample output:

```json
{
  "subscription_id": "234bda31-0fde-31de-b81e-f123adg51cba"
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
