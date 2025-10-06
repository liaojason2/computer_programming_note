# Web Service

## Deploy app

### .NET

```bash
# Publish app to \publish folder
dotnet publish -c Release -o .\publish

# Access into publish folder
cd .\publish

# Archive a file to zip
# Ensure there is no exist deploy.zip file in the path
Compress-Archive -Path * -DestinationPath deploy.zip
# Overwrite the file
Compress-Archive -Path * -DestinationPath deploy.zip --force

# Deploy file to Azure
az webapp deployment source config-zip --resource-group <resource group> --name <app name> --src deploy.zip
```
