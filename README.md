# Lottery Prediction Service
https://workforakng.github.io/prediction/
This repository contains the backend (Flask API) and worker service for a lottery prediction application. It operates continuously to provide updated predictions.
Its files are private(Will update soon)

## Table of Contents

-   [Features](#features)
-   [Architecture](#architecture)
-   [Operation](#operation)
-   [API Endpoints](#api-endpoints)
-   [Contributing](#contributing)

## Features

* **Lottery Prediction:** Generates and stores lottery predictions.
* **Data Storage:** Utilizes a high-performance, in-memory data store for predictions, historical data, and service status.
* **AI Toggle:** Allows enabling or disabling AI-based predictions via an API.
* **Status Monitoring:** Provides API endpoints to check the service status and retrieve the latest prediction updates.
* **Secure Communication:** Configured for secure cross-origin resource sharing with authorized frontend applications.

## Architecture

The service consists of two primary components:

1.  **API Service:**
    * A Flask application that exposes RESTful API endpoints for interaction with frontends.
    * Retrieves and serves prediction data from the data store.
    * Manages AI toggle requests.

2.  **Worker Service:**
    * Runs the core prediction logic.
    * Fetches and processes historical lottery data.
    * Executes prediction algorithms (including AI models).
    * Stores the latest predictions and related analytical data into the central data store. This worker updates the data store, saving information like history, predictions, number statistics, trend analysis, and streaks.

3.  **Data Store:**
    * A fast, in-memory database used for quick access to various data points, including:
        * The latest prediction data.
        * Historical lottery information.
        * Prediction results and statistics.
        * AI enabled/disabled status.

## Operation

This service is designed for continuous, automated operation. The worker service runs an auto-running prediction cycle approximately every 30 seconds, 24/7. This ensures that the predictions and service status are regularly updated and available.

## API Endpoints

All API endpoints are prefixed with `/api`.

* **`GET /api/prediction`**
    * Retrieves the latest lottery prediction data.
    * **Response:** JSON object containing prediction data, timestamp, and AI status.
* **`GET /api/status`**
    * Provides the current operational status of the prediction service.
    * **Response:** JSON object with service status, last update timestamp, and AI status.
* **`GET /api/ai/status`**
    * Checks if the AI prediction is currently active.
    * **Response:** `{"ai_enabled": true/false}`
* **`POST /api/ai/start`**
    * Activates AI-based predictions.
    * **Response:** `{"status": "success", "ai_enabled": true}`
* **`POST /api/ai/stop`**
    * Deactivates AI-based predictions.
    * **Response:** `{"status": "success", "ai_enabled": false}`

## Contributing

Contributions are welcome! Please feel free to open issues or submit pull requests.

