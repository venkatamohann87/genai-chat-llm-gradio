## Development and Deployment of a 'Chat with LLM' Application Using the Gradio Blocks Framework

### AIM:
To design and deploy a "Chat with LLM" application by leveraging the Gradio Blocks UI framework to create an interactive interface for seamless user interaction with a large language model.

### PROBLEM STATEMENT:
Building a user-friendly application that allows seamless interaction with a large language model (LLM) is challenging without requiring specialized API keys or external resources. This project addresses the need for an accessible, open-source solution to implement such applications using pre-trained models and the Gradio Blocks framework.

### DESIGN STEPS:
#### STEP 1:

Import Required Libraries. Install and import the necessary libraries: Gradio for the UI. Transformers for using pre-trained models.

#### STEP 2:

Use a pre-trained model like GPT-2 or DialoGPT from Hugging Face.Initialize the model using the pipeline API for straightforward interaction.

#### STEP 3:

Run the application locally with demo.launch(). Optionally deploy it to the cloud for broader accessibility.

### PROGRAM:
```
Name: Venkata Mohan N
Reg.No: 212224230298
```
```
import os
import io
import IPython.display
from PIL import Image
import base64 
import requests 
requests.adapters.DEFAULT_TIMEOUT = 60

from dotenv import load_dotenv, find_dotenv
_ = load_dotenv(find_dotenv()) # read local .env file
hf_api_key = os.environ['HF_API_KEY']


# Helper function
import requests, json
from text_generation import Client

#FalcomLM-instruct endpoint on the text_generation library
client = Client(os.environ['HF_API_FALCOM_BASE'], headers={"Authorization": f"Basic {hf_api_key}"}, timeout=120)


#Back to Lesson 2, time flies!
import gradio as gr
def generate(input, slider):
    output = client.generate(input, max_new_tokens=slider).generated_text
    return output

demo = gr.Interface(fn=generate, 
                    inputs=[gr.Textbox(label="Prompt"), 
                            gr.Slider(label="Max new tokens", 
                                      value=20,  
                                      maximum=1024, 
                                      minimum=1)], 
                    outputs=[gr.Textbox(label="Completion")])

gr.close_all()
demo.launch(share=True, server_port=int(os.environ['PORT1']))

```
### OUTPUT:
<img width="1010" height="361" alt="image" src="https://github.com/user-attachments/assets/951d0303-63cb-4864-ab97-1333ce36bef2" />



### RESULT:
Thus the Chat with LLM Application Using the Gradio Blocks Framework is created successfully.
