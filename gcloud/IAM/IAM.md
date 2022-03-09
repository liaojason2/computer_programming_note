# Service Account

## Create service account

- `gcloud iam service-accounts create my-sa-123 --display-name "my service account"`

## Role binding

- `gcloud projects add-iam-policy-binding $DEVSHELL_PROJECT_ID \
    --member serviceAccount:my-sa-123@$DEVSHELL_PROJECT_ID.iam.gserviceaccount.com --role roles/editor`
