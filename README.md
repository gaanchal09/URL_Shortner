# URL_Shortner

A simple URL Shortener service built with Python and Flask.  
This API lets you shorten long URLs into 6-character short codes, redirect using these short URLs, and track analytics like click counts.

## Features

- Shorten long URLs to unique 6-character short codes.
- Redirect short URLs to the original long URLs.
- Track analytics: number of clicks, creation date, and the original URL.
- Validate URLs to accept only valid input.
- Thread-safe in-memory storage.
- Includes automated tests covering core functionality and error cases.

## Getting Started

### Prerequisites
```bash
- Python 3.8 or higher  
- pip (Python package manager)
```
### Installation

1. Clone the repository:
```bash
git clone https://github.com/your_username/url-shortener.git
cd url-shortener
```


2. Install dependencies:
```
pip install -r requirements.txt
```

## Running the Application

Start the Flask application:
```
python -m flask --app app.main run
```

This will start the server at http://localhost:5000

## API Endpoints

| Method | Endpoint               | Description                              | Request Body Example             |
|--------|------------------------|----------------------------------------|--------------------------------|
| POST   | `/api/shorten`         | Shorten a long URL                      | `{ "url": "https://example.com" }` |
| GET    | `/<short_code>`        | Redirect to the original long URL      |                                |
| GET    | `/api/stats/<short_code>` | Get analytics for a specific short code |                                |

### Example Usage

**Shorten a URL:**
```bash
curl -X POST http://localhost:5000/api/shorten
-H "Content-Type: application/json"
-d '{"url":"https://www.example.com"}'
```


**Response:**
{
"short_code": "a1B2c3",
"short_url": "http://localhost:5000/a1B2c3"
}



**Use the short URL:**
Open `http://localhost:5000/a1B2c3` in your browser to be redirected to the original URL.

**Get URL statistics:**
```bash
curl http://localhost:5000/api/stats/a1B2c3
```


**Example stats response:**
{
"url": "https://www.example.com",
"clicks": 5,
"created_at": "2025-07-23T10:15:00"
}

## Running Tests

Run all automated tests using:
```
pytest
```
## Project Structure

url-shortener/
│
├── app/
│ ├── init.py
│ ├── main.py # Flask app and endpoints
│ ├── models.py # Thread-safe URL storage
│ └── utils.py # Helper functions (URL validation, short code generation)
│
├── tests/
│ └── test_basic.py # Automated tests
│
├── requirements.txt # Project dependencies
└── README.md # This file



## Notes

- The app uses in-memory storage, so all shortened URLs will be lost on server restart.
- URL validation is basic; you can improve it as needed.
- This project is for learning and demonstration purposes, not production-ready.
- Feel free to extend with persistent storage, authentication, dashboard, etc.
