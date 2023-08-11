
# Week 32 - Augest 2023


## 1. 👫 Strict separation of settings from code with Decouple

*Decouple* is a tool that assists in managing settings, allowing you to adjust parameters without the need to redeploy your application. It offers several benefits, such as the ability to store parameters in files like *ini* or *.env*, set up default values, ensure proper data type conversions, and centralize all configurations into a single module. Initially created for Django, it has evolved into a versatile tool for separating settings from the core code, making it applicable to various projects beyond Django.

**How to use in your project ?**

1. Install the package into your project environment.
```shell
pip install python-decouple
```
2. In your  `config.py`

```python
from decouple import config

SECRET_KEY = config('SECRET_KEY')
DEBUG = config('DEBUG', default=False, cast=bool)
EMAIL_HOST = config('EMAIL_HOST', default='localhost')
EMAIL_PORT = config('EMAIL_PORT', default=25, cast=int)
PAYMENT_GATEWAY_API_KEY = config('PAYMENT_GATEWAY_API_KEY', cast=str)
```

3. Now in your other modules where you need to use these values

```python
import config as cfg
print(cfg.EMAIL_HOST)

```

## 2. 🐍 Empower yourself with Pydantic

Pydantic is a powerful data validation library for Python that has gained significant popularity among developers due to its extensive features and ease of use.

1. Typehints powering schema validation: Pydantic leverages Python type hints to define the structure of data models.

2. Performance: The core is written in rust, making it superfast.

3. Serialization: Pydantic provides seamless serialization and deserialization of data models to and from JSON, dictionaries, and other data formats.

4. JSON Schema: JSON Schema is a standard for describing the structure of JSON data. Pydantic can automatically generate JSON Schema representations of your data models. This allows you to validate your data against a defined JSON Schema or share the schema with other systems.

5. Strict mode and data coercion: Pydantic supports a strict mode that enforces the data model's field types strictly. It also provides data coercion, allowing you to automatically convert data to the specified types whenever possible. This feature makes handling user inputs and external data sources more robust.


Let's consider a simple use case of using Pydantic to validate and serialize data for a User model:

```python
from pydantic import BaseModel

class User(BaseModel):
    username: str
    email: str
    age: int

# Valid data
user_data = {
    "username": "john_doe",
    "email": "john@example.com",
    "age": 30
}

# Creating a User instance from the data
user = User(**user_data)

# The instance is automatically validated and parsed
print(user.username)  # Output: john_doe
print(user.email)     # Output: john@example.com
print(user.age)       # Output: 30

# Invalid data - missing 'email' field
invalid_user_data = {
    "username": "jane_doe",
    "age": 25
}

# Trying to create a User instance with invalid data
try:
    invalid_user = User(**invalid_user_data)
except Exception as e:
    print(f"Error: {e}")
    # Output: Error: 1 validation error for User
    # email
    #   field required (type=value_error.missing)
```

In this example, we define a simple User model using Pydantic's BaseModel class and specify the expected types for each field (username, email, and age). When we create an instance of the User model with valid data, Pydantic automatically validates and parses the input. If the data is invalid, Pydantic raises an error with a helpful validation message.

Overall, Pydantic simplifies data validation, serialization, and parsing tasks, making it an invaluable tool for Python developers, especially in the context of web APIs, data processing, and data validation tasks. Its performance, type hint-based approach, and seamless integration with other libraries contribute to its widespread adoption in the Python ecosystem.


## 3. 🐃 Stable Diffusion WebUI

This project offers a browser interface based on Gradio library for Stable Diffusion.

Gradio is a library offered by HuggingFace to quickly develop web interfaces for ml apps.

In simple words you can generate images based on a prompt.

