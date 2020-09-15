# Developer's guide to set up Caper server

Follow [this instrution](https://github.com/ENCODE-DCC/caper/tree/master/scripts/gcp_caper_server) to create a Caper server instance.

```bash
$ SERVICE_ACCOUNT_KEY_JSON=[YOUR_KEY_JSON_FILE]
$ git clone https://github.com/ENCODE-DCC/caper
$ cd caper
$ bash scripts/gcp_caper_server/create_instance.sh encode-workshop-2020-caper-server encode-workshop $SERVICE_ACCOUNT_KEY_JSON gs://encode-workshop-2020/caper_out -l gs://encode-workshop-2020/caper_tmp -b 200GB
```
