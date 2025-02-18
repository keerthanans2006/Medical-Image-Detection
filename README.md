# Medical Image Detection 
We will be using Python, Streamlit for front end, and Google’s Gemini-2.0-pro-exp-02-05. The user will be able to import medical images, obtain analysis, as well as get recommendations and some pointers regarding treatment.

https://github.com/keerthanans2006/Medical-Image-Detection/blob/main/Screenshot%20(3).png?raw=true

## Setting Up the Project
First, let’s create a new folder and open it in VS Code. We’ll create two files: api_key.py to hold our API key and app.py to hold our application logic.

## Configuring the API Key
In `api_key.py`, we’ll store our API key:
```python
API_KEY = "YOUR_API_KEY_HERE"
```
## Setting Up the Front End
In app.py, we’ll import the necessary modules:
```
import streamlit as st
import pathlib
import google.generativeai as genai
```
Configuring the Gemini Pro Vision Model
We’ll configure the Gemini-2.0-pro-exp-02-05 model:
```
gen_ai.configure(api_key=API_KEY)
model = gen_ai.gemini-2.0-pro-exp-02-05()
```
Uploading the Image
We’ll create a file uploader:
```
uploaded_file = st.file_uploader(“Upload medical image for analysis”, type=[“png”, “jpg”, “jpeg”])
```
Generating the Analysis
We’ll create a button to generate the analysis:
```
if st.button(“Generate Analysis”):
# Process the uploaded image
image_data = uploaded_file.getvalue()
# Create the prompt parts
prompt_parts = [
{“image”: image_data, “image/png”: image_data},
{“prompt”: “As a highly skilled medical practitioner specializing in image analysis, you are tasked with examining medical images for a renowned hospital. Your expertise is crucial in identifying any anomalies, diseases, or health issues that may be present in the image.”}
]
# Generate the response
response = model.generate(content=prompt_parts)
# Print the response
st.write(response.text)
```
Running the Application
We’ll run the application using Streamlit:
```
streamlit run app.py
```
https://github.com/keerthanans2006/Medical-Image-Detection/blob/main/Screenshot%20(4).png?raw=true

https://github.com/keerthanans2006/Medical-Image-Detection/blob/main/Screenshot%20(5).png?raw=true
