# Health RESTFUL API - Setup and Instructions

This document provides instructions on how to set up and run the Health RESTFUL API locally. The API is a Node.js/Express application connected to a MongoDB database.

## Requirements

- Python 3.x
- [virtualenv](https://virtualenv.pypa.io/en/latest/) for isolated environments
- [Node.js](https://nodejs.org/) (which includes npm)
- [MongoDB](https://www.mongodb.com/)

## Setup

### 1. Clone the repository

```bash
git clone https://github.com/AlejandroMoc/API_Restful
cd API_Restful
```

### 2. Create and activate a virtual environment

On Linux/macOS:

```sh
python3 -m venv venv
source venv/bin/activate
```

On Windows:

```sh
python -m venv venv
venv\Scripts\activate
```

### 3. Install the required packages

```sh
pip install -r requirements.txt
```

### 4. Database Setup (MongoDB)

Make sure a local MongoDB server (4.2 or newer) is running on port 27017, then create/use the corresponding database. The API connects to `retos_salud`, so use that database name.

```bash
mongosh
use retos_salud
```

> Note: If port 27017 is occupied by an SSH tunnel to an older MongoDB, stop the tunnel (or run `mongod` on a free port and update `src/utils/database.js`) so the driver can talk to a MongoDB 4.2+ server.

### 5. Run the API

```bash
# Start the API
npm run dev
```

The API should now be running, typically on port 3000. Check the terminal output for the exact URL.

## API Usage

Documentation about the endpoints can be found in [API.md](/doc/API.md).