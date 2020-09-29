## How to login on Caper server

Video of these instructions can be found [here](https://drive.google.com/file/d/1CtXuK0UM8zD_zm93gio19navmcCrAdp7/view).

Click [this](https://ssh.cloud.google.com/cloudshell/editor?shellonly=true) to open up Google Cloud Shell. Provisioning the cloud shell machine can take up to 30 seconds, don't worry! 

You will be asked to choose your Google account or enter your Google credentials. Choose the right Google account that you have registered with the workshop.

On Google Cloud Shell, run the following command line to login on the instance:
```bash
gcloud beta compute ssh --zone us-central1-a encode-workshop-2020-caper-server --project encode-workshop
```

The system may ask for authorization to use your credentials. In that case click `Authorize`. 
In case you run into authentication related errors, please double check that you are using the account you registered to the workshop with and repeat the login process from the beginning.
If your connection to times out, you should repeat the login steps to get back into the cloudshell.