Refer to the [GitHub repository](https://github.com/AUTOMATIC1111/stable-diffusion-webui) to learn about installation and usage.

## 4. ✍️ Text Generation WebUI

This is a sibling project of the previous one. A gradio web UI for running Large Language Models like LLaMA, llama.cpp, GPT-J, OPT, and GALACTICA.

As per its documentation the key features are:

- 3 interface modes: default, notebook, and chat
- Multiple model backends: tranformers, llama.cpp, AutoGPTQ, GPTQ-for-LLaMa, ExLlama, RWKV, FlexGen
- Dropdown menu for quickly switching between different models

Refer to the [github repository](https://github.com/oobabooga/text-generation-webui) for learning how to install and use.


## 5. 🥇 Streamlit: A Python Library for Interactive Data Apps

In recent years, data visualization and interactive web applications have become essential tools for data scientists and developers. Creating intuitive and interactive data apps used to require extensive web development skills, but now, with the Streamlit Python library, anyone with basic Python knowledge can build powerful data-driven applications effortlessly.

**What is Streamlit?**

Streamlit is an open-source Python library that allows developers to create web applications for data exploration and visualization with minimal effort. It was designed to simplify the process of turning data scripts into shareable web apps, making it an excellent tool for showcasing data insights and machine learning models.

**Getting Started**

To use Streamlit, you need to have Python installed on your system. You can install Streamlit using pip:

```
pip install streamlit
```

**Creating Your First Streamlit App**

Once Streamlit is installed, creating a basic app is as simple as writing a few lines of Python code. Let's start by importing Streamlit and creating a simple app that displays a line chart:

```python
# app.py
import streamlit as st
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# Create a sample dataframe
data = pd.DataFrame({
    'x': np.arange(10),
    'y': np.random.randn(10)
})

# Add a title to the app
st.title('My First Streamlit App')

# Display the dataframe
st.dataframe(data)

# Create a line chart
plt.plot(data['x'], data['y'])
st.pyplot(plt)
```

Save this code in a file named `app.py`, and then run the app using the following command:

```
streamlit run app.py
```

A new tab will open in your default web browser, displaying your first Streamlit app. The app will show a DataFrame and a simple line chart based on the data provided.

**Customizing Your App**

One of the greatest strengths of Streamlit is its ability to respond to user inputs and generate dynamic visualizations accordingly. For instance, you can add widgets like sliders, buttons, and text inputs to allow users to interact with your app.

Here's an example of how to add a slider to control the number of data points displayed in the chart:

```python
# app.py
import streamlit as st
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# Create a sample dataframe
data = pd.DataFrame({
    'x': np.arange(100),
    'y': np.random.randn(100)
})

# Add a title to the app
st.title('Dynamic Chart with Streamlit')

# Add a slider for the number of data points
num_points = st.slider('Number of Data Points', 10, 100, 50)

# Display the selected number of data points in the DataFrame
st.dataframe(data.head(num_points))

# Create a dynamic line chart
plt.plot(data['x'][:num_points], data['y'][:num_points])
st.pyplot(plt)
```

Now, when you run the app again, you will see a slider that allows you to control the number of data points displayed in the line chart.

**Sharing Your App**

Once you've created your Streamlit app and are satisfied with its functionality, you can easily share it with others. You can deploy it on various platforms, including Streamlit Sharing, Heroku, or your own web server.

For example, if you want to deploy it on Streamlit Sharing, you can follow these steps:

1. Create a GitHub repository with your Streamlit app code.
2. Sign in to Streamlit Sharing (https://streamlit.io/sharing) using your GitHub account.
3. Connect your GitHub repository to Streamlit Sharing and set up the deployment settings.
4. Once connected, Streamlit Sharing will automatically build and deploy your app.

Now, you have a publicly accessible web link for your Streamlit app that you can share with anyone.

**Conclusion**

Streamlit is a game-changer in the world of data visualization and app development. Its simplicity and ease of use allow data scientists and developers to focus on presenting their data insights and models interactively without getting bogged down in web development complexities. With its increasing popularity and active community, Streamlit is likely to remain a popular choice for building interactive data applications in Python. So, if you want to create stunning and interactive data apps quickly, give Streamlit a try!


