# Sentiment Analysis API

Flask API exposing an endpoint for determining the
sentiment of text.

[![status: archived](https://img.shields.io/badge/status-archived-red.svg)](https://docs.github.com/en/repositories/archiving-a-github-repository/archiving-repositories)
> ⚠ **Note:** This repository has been **archived** and is no longer maintained.
```
This fork was primarily to contribute enhancements to the open-source sentiment-api project by Martin Oywa (martinoywa).
It is no longer in active use, and there are no current or future plans to contribute to or develop this repository further.

The code and history remain available for reference. Feel free to browse or fork, but please be aware that:
- Issues and pull requests are disabled
- No support or updates will be provided

Thanks for your interest!
```

# How to run locally. (**_Terminal_**)
> The following commands require execution in the project root.

1. Create a virtual environment.
```bash
python3 -m venv .venv
```


2. Activate the virtual environment.
```bash
. .venv/bin/activate
```

> The following commands assume you have an active virtual environment.

3. Install dependencies. (Using the Makefile)
```bash
make install
```

> ⚠ The above make `target` will install the latest, unpinned requirements from the file: `requirements.in`. If encounter any dependency-related issue during installation or runtime, fall back to use tested, pinned, and stable requirements defined in the file: `requirements.txt` 

- [Optional] Fall back to stable requirements.
```bash
pip install -r requirements.txt
```

4. Run the application.
```bash
python app.py
```


5. Query the api.

Query: `I don't like this game`
```bash
curl \
-X POST \
-H "Content-Type: application/json" \
-d '{"input": "I don't like this game"}' \
"http://127.0.0.1:10010/api/v1/sentiment"
```

Output:
```json
{
  "prediction": {
    "confidence": 0.9779077172279358,
    "label": "Negative"
  }
}
```

# How to run locally. (**_Docker_**)

1. Prerequisite: Make sure you have docker installed. [Link](https://docs.docker.com/desktop/install/mac-install/)


2. Build the docker image. This uses the Docker file in the repository's root.
```bash
docker build --build-arg VERSION=SENTIMENT-v1 -t sentiment-api:dev .
```


3. Run a container using the image as its base.
```bash
docker run --rm -p 10010:10010 --name sentiment-api sentiment-api:dev
```


4. Querying works like the previous one. You can also use **Postman**.


5. More Examples:

Query: `I like this game` 

```bash
curl \
-X POST \
-H "Content-Type: application/json" \
-d '{"input": "I like this game"}' \
"http://127.0.0.1:10010/api/v1/sentiment"
```

```json
{
  "prediction": {
    "confidence": 0.9681828022003174,
    "label": "Positive"
  }
}
```

Query: `I have no opinion`
```bash
curl \
-X POST \
-H "Content-Type: application/json" \
-d '{"input": "I have no opinion"}' \
"http://127.0.0.1:10010/api/v1/sentiment"
```

```json
{
  "prediction": {
    "confidence": 0.49172118306159973,
    "label": "Neutral"
  }
}
```


# How to run on cloud. (**_AWS_**)

1. Code available in branches `deploy` for `AWS Lightsail` and `ebs` for `AWS Elasticbeanstalk`.
2. Documentations are available via this [link](https://bit.ly/3Z00RlR), Pages `8` & `9`.


###

Built with ❤️ by [martinoywa](https://github.com/martinoywa).
