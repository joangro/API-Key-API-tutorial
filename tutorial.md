# API Keys API Overview

## Set up the environment

### Authenticate with your account in gcloud

```bash
gcloud init
```

### Enable API Keys API 

Requires having [servicemanagement](https://cloud.google.com/service-infrastructure/docs/service-management/getting-started) API and enabled and (serviceusage.services.enable)[https://cloud.google.com/service-usage/docs/reference/rest/] permissions in the project.

```bash
curl "https://servicemanagement.googleapis.com/v1/services/apikeys.googleapis.com:enable" \
-H "Authorization: Bearer $(gcloud auth print-access-token)" -H'content-type:application/json' -X POST \
-d"{
    \"consumerId\": \"project:$DEVSHELL_PROJECT_ID\"
   }" 
```

## List Project API Keys

```bash
 curl "https://apikeys.googleapis.com/v1/projects/$DEVSHELL_PROJECT_ID/apiKeys" \
 -H'content-type:application/json' -H "Authorization: Bearer $(gcloud auth print-access-token)"
 ```
 
 ## Add API Key
 
 ```bash
curl "https://apikeys.googleapis.com/v1/projects/$DEVSHELL_PROJECT_ID/apiKeys" \
-H "Authorization: Bearer $(gcloud auth print-access-token)" -H'content-type:application/json' -X POST \
-d"{
    \"displayName\": \"API key example\",
    \"androidKeyDetails\":{
        \"allowedApplications\":[]
      }
    }"
 ```
