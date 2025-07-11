




#### Introduction
FastAPI is a modern web framework designed for building APIs with Python. It is known for its high performance, ease of use, and automatic generation of API documentation. The framework is particularly beneficial for building custom API endpoints, and it has become popular in recent times due to its support for AI and generative applications.

In this guide, we will explore the basics of FastAPI, how to set it up in your system, and how to create custom endpoints. We will also discuss how FastAPI simplifies the process of API development and how to execute FastAPI applications.

#### Table of Contents
1. What is FastAPI?
2. Why Use FastAPI?
3. Basic Setup of FastAPI
4. Creating Custom API Endpoints
5. FastAPI Documentation (Swagger)
6. Running and Stopping FastAPI Applications
7. Conclusion


### 1. What is FastAPI?
FastAPI is a Python web framework designed for building APIs. It is fast, easy to use, and supports asynchronous operations. FastAPI automatically generates interactive documentation for your APIs, making it easy to test and understand the endpoints.

#### Key Features of FastAPI:
* Asynchronous support: Handles multiple requests simultaneously.
* Automatic API Documentation (Swagger): FastAPI generates interactive API documentation automatically, making it easy to understand and use.
* High performance: Due to its asynchronous nature, FastAPI is highly performant compared to other Python web frameworks.


### 2. Why Use FastAPI?
There are several reasons why FastAPI has become the preferred choice for API development:

* Ease of Use: FastAPI is beginner-friendly and provides a simple way to build APIs.
* Integration with AI and Generative AI: FastAPI facilitates the development of AI-powered applications, making it highly relevant for AI developers.
* Scalability and Security: FastAPI's scalability and security features make it ideal for both small and large-scale projects.

FastAPI is suitable for projects ranging from basic web apps to complex machine learning models.

### 3. Basic Setup of FastAPI
To get started with FastAPI, follow the steps below for setting up the environment and creating your first FastAPI application.

#### Step 1: Install FastAPI and Uvicorn
To use FastAPI, we need to install it along with Uvicorn, which is an ASGI server used to run FastAPI applications.

```bash
pip install fastapi uvicorn
```

#### Step 2: Create a FastAPI Application
Once you have installed FastAPI, create a Python file (e.g., app.py). Here's how you can define a simple "Hello World" FastAPI app:

```bash
from fastapi import FastAPI
app = FastAPI(title="My First API", description="A Simple API Using FastAPI", version="1.0.0")

@app.get("/")

def read_root():

    return {"message": "Hello, World! Welcome to FastAPI"}
```    

#### Step 3: Run the FastAPI Application
To run the FastAPI application, use the Uvicorn server. You can do this by executing the following command in your terminal:
```bash
uvicorn app:app --reload
```
The --reload option ensures that the server automatically restarts whenever you make changes to the code.

#### 4. Creating Custom API Endpoints
FastAPI allows you to create custom API endpoints easily. Here's an example of creating a custom endpoint where the user can input their name, and the API will return a greeting message.

```bash
@app.get("/hello/{name}")

def read_item(name: str):

    return {"message": f"Hello, {name}!"}
```   
##### Explanation:
* @app.get("/hello/{name}"): This defines the GET endpoint /hello/{name}.
* The name parameter is passed as part of the URL, and the function returns a greeting message. 

To test this endpoint, run the server and visit the URL in the browser: http://127.0.0.1:8000/hello/YourName.

### 5. FastAPI Documentation (Swagger)
FastAPI automatically generates documentation for your API. This documentation is known as Swagger and provides a user-friendly interface to interact with your API.

* To access the documentation, simply add /docs to your FastAPI app's
URL: http://127.0.0.1:8000/docs.
* FastAPI also provides an alternative interactive documentation 
at /redoc: http://127.0.0.1:8000/redoc.

In the documentation, you'll find:

* The API's title, description, and version.
* A list of available endpoints.
* Options to test the endpoints interactively.


### 6. Running and Stopping FastAPI Applications
#### Running the FastAPI Application
To run the FastAPI application, use the following command:

```bash
uvicorn app:app --reload
```

#### Stopping the FastAPI Application
To stop the FastAPI server, press CTRL + C in the terminal where the server is running.

### 7. Conclusion
In this guide, we covered the basics of FastAPI, including setting up the environment, creating custom API endpoints, and using FastAPI's automatic documentation. We also explored how to run and stop FastAPI applications.
FastAPI is a powerful tool for building APIs and offers several advantages, such as ease of use, high performance, and automatic API documentation. As you become more familiar with FastAPI, you'll be able to create more complex endpoints and even develop applications for AI and machine learning.
In future lectures, we will explore more advanced FastAPI topics and develop projects to apply everything we've learned.
