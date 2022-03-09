# k8s

## kubectl command

- `kubectl explain`
  - `kubectl explain deployment`
  - `kubectl explain deployment --recursive`
  - `kubectl explain deployment.metadata.name`
- `kubectl create -f deployments/auth.yaml`
  - create a deployment

## GKE

Create a cluster with five n1-standard-1 nodes (this will take a few minutes to complete):

```sh
gcloud container clusters create bootcamp --num-nodes 5 --scopes "https://www.googleapis.com/auth/projecthosting,storage-rw"
```

Get cretenional 

```sh
gcloud container clusters get-credentials jenkins-cd
```

## Link

- [Google Cloud Booth (Qwiklabs)](google_cloud_skills_booth.md)