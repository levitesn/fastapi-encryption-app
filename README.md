# FastAPI Encryption Service

This is a FastAPI application that provides endpoints for encrypting and decrypting data using the `cryptography` library. The application includes two endpoints:
- `/encrypt`: Encrypts input data and returns the encrypted data.
- `/decrypt`: Decrypts input data and returns the decrypted data.

## Prerequisites

- Docker
- Docker Compose (optional, if you want to use it)
- Python 3.6+ (Python 3.11 was used for development)

## Installation

### Using Docker

1. **Clone the repository**:
    ```bash
    git clone https://github.com/levitesn/fastapi-encryption-app
    cd fastapi-encryption-app
    ```

2. **Build the Docker image**:
    ```bash
    docker build -t fastapi-encryption-app .
    ```

3. **Run the Docker container**:
    ```bash
    docker run -p 8001:8001 fastapi-encryption-app
    ```

The application will be accessible at `http://localhost:8001`.

### Without Docker

1. **Clone the repository**:
    ```bash
    git clone https://github.com/levitesn/fastapi-encryption-app
    cd fastapi-encryption-app
    ```

2. **Create a virtual environment and activate it**:
    ```bash
    python3 -m venv venv
    source venv/bin/activate
    ```

3. **Install the dependencies**:
    ```bash
    pip install -r requirements.txt
    ```

4. **Run the application**:
    ```bash
    uvicorn app:app --host 0.0.0.0 --port 8001
    ```

The application will be accessible at `http://localhost:8001`.

## Endpoints

### `/encrypt` (POST)
Encrypts the input data.

- **Request Body**: Raw binary data
- **Response**: JSON object containing the encrypted data as a base64-encoded string.

### `/decrypt` (POST)
Decrypts the input data.

- **Request Body**: JSON object containing the `encrypted_data` field with the base64-encoded encrypted data.
- **Response**: JSON object containing the decrypted data as a string.

## OpenAPI Specification

The OpenAPI specification for this application is provided in the `openapi.yaml` file. You can view the auto-generated API documentation by visiting `http://localhost:8001/docs` when the application is running.

## Example Calls in Python

You can use the `requests` library in Python to interact with the `/encrypt` and `/decrypt` endpoints of this FastAPI application.

First, ensure you have the `requests` library installed. You can install it using:

```bash
pip install requests
````

Here are some example calls to the endpoints:

```python
import requests

# Define the data to be encrypted
data_to_encrypt = b"Test data for encryption"

# Send a POST request to the /encrypt endpoint
response = requests.post("http://localhost:8001/encrypt", data=data_to_encrypt)

# Check if the request was successful
if response.status_code == 200:
    encrypted_data = response.json()["encrypted_data"]
    print(f"Encrypted Data: {encrypted_data}")
else:
    print(f"Failed to encrypt data: {response.status_code} - {response.text}")
```

 ```python
import requests

# Assume we have the encrypted data from the previous step
encrypted_data = "..."  # Replace with the actual encrypted data

# Send a POST request to the /decrypt endpoint
response = requests.post("http://localhost:8001/decrypt", json={"encrypted_data": encrypted_data})

# Check if the request was successful
if response.status_code == 200:
    decrypted_data = response.json()["decrypted_data"]
    print(f"Decrypted Data: {decrypted_data}")
else:
    print(f"Failed to decrypt data: {response.status_code} - {response.text}")
```

## Running Tests

To run the tests, you need to have `pytest` installed. You can install it using:

```bash
pip install pytest

# Run the tests
pytest test_app.py
```