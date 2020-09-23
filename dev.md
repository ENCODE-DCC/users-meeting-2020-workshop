## Creating a Caper server instance

Follow [these instructions](https://github.com/ENCODE-DCC/caper/tree/master/scripts/gcp_caper_server) to create a Caper server instance.

```bash
$ SERVICE_ACCOUNT_KEY_JSON=[YOUR_KEY_JSON_FILE]
$ git clone https://github.com/ENCODE-DCC/caper && cd caper
$ bash scripts/gcp_caper_server/create_instance.sh encode-workshop-2020-caper-server encode-workshop $SERVICE_ACCOUNT_KEY_JSON gs://encode-workshop-2020/caper_out -l gs://encode-workshop-2020/caper_tmp -b 200GB
```

## Setting up `OS Login` for users

Click on [Metadata](https://console.cloud.google.com/compute/metadata?project=encode-workshop&folder&organizationId) of the project and add key/value pair `enable-oslogin`/`TRUE` to allow `OS Login`.


## How to add users

Click on [IAM](https://console.cloud.google.com/iam-admin/iam?orgonly=true&project=encode-workshop&supportedpurview=organizationId) and click on the `ADD` button on top right.

Add users' Google account or email address associated with it. Give them the followings roles:
- `OS Login`
- `Service Account User`

