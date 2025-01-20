# Cloud Function

## Quickstart

```python
import functions_framework

# Get request return Hello World
@functions_framework.http
def main(request):
  return "Hello World"
```

## Run function locally

- [Run functions with Functions Framework](https://cloud.google.com/functions/docs/running/function-frameworks#functions-local-ff-install-python)

```shell
functions-framework --target=<YOUR_FUNCTION_NAME>
```

## Deploy to GCP

- [Create a Cloud Run function by using the Google Cloud CLI](https://cloud.google.com/functions/docs/create-deploy-gcloud)

```shell
gcloud functions deploy notion-automation \
  --gen2 \
  --runtime=python312 \
  --region=asia-east1 \
  --source="." \
  --entry-point=main \
  --trigger-topic=notion-notify \
  --env-vars-file="env.yaml"
```
