
### Introduction
In this Lecture, we will explore the creation and execution of a FastAPI application, focusing on a text processing API. The API performs a series of tasks, including string manipulation and validation, and also returns the processed text along with its length. We will cover the process of making custom API endpoints, handling user input, validating data, and using FastAPI's built-in features such as automatic API documentation generation. The purpose of this application is to showcase FastAPI's efficiency and flexibility in handling complex operations.

### Key Concepts

#### 1. API Endpoints
 FastAPI allows the creation of custom endpoints that send requests to a server and return a response based on the user's input. These endpoints can be customized with the appropriate parameters and validation mechanisms.

#### 2. GET vs POST Methods
* GET Method: Retrieves data from the server. This was used initially for basic display, like showing a "Hello World" message.
* POST Method: Sends data to the server for processing. In this case, the POST method processes the input string and returns the processed result along with its length.
