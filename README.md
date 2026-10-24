# Inventory AI Agent - EECE 430 Assignment 5

A Dockerized version of the Lab 3 inventory agent, built with Django, Google Gemini and SQLite.

## Features

- Check stock quantities and item prices.
- Add or remove stock, update prices and delete items.
- Manage inventory through a chat interface with conversation history.

## Technologies Used

Python 3.13, Django 6.1.1, Google Gen AI SDK, SQLite and Docker.

## Setup

Docker Desktop must be running with Linux containers enabled.

Clone the repository and open the project directory:

```powershell
git clone https://github.com/hsn-28/eece430-assignment5-hassan-hashem.git
cd eece430-assignment5-hassan-hashem
```

Create a local `.env` file from `.env.example` and configure:

- `GEMINI_API_KEY`: a valid key with access to `gemini-3.8-flash`.
- `DJANGO_SECRET_KEY`: a private random value.

The `.env` file and database files are excluded from Git and the Docker image.

## Build and Run

From the project directory:

```powershell
docker build -t inventory-agent .
docker run -d --name inventory-agent -p 8000:8000 --env-file .env inventory-agent
```

Open http://localhost:8000/.

Database migrations run automatically at startup.

To view logs, stop or restart the container:

```powershell
docker logs inventory-agent
docker stop inventory-agent
docker start inventory-agent
```

## Example Requests

- "Add 10 rolls of Packing Tape."
- "Set the price of Packing Tape to 2.00."
- "What is the cost of 3 rolls of Packing Tape after adding 10% VAT?"
- "How many rolls of Packing Tape are in stock?"
- "Increase the price of Packing Tape by 50%."

For the VAT example, a unit price of `2.00` gives an expected total of `6.60`.

## Project Structure

```text
chat/              Agent, inventory tools, models, views and templates
config/            Django settings and URL configuration
manage.py          Django management commands
Dockerfile         Docker build and startup instructions
requirements.txt   Python dependencies
.env.example       Environment variable template
.dockerignore      Files excluded from the Docker image
.gitignore         Files excluded from Git
```