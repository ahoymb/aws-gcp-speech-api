*\*This is not an official GCP repository*

# Google Speech API call from AWS

## Introduction
This code performs a [Google Cloud Speech API](https://cloud.google.com/speech-to-text/) call using a file in [AWS Cloud File](https://aws.amazon.com/what-is-cloud-file-storage/) storage for transcribing an audio file into text.

### Architecture
![architecture](./architecture.svg)

## Pre-Requisites
1. Need a Google Cloud Platform account
1. Need an AWS account
1. Add a custom domain for your applicaion, see [Verification](https://cloud.google.com/appengine/docs/flexible/python/mapping-custom-domains)
(If this is your first time, follow "Your first app with Python" set-up

## Setup
1. Create a GCP Project from Cloud Shell
```
gcloud projects create ablesoul-aws-gcp-speech-api
```
2. Log into to project.
```
gcloud init
```
3. Clone [github repository](https://github.com/GoogleCloudPlatform/training-data-analyst).
```
git clone https://github.com/GoogleCloudPlatform/training-data-analyst
```
4. Change directory to blogs/endpointslambda/aeflex-endpoints/
```
cd training-data-analyst/blogs/endpointslambda/aeflex-endpoints/
```
5. Update the host field to your project name in the openapi.yaml file.
"host: "echo-api.endpoints.ablesoul-aws-gcp-speech-api.cloud.goog"
6. Deploy API
```
gcloud endpoints services deploy openapi.yaml
```
7. Collect the Service configuration [2018-09-15r0] for the service. Update the name and config_id fields in the app.yaml file.
```
  name: echo-api.endpoints.ablesoul-aws-gcp-speech-api.cloud.goog
  config_id: 2018-09-15r0
```
8. Deploy the application. If billing is not enabled, be sure to link a billing account to the project.
```
gcloud app deploy
```

## Create an API Key to Authenticate Clients
1. In the GCP Console, on the Products & services menu, click API Manager > Credentials.
1. Click Create Credentials > API key. Note the API key.


## Create an AWS S3 Buckets for Raw Files
1. Create an S3 Bucket. Note the name: ablesoul-gcp-raw
1. Create IAM Roles
1. Create SQS Queue
1. Create Lambda function

## Edit lambdafunctioninline.py
1. change endpoint URL

## Sources
1. https://cloudplatform.googleblog.com/2017/04/going-multi-cloud-with-Google-Cloud-Endpoints-and-AWS-Lambda.html
1. https://medium.com/@lestrrat/open-your-repository-in-google-cloud-shell-550610963a7a
