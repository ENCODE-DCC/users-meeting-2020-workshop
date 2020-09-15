# ENCODE Workshop 2020

## How to login on Caper server

Click [this](https://ssh.cloud.google.com/cloudshell/editor) to open up Google Cloud Shell.

You will be asked to choose your Google account or enter your Google credentials. Choose the right Google account that you have registered with the workshop.

On Google Cloud Shell, run the following command line to login on the instance:
```bash
$ gcloud beta compute ssh --zone us-central1-a encode-workshop-2020-caper-server --project encode-workshop
```

## How to submit a pipeline

Run the following command line to submit ENCODE RNA-seq pipeline with test sample.
```bash
$ WDL=https://raw.githubusercontent.com/ENCODE-DCC/rna-seq-pipeline/master/rna-seq-pipeline.wdl
$ INPUT=https://raw.githubusercontent.com/ENCODE-DCC/rna-seq-pipeline/master/test/test_workflow/PE_unstranded_input.json
$ caper submit $WDL -i $INPUT -s ANY_LABEL_YOU_LIKE
```

## How to monitor it

Check if your job is submitted. Check its status (Submitted -> Running -> Succeeded/Failed).
```bash
$ caper list | grep $USER
```
Output of the above command includes workflow's ID (in the first column).


## How to organize output

Make sure that you already have workflow's ID from the above section.

Run the following command line to organize outputs. This will also generate an HTML report with browser tracks and task graph.
```bash
$ OUTPUT_DIR=gs://encode-workshop-2020/croo/$USER
$ croo YOUR_WORKFLOW_ID --out-dir $OUTPUT_DIR --ucsc-genome-db hg38 --public-gcs
```

Click [this](https://console.cloud.google.com/storage/browser/encode-workshop-2020/croo?project=encode-workshop) to open up Google Cloud Storage Console. Find a directory named with your username.

Click on an HTML file.
