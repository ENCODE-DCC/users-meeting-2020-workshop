## How to submit a pipeline

To submit an RNA-seq pipeline with data from ENCODE experiment [ENCSR059VBF](https://www.encodeproject.org/experiments/ENCSR059VBF/).
```bash
$ WDL=https://raw.githubusercontent.com/ENCODE-DCC/rna-seq-pipeline/master/rna-seq-pipeline.wdl
$ INPUT=gs://encode-workshop-2020/input_json/ENCSR059VBF_workshop_input.json
$ caper submit $WDL -i $INPUT -s ANY_LABEL_YOU_LIKE
```

You will see few log messages, and on the last line a message that tells you the workflow has been submitted. The message should be similar to this (timestamp and id will be different):
```bash
2020-09-16 10:20:14,677|caper.caper_client|INFO| submit: {'id': '15df0113-8260-45b7-ac33-5ec248136ad6', 'status': 'Submitted'}
```

## How to monitor it

See that  your workflow is submitted. Find workflow's ID in the first column.
```bash
$ caper list | grep $USER
```

After a moment your workflow will show up in state `Running`:
```bash
15df0113-8260-45b7-ac33-5ec248136ad6    Running rna     workshop_testing_otto   otaljo_gmail_com        None    2020-09-16T10:20:14.673Z
```

The run will take roughly 40 minutes (meanwhile please sit back and enjoy our presentation).

Eventually your workflow will move in to state `Succeeded`:
```bash
15df0113-8260-45b7-ac33-5ec248136ad6    Succeeded       rna     workshop_testing_otto   otaljo_gmail_com        None    2020-09-16T10:20:14.673Z
```

## How to organize/visualize outputs

Once your workflow's `status` is `Succeeded` then download `metadata.json` from the server.
```bash
$ caper metadata YOUR_WORKFLOW_ID > metadata.json
```

Use Croo with `metadata.json` to make an HTML report with file table, browser tracks and task graph.
```bash
$ OUTPUT_DIR=gs://encode-workshop-2020/croo/$USER
$ croo metadata.json --out-dir $OUTPUT_DIR --ucsc-genome-db mm10 --public-gcs
```

Click [this](https://console.cloud.google.com/storage/browser/encode-workshop-2020/croo?project=encode-workshop) to open up Google Cloud Storage Console. Find a directory named with your username. Click on an HTML file.
