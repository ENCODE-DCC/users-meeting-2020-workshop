## How to submit a pipeline

Video of these instructions can be found [here](https://drive.google.com/file/d/1jXdqKlLdWXNf67yy5GtJbWSkEhBpNtOG/view).

To submit an RNA-seq pipeline with data from ENCODE experiment [ENCSR059VBF](https://www.encodeproject.org/experiments/ENCSR059VBF/). The data is part of the dataset used in a [paper](https://www.nature.com/articles/s41586-020-2536-x) published in the Nature.
Run the following commands on the cloudshell window where you have logged in to the caper server.
```bash
WDL=https://raw.githubusercontent.com/ENCODE-DCC/rna-seq-pipeline/master/rna-seq-pipeline.wdl
```
```bash
INPUT=gs://encode-workshop-2020/input_json/ENCSR059VBF_workshop_input.json
```
```bash
caper submit $WDL -i $INPUT -s ANY_LABEL_YOU_LIKE
```

You will see few log messages, and on the last line a message that tells you the workflow has been submitted. The message should be similar to this (timestamp and id will be different):
```bash
2020-09-16 10:20:14,677|caper.caper_client|INFO| submit: {'id': '15df0113-8260-45b7-ac33-5ec248136ad6', 'status': 'Submitted'}
```

## How to monitor it

Video of these instructions can be found [here](https://drive.google.com/file/d/1_AkNthqUHpaLOs5hDtPm7B0Yx6iNDfFp/view).

See that  your workflow is submitted. Find workflow's ID in the first column. In the following command `caper list` shows all the workflows submitted to the server. With `grep $USER` we use a standard unix tool `grep` to find the line that contains your username.
```bash
caper list | grep $USER
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

Video of these instructions can be found [here](https://drive.google.com/file/d/1Jfm55PMhnZTm70H2c-lxEJ9KlMecipja/view?usp=sharing).

Once your workflow's `status` is `Succeeded` then download `metadata.json` from the server.
```bash
caper metadata YOUR_WORKFLOW_ID > metadata.json
```

Use Croo with `metadata.json` to make an HTML report with file table, browser tracks and task graph.
```bash
OUTPUT_DIR=gs://encode-workshop-2020/croo/$USER
croo metadata.json --out-dir $OUTPUT_DIR --ucsc-genome-db mm10 --public-gcs
```

Click [this](https://console.cloud.google.com/storage/browser/encode-workshop-2020/croo?project=encode-workshop) to open up Google Cloud Storage Console. Find a directory named with your username (to find out what your username run `echo $USER` on the caper server). Click on the HTML file. On the following page clicking `Public URL` or `Authenticated URL` will open the croo output report.

