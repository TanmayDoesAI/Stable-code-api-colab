# StableCode Instruct Alpha 3b API Implementation

The following Colab notebook presents an implementation using the **stablecode-instruct-alpha-3b** model by [StabilityAI](https://huggingface.co/stabilityai) as a Flask (ngrok) based API.

This project was developed as part of the **StableCode 24-hours Hackathon** at [LabLab.ai](https://lablab.ai), with the goal of utilizing the StableCode Instruct Alpha 3b model to create a functional API.

## Getting Started

To run the API, follow these steps:

1. Open the Colab notebook provided: [StableCode Instruct Alpha 3b API Notebook](https://colab.research.google.com/drive/1MEY4gYU5GfoE59mwjcVHgu33QDUPh1Fq#scrollTo=ZDDNqlh2ZmzW).
2. Obtain your Hugging Face access tokens as outlined in the notebook.
3. Run through the notebook, executing the cells sequentially.
4. At the end of the notebook, you will receive an ngrok link which will be your API endpoint.

## Open in Colab

You can interact with the entire project in the live Colab environment. Click the button below to open the notebook:

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1MEY4gYU5GfoE59mwjcVHgu33QDUPh1Fq#scrollTo=ZDDNqlh2ZmzW)

## API Calling
#### Using Curl:
```
curl -X POST -H "Content-Type: application/json" -d "{\"input_string\": \"Write entire code for matrix multiplication in python with a test run\"}" http://17b7-34-138-136-161.ngrok.io/process_string
```
#### Using it in python:
```python
import requests

#Add the link from the code here
ngrok_link = "http://16f2-34-126-134-108.ngrok.io"

api_url = f"{ngrok_link}/process_string"

# JSON payload for the POST request
payload = {
    "input_string": "Write entire code for matrix multiplication in python with a test run"
}

# Making the POST request
response = requests.post(api_url, json=payload)

# Checking the response
if response.status_code == 200:
    response_json = response.json()
    result = response_json.get('result', '')
    formatted_result = result.replace('\\n', '\n').replace('\\t', '    ')
    print("Response Code:", response.status_code)
    print("Formatted Result:")
    print(formatted_result)
else:
    print("Request failed with status code:", response.status_code)

```
## Acknowledgments

- [StabilityAI](https://huggingface.co/stabilityai) for providing the StableCode Instruct Alpha 3b model.
- [LabLab.ai](https://lablab.ai) for hosting the StableCode Hackathon.
- Special thanks to the organizers, mentors, and contributors who made this project possible.
