## How to login on Caper server

Video of these instructions can be found [here](https://drive.google.com/file/d/1CtXuK0UM8zD_zm93gio19navmcCrAdp7/view).

Click [this](https://ssh.cloud.google.com/cloudshell/editor) to open up Google Cloud Shell.

You will be asked to choose your Google account or enter your Google credentials. Choose the right Google account that you have registered with the workshop.

On Google Cloud Shell, run the following command line to login on the instance:
```bash
$ gcloud beta compute ssh --zone us-central1-a encode-workshop-2020-caper-server --project encode-workshop
```
