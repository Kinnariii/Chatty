# Whiz - Real-time Chat Application

Whiz is a real-time chat application built using **Go**, **React**, **PostgreSQL**, and **WebSockets**. It provides channel-based messaging with persistent storage and AI-powered conversation summaries. The application is designed with a modular architecture, making it easy to develop, maintain, and extend.

---

## Features

* Real-time messaging using WebSockets
* Channel-based communication
* Threaded conversations
* Persistent message storage with PostgreSQL
* RESTful API for channels and messages
* AI-generated message context and conversation summaries
* Docker support for quick local deployment
* Modular backend architecture in Go

---

## Tech Stack

### Frontend

* React
* JavaScript
* CSS

### Backend

* Go
* Gorilla WebSocket
* REST API

### Database

* PostgreSQL

### AI Integration

* Google Gemini API (Optional)

### DevOps

* Docker
* Docker Compose

---

## Project Structure

```text
Whiz/
│
├── backend/
│   ├── cmd/
│   │   └── server/
│   ├── internal/
│   │   ├── api/
│   │   ├── db/
│   │   └── ws/
│   └── migrations/
│
├── frontend/
│   ├── src/
│   │   ├── api/
│   │   ├── components/
│   │   ├── contexts/
│   │   └── utils/
│
├── docker-compose.yml
└── README.md
```

---

## Prerequisites

Ensure the following are installed:

* Go 1.20 or later
* Node.js 16 or later
* Docker
* Docker Compose

---

## Database Setup

Start PostgreSQL using Docker:

```bash
docker-compose up -d
```

This starts PostgreSQL on **localhost:5432**.

Database migrations are automatically applied when the backend starts.

---

## Backend Setup

Navigate to the backend directory:

```bash
cd backend
```

Install dependencies:

```bash
go mod download
```

Create a `.env` file with the following configuration:

```env
PORT=8080

DB_HOST=localhost
DB_PORT=5432
DB_USER=postgres
DB_PASSWORD=postgres
DB_NAME=whiz

GEMINI_API_KEY=
```

Run the server:

```bash
go run cmd/server/main.go
```

The backend will be available at:

```text
http://localhost:8080
```

---

## Frontend Setup

Navigate to the frontend directory:

```bash
cd frontend
```

Install dependencies:

```bash
npm install
```

Start the development server:

```bash
npm start
```

The frontend will be available at:

```text
http://localhost:3000
```

---

## WebSocket Server

The WebSocket server runs on:

```text
ws://localhost:8081
```

It is responsible for:

* Real-time messaging
* Live channel updates
* Instant synchronization between connected clients

---

## API Endpoints

### Channels

| Method | Endpoint             | Description           |
| ------ | -------------------- | --------------------- |
| GET    | `/api/channels`      | Retrieve all channels |
| POST   | `/api/channels`      | Create a new channel  |
| GET    | `/api/channels/{id}` | Retrieve a channel    |
| PUT    | `/api/channels/{id}` | Update a channel      |
| DELETE | `/api/channels/{id}` | Delete a channel      |

### Messages

| Method | Endpoint                     | Description               |
| ------ | ---------------------------- | ------------------------- |
| GET    | `/api/messages?channel_id=1` | Retrieve channel messages |
| POST   | `/api/messages`              | Create a message          |
| GET    | `/api/messages/{id}`         | Retrieve a message        |
| PUT    | `/api/messages/{id}`         | Update a message          |
| DELETE | `/api/messages/{id}`         | Delete a message          |
| GET    | `/api/messages/{id}/context` | Generate AI context       |

### Summaries

| Method | Endpoint                                                | Description                |
| ------ | ------------------------------------------------------- | -------------------------- |
| GET    | `/api/summaries/channel/{channelId}`                    | Generate a channel summary |
| GET    | `/api/summaries/missed/{channelId}/{lastSeenMessageId}` | Summarize missed messages  |

---

## Sample Requests

### Create a Channel

```http
POST /api/channels
```

```json
{
  "name": "tech-talk",
  "description": "Technology discussions"
}
```

### Create a Message

```http
POST /api/messages
```

```json
{
  "channel_id": 1,
  "content": "Hello World!",
  "parent_id": null
}
```

---

## Development Notes

* AI functionality works with the Google Gemini API.
* If no Gemini API key is provided, mock AI responses are returned.
* Database migrations run automatically during backend startup.
* Docker Compose provides a complete local PostgreSQL environment.
* The WebSocket server enables real-time synchronization across connected clients.

---

## Running the Application

Start the PostgreSQL container:

```bash
docker-compose up -d
```

Start the backend:

```bash
cd backend
go run cmd/server/main.go
```

Start the frontend:

```bash
cd frontend
npm install
npm start
```

Application URLs:

```text
Frontend   : http://localhost:3000
Backend    : http://localhost:8080
WebSocket  : ws://localhost:8081
```

---

## Future Improvements

* User authentication
* Private messaging
* Read receipts
* Typing indicators
* Emoji reactions
* File and image sharing
* User presence status
* Push notifications
* Message search
* Voice and video calling

---

