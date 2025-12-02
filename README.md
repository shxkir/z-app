# ZaryahPlus App

This document provides instructions to run the backend (FastAPI + LangChain) and the frontend (Flutter) for the ZaryahPlus application.

## Prerequisites
- Python 3.11
- Flutter SDK
- A `.env` file with necessary API keys.

## Backend (FastAPI)

1.  **Navigate to the project directory:**
    From your terminal, change into the `ZRHPlus_v1` directory.
    ```bash
    cd path/to/ZRHPlus_v1
    ```

2.  **Create and activate a Python virtual environment:**
    This isolates the project's dependencies.
    ```bash
    # For macOS/Linux
    python3.11 -m venv .venv
    source .venv/bin/activate

    # For Windows
    # python -m venv .venv
    # .\.venv\Scripts\activate
    ```
    After activation, your command prompt should be prefixed with `(.venv)`.

3.  **Install dependencies:**
    ```bash
    pip install -r langchain_backend/requirements.txt
    ```

4.  **Configure environment variables:**
    Create a file named `.env` in the `ZRHPlus_v1` directory. It should contain your API keys and other configurations. An example structure is:
    ```
    # ZRHPlus_v1/.env
    API_KEY_1="your_secret_key"
    API_KEY_2="another_secret_key"
    NPY_SKIP_MACOS_CHECK=1
    ```

5.  **Start the API server:**
    The `HOST` and `PORT` can be adjusted if needed.
    ```bash
    HOST=0.0.0.0 PORT=8000 python langchain_backend/app/main.py
    ```

6.  **Verify the server is running:**
    Open a new terminal and run the following command. You should see a success message.
    ```bash
    curl http://localhost:8000/health
    ```

## Frontend (Flutter)

1.  **Configure backend connection:**
    - In `lib/core/config/app_config.dart`, set `ipv4` to your machine's local IP address (e.g., `192.168.1.10`) and `backendPort` to `8000` (or the port you used for the backend). Use `localhost` for `ipv4` if you are running the frontend in a web browser on the same machine.
    - In your `.env` file at the project root, ensure you have `BACKEND_URL=http://<your-ip>:8000`.

2.  **Install dependencies and run the app:**
```
cd ZRHPlus_v1
python3.11 -m venv .venv
source .venv/bin/activate
pip install -r langchain_backend/requirements.txt
```
2) Configure environment: ensure `.env` exists at `ZRHPlus_v1/.env` with your keys and `NPY_SKIP_MACOS_CHECK=1`.
3) Start the API (adjust HOST/PORT if needed):
```
NPY_SKIP_MACOS_CHECK=1 HOST=0.0.0.0 PORT=8000 python langchain_backend/app/main.py
```
4) Verify:
```
curl http://localhost:8000/health
```

## Frontend (Flutter)
1) Set `lib/core/config/app_config.dart` -> `ipv4` to your machine IP (or `localhost` for web) and `backendPort` to `8000` (or the port you use).
2) Ensure `.env` has `BACKEND_URL=http://<your-ip>:8000`.
3) Install deps and run:
```
flutter pub get
flutter run -d chrome   # or pick your device
```

Tip: First Flutter web build can take a few minutes; subsequent runs are faster.
