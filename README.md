#  Deep-Dive: Debugging Python with PyCharm on macOS (Local & Docker) 🐍

> [!IMPORTANT]
> Check my [blog post on genmind.ch](https://genmind.ch/posts/Deep-Dive-Debugging-Python-with-PyCharm-on-macOS/) to get detail instructions on how to use this repo.


A FastAPI-based DateTime API with advanced timezone conversion and business hours' functionality. This project serves as a comprehensive example for [debugging Python applications with PyCharm on macOS](https://genmind.ch/posts/Deep-Dive-Debugging-Python-with-PyCharm-on-macOS/), both locally and in Docker containers.

## Features

- ✅ Current UTC datetime retrieval with timezone conversion
- ✅ Multi-timezone conversion for any datetime
- ✅ Business hours checking across timezones
- ✅ Time difference calculations
- ✅ Comprehensive logging for debugging
- ✅ Full Docker support

## Quick Start

```bash
# Option 1: Local with conda
conda env create -f environment.yml
conda activate datetime-api
cd src && uvicorn main:app --reload

# Option 2: Docker
docker build -t datetime-api:latest -f src/Dockerfile src/
docker run -d -p 8000:8000 datetime-api:latest

# Option 3: Docker Compose
docker-compose up -d
```

Access the API: http://localhost:8000  
API Documentation: http://localhost:8000/docs

## API Endpoints

- `GET /` - API information
- `GET /datetime` - Current UTC datetime (with optional timezone conversion)
- `GET /datetime/convert` - Convert datetime to multiple timezones
- `GET /business-hours` - Check if current time is within business hours
- `GET /time-diff` - Calculate difference between two datetimes

## Debugging Guide 🐛

This project includes a comprehensive guide for debugging Python applications with PyCharm:

- **Quick Start**: See [`DEBUGGING_GUIDE.md`](DEBUGGING_GUIDE.md) for setup instructions
- **Full Blog Post**: See [Deep-Dive: Debugging Python with PyCharm on macOS (Local & Docker) on GenMind.ch](https://genmind.ch/posts/Deep-Dive-Debugging-Python-with-PyCharm-on-macOS/) for the complete debugging guide covering:
  - Local debugging with conda
  - Docker interpreter debugging
  - Docker Compose debugging
  - Remote debugging with Python Debug Server
  - Troubleshooting and best practices


## Testing the API

```bash
# Get current time in EST
curl "http://localhost:8000/datetime?tz=EST"

# Convert time to multiple timezones
curl "http://localhost:8000/datetime/convert?time_str=2024-11-21T15:00:00Z&timezones=EST,PST,JST"

# Check business hours
curl "http://localhost:8000/business-hours?tz=EST&start_hour=9&end_hour=17"
```
