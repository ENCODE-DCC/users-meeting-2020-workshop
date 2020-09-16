## How to submit a pipeline

To submit an RNA-seq pipeline with data from ENCODE experiment [ENCSR059VBF](https://www.encodeproject.org/experiments/ENCSR059VBF/).
```bash
$ WDL=https://raw.githubusercontent.com/ENCODE-DCC/rna-seq-pipeline/master/rna-seq-pipeline.wdl
$ INPUT=gs://encode-workshop-2020/input_json/ENCSR059VBF_workshop_input.json
$ caper submit $WDL -i $INPUT -s ANY_LABEL_YOU_LIKE
```

## How to monitor it

Check if your job is submitted. Find workflow's ID in the first column.
```bash
$ caper list | grep $USER
```

## How to organize/visualize outputs

Once your workflow's `status` is `Succeeded` then download `metadata.json` from the server.
```bash
$ caper metadata YOUR_WORKFLOW_ID > metadata.json
```

Use Croo with `metadata.json` to make an HTML report with file table, browser tracks and task graph.
```bash
$ OUTPUT_DIR=gs://encode-workshop-2020/croo/$USER
$ croo metadata.json --out-dir $OUTPUT_DIR --ucsc-genome-db hg38 --public-gcs
```

Click [this](https://console.cloud.google.com/storage/browser/encode-workshop-2020/croo?project=encode-workshop) to open up Google Cloud Storage Console. Find a directory named with your username. Click on an HTML file.
