Login on the instance.
```bash
gcloud beta compute ssh --zone us-central1-a encode-workshop-2020-caper-server --project encode-workshop
```

Submit a workflow.
```bash
caper submit https://raw.githubusercontent.com/ENCODE-DCC/rna-seq-pipeline/master/rna-seq-pipeline.wdl -i gs://encode-workshop-2020/input_json/ENCSR059VBF_workshop_input.json -s ANY_LABEL_YOU_LIKE
```

Check status of your workflow:
```bash
caper list | grep $USER
```

Once your workflow's `status` is `Succeeded` then download `metadata.json` from the server.
```bash
caper metadata YOUR_WORKFLOW_ID > metadata.json
```

Use Croo with `metadata.json` to make an HTML report with file table, browser tracks and task graph.
```bash
croo metadata.json --out-dir gs://encode-workshop-2020/croo/$USER --ucsc-genome-db mm10 --public-gcs
```

Click [this](https://console.cloud.google.com/storage/browser/encode-workshop-2020/croo?project=encode-workshop) to open up Google Cloud Storage Console. Find a directory named with your username. Click on the HTML file. On the following page clicking `Public URL` or `Authenticated URL` will open the croo output report.

