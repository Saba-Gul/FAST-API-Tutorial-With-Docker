# Leveraging FastAPI With Docker

This is a simple FastAPI project that demonstrates basic API endpoints. The application provides a set of routes, including basic arithmetic, string manipulation, and a password checker.

## Features

- **Root Endpoint:** Returns a simple "Hello World" message.
- **Even Number Generator:** Generates a string of even numbers.
- **Password Checker:** Validates a username and password.

## Getting Started

### Prerequisites

Make sure you have Python 3.7+ installed on your system. You also need to install the necessary dependencies, such as FastAPI, Uvicorn, and Nest Asyncio.

### Installation

1. **Clone the repository:**

   ```bash
   git clone https://github.com/your-username/your-repo-name.git
   cd your-repo-name
   ```

2. **Create a virtual environment:**

   ```bash
   python3 -m venv venv
   source venv/bin/activate  # On Windows use `venv\Scripts\activate`
   ```

3. **Install the required packages:**

   ```bash
   pip install -r requirements.txt
   ```

### Running the Application

To run the FastAPI application, use the following command:

```bash
uvicorn main:app --reload
```

This will start the server, and you can access the API at `http://127.0.0.1:8000`.

### Dockerization

You can also run this FastAPI application using Docker.

1. **Build the Docker image:**

   ```bash
   docker build -t fastapi-app .
   ```

2. **Run the Docker container:**

   ```bash
   docker run -d -p 8000:8000 fastapi-app
   ```

   The application will be accessible at `http://localhost:8000`.

### Dockerfile

The project includes a `Dockerfile` that sets up the environment for running the FastAPI application in a Docker container:

```Dockerfile
# Use the official Python 3.9 slim image as the base image
# This is a lightweight version of Python with only the essential libraries
FROM python:3.9-slim

# Set the working directory inside the container to /app
# All subsequent commands will be run in this directory
WORKDIR /app

# Copy the contents of the current directory (your project files) into the /app directory in the container
COPY . /app

# Install the Python dependencies listed in requirements.txt
# This ensures that all necessary packages for your FastAPI app are installed
RUN pip install -r requirements.txt

# Define the command to run the application
# Uvicorn is used to serve the FastAPI application, with auto-reload enabled, on port 8000 and host 0.0.0.0
CMD uvicorn main:app --reload --port=8000 --host=0.0.0.0
```

### Summary of Each Line:
1. **`FROM python:3.9-slim`:** Specifies the base image as Python 3.9-slim, which is a minimal version of Python.
2. **`WORKDIR /app`:** Sets `/app` as the working directory inside the container.
3. **`COPY . /app`:** Copies the application code from the current directory on your local machine to the `/app` directory in the container.
4. **`RUN pip install -r requirements.txt`:** Installs all the Python packages listed in the `requirements.txt` file.
5. **`CMD uvicorn main:app --reload --port=8000 --host=0.0.0.0`:** Runs the FastAPI application using Uvicorn with the specified settings (reload on changes, port 8000, accessible on any network interface).
### Available Endpoints

#### Root Endpoint

- **URL:** `/`
- **Method:** `GET`
- **Description:** Returns a simple message: "Hello World".

#### Even Number Generator

- **URL:** `/enwi`
- **Method:** `GET`
- **Description:** Generates a string of even numbers from 0 to 18.

#### Password Checker

- **URL:** `/a/{name}/{password}`
- **Method:** `GET`
- **Description:** Validates a username and password. The correct combination is "abc" and "123".

### Example Usage

You can test the endpoints using Postman or `cURL`.

#### Using Postman

1. **Root Endpoint:**
   - Method: `GET`
   - URL: `http://127.0.0.1:8000/`

2. **Even Number Generator:**
   - Method: `GET`
   - URL: `http://127.0.0.1:8000/enwi`

3. **Password Checker:**
   - Method: `GET`
   - URL: `http://127.0.0.1:8000/a/abc/123`

#### Using `cURL`

1. **Root Endpoint:**
   ```bash
   curl -X GET "http://127.0.0.1:8000/"
   ```

2. **Even Number Generator:**
   ```bash
   curl -X GET "http://127.0.0.1:8000/enwi"
   ```

3. **Password Checker:**
   ```bash
   curl -X GET "http://127.0.0.1:8000/a/abc/123"
   ```

### Additional Information

- **Project Structure:**
  - `main.py`: The main FastAPI application file.
  - `Dockerfile`: The Dockerfile for containerizing the application.
  - `requirements.txt`: The file containing the list of dependencies.

- **Dependencies:**
  - `FastAPI`: A modern, fast (high-performance) web framework for building APIs with Python.
  - `Uvicorn`: An ASGI server implementation, using `uvloop` and `httptools`.
  - `Nest Asyncio`: Allows running async functions in environments where event loops are already running.


