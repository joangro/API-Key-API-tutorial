# API Keys API Overview

## Set up the environment

### Authenticate with your account in gcloud

```
gcloud init
```

### Enable API Keys API 

Requires having [servicemanagement](https://cloud.google.com/service-infrastructure/docs/service-management/getting-started) API enabled and [serviceusage.services.enable](https://cloud.google.com/service-usage/docs/reference/rest) permissions in the project.

```
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
 
```
curl "https://apikeys.googleapis.com/v1/projects/$DEVSHELL_PROJECT_ID/apiKeys" \
-H "Authorization: Bearer $(gcloud auth print-access-token)" -H'content-type:application/json' -X POST \
-d"{
    \"displayName\": \"API key example\",
    \"androidKeyDetails\":{
        \"allowedApplications\":[]
      }
    }"
```
 
## Describe API Key
  
Export API Key ID:

```
export KEY_ID=<keyId>
```

Describe API Key:
```bash
curl "https://apikeys.googleapis.com/v1/projects/$DEVSHELL_PROJECT_ID/apiKeys/$KEY_ID" \
-H "Authorization: Bearer $(gcloud auth print-access-token)" -H'content-type:application/json' -X GET
```

Delete API Key:
```bash
curl "https://apikeys.googleapis.com/v1/projects/$DEVSHELL_PROJECT_ID/apiKeys/$KEY_ID" \
-H "Authorization: Bearer $(gcloud auth print-access-token)" -H'content-type:application/json' -X DELETE
```

## Done!
<walkthrough-conclusion-trophy></walkthrough-conclusion-trophy>
<walkthrough-tutorial-duration></walkthrough-tutorial-duration>

 
 
 
 
 
 
