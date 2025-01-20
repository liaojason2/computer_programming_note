# Cloud Scheduler

- [Scheduling Google Cloud Functions to Run Periodically](https://gauravtanwar1.medium.com/scheduling-google-cloud-functions-to-run-periodically-4fd3e763e78f)
- [Schedule an event-driven Cloud Run function](https://cloud.google.com/scheduler/docs/tut-gcf-pub-sub)

## Example

```sh
Create a event triggered pub/sub based cloud scheduler 

gcloud scheduler jobs create pubsub scheduler-demo \
  --topic=pub-sub-scheduler-demo \
  --schedule="* 22 * * *" \  # Run every day at 10 PM
  --message-body="." \
  --location="asia-east1"
```