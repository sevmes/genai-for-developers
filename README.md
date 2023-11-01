# dai


Venv Commands

```sh
python3 -m venv venv
. venv/bin/activate
deactivate
```

Dependencies
```sh
pip install click
pip install google-cloud-aiplatform
pip install google-cloud-discoveryengine

pip freeze > requirements.txt

pip install -r requirements.txt
```

Run the app from source
```sh
python hello.py
```

Install the app
```sh
pip install --editable .
```

Run the installed app
```sh
dai ai
```

Uninstall the app
```sh
python setup.py develop -u
```

Use the app
```sh
cd gcloudai
python gcloudai/hello.py query
python gcloudai/hello.py readfiles
```

Docker

```sh
docker build -t dai-img .
docker run -it dai-img
dai ai

# mount local gcloud config for adc
docker run -it -v ~/.config:/root/.config dai-img
dai query
```

# Swtich account/project account

```sh
gcloud auth login
gcloud auth list
gcloud config set account {account}

gcloud config set project genai-cicd
```

Cloud Build
```sh
gcloud artifacts repositories create app-image-repo \
    --repository-format=docker \
    --location=us-central1

gcloud builds submit . --config=cloudbuild-local.yaml \
    --substitutions=_ARTIFACT_REGISTRY_REPO=app-image-repo

gcloud builds submit . --config=cloudbuild-pipeline-test.yaml 

```
