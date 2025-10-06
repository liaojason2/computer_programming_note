# Web Service

## Deploy app

### .NET

```bash
# Archive a file to zip
Compress-Archive -Path * -DestinationPath deploy.zip

# Deploy file to Azure
az webapp deployment source config-zip --resource-group <resource group> --name <app name> --src deploy.zip
```