# Getting Started w/ Example Notebooks
Our example notebooks are hosted on Google Colab. To use them, do the following:

[Sign In](#signing-in)

[Save Your API Keys as Secrets](#google-colab-secrets-manager)

[Retrieve Your Keys](#retrieving-secrets-in-google-colab)

## Signing In
Go to colab.research.google.com
If you're not already signed in to a Google account, you'll be prompted to do so

Enter your Google email address and click "Next"
Enter your password and click "Next"
If you have 2-Factor Authentication enabled, complete the additional verification step


Once signed in, you'll be taken to the Colab homepage

Note: If you don't have a Google account, you'll need to create one to use Colab.

## Google Colab Secrets Manager
To use our simulation environments with OpenAI or Anthropic (Claude), you will have to use your API key.
To keep your API key information secure, save it in `Secrets` manager. 

Once you have opened a Google Colab notebook, look to the far left of the page and select the
key symbol. It should look like this:

<img width="45" alt="orange_key_google" src="https://github.com/user-attachments/assets/3a70d8ae-7ca1-4f23-a5b4-927bdb18ee06">

Then, you will select the `+ Add New Secret` option to import your OpenAI and/or Anthropic Keys.

<img width="177" alt="add_new_secret_google" src="https://github.com/user-attachments/assets/b5291aa6-1805-44c8-9fae-f8854b5da9e9">

Within the code, OpenAI and Anthropic's keys are called using all capital letters, so save your OpenAI key as
`OPENAI_API_KEY` and your Anthropic key as `ANTROPIC_API_KEY`.

## Retrieving Secrets in Google Colab
Our Notebooks already have the code necessary to retrieve your keys from the Google Colab secrets manager, 
but just in case, we have the code below to assist. 

First you will import the `userdata` module from the `google.colab` package as so:


```python
from google.colab import userdata
```

Then you will collect your secrets using the `userdata` command. 

```python
OpenAIAgent(api_key=userdata.get("OPENAI_API_KEY"), model="your-model") # when using openai 
ClaudeAgent(api_key=userdata.get("ANTHROPIC_API_KEY")) # when using Anthropic
```
