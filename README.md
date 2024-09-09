# OPA Feedback Form in ruletxt format

This is a ruletxt version of the [OPA Feedback Form rulebase](https://github.com/ministryofjustice/laa-ccms-opa-feedback-form-v23).

## Generating the ruletxt

### Setup

Clone this repo:
```sh
cd ~/code
git clone git@github.com:ministryofjustice/laa-ccms-opa-feedback-form-v23-ruletxt.git
```

opa_tools needs to be cloned, requirements installed and LFS installed - see [opa_tools setup](https://github.com/ministryofjustice/opa_tools?#setup)

### Convert all .docx files

Get the latest source rulebase Zip and extract to Word docs:
```sh
cd ~/code/laa-ccms-opa-feedback-form-v23
git pull
# If you've previously done this, move aside the old extracted model
mv ../laa-ccms-opa-feedback-form-v23-extracted /tmp/
unzip FeedbackForm.zip -d ../laa-ccms-opa-feedback-form-v23-extracted
```

Convert the Word docs to Ruletxt
```sh
cd ~/code/laa-ccms-opa-feedback-form-v23-ruletxt
# If you've previously done this, delete the old ruletxt files
rm *.ruletxt
. ~/code/opa_tools/venv/bin/activate
python ~/code/opa_tools/docx2ruletxt.py -d ../laa-ccms-opa-feedback-form-v23-extracted/FeedbackForm/Rules -o ../laa-ccms-opa-feedback-form-v23-ruletxt
```

Commit the changes to the repo:
```sh
git commit -a -m 'Update'
git push
```
