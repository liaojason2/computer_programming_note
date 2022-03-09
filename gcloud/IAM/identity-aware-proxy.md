# Identity-Aware Proxy

## Configure Consent Screen

- Internal

## IAP setting

1. Select Internal under User Type and click Create
2. Fill in the required blanks with appropriate values

- App name
  - IAP Example
- User support email
  - Select your Qwiklabs student email address from the dropdown.
- Application home page
  - The URL you used to view your app. You can find this again by running the gcloud app browse command in cloud shell again.
- Application privacy Policy link
  - The privacy page link in the app, same as the homepage link with /privacy added to the end
- Authorized domains
  - Click + ADD DOMAINThe hostname portion of the application's URL, e.g. iap-example-999999.appspot.com. You can see this in the address bar of the Hello World web page you previously opened. Do not include the starting https:// or trailing / from that URL.

## Disable Flex API

- `gcloud services disable appengineflex.googleapis.com`

App Engine has its standard and flexible environments which are optimized for different application architectures. Currently, when enabling IAP for App Engine, if the Flex API is enabled, Google Cloud will look for a Flex Service Account. Your Qwiklabs project comes with a multitude of APIs already enabled for the purpose of convenience. However, this creates a unique situation where the Flex API is enabled without a Service Account created.

## Turn on IAP

Turn on IAP after created.

