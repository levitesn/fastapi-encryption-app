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
    git clone https://github.com/your-username/fastapi-encryption-app.git
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
    git clone https://github.com/your-username/fastapi-encryption-app.git
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

## Running Tests

To run the tests, you need to have `pytest` installed. You can install it using:

```bash
pip install pytest

# Run the tests
pytest test_app.py
```