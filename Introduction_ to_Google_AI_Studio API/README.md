


## Introduction
This Lecture introduces the Google AI Studio platform, its Gemini models, and how to utilize their APIs in Python. It emphasizes the advanced functionalities available in AI APIs, best practices for understanding and debugging code, and encourages a self-learning mindset for working with evolving AI platforms.


### Setting Up Google Client in Python
**pip install google-generative-ai**


```bash
import google.generativeai as genai
genai.configure(api_key="YOUR_API_KEY")

```

### Obtaining API Keys from Google
* Visit Google AI Studio.
* Accept terms regarding data usage for model training.
* Create new API keys under projects.
* Store keys securely in environment variables or .env files.


## Using Google AI Studio APIs:

* Use genai.list_models() to retrieve all available models.
* Filter models with “Gemini” in their names to select the appropriate one.
* Validation of API keys occurs during client setup and model listing.