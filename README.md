Whiz - Real-time Chat Application
A real-time chat application with channels using WebSockets.

Features
Real-time messaging using WebSockets
Channel-based communication
PostgreSQL database for persistent storage
Docker setup for easy deployment
Setup Instructions
Prerequisites
Go 1.20+
Node.js 16+
Docker and Docker Compose
Database Setup
Start the PostgreSQL database using Docker:
docker-compose up -d
This will start PostgreSQL on port 5432.

The migrations will be automatically applied when the server starts.
Backend Setup
Navigate to the backend directory:
cd backend
Install dependencies:
go mod download
Make sure your .env file is set up correctly:
# Server Configuration
PORT=8080

# Database Configuration
DB_HOST=localhost
DB_PORT=5432
DB_USER=postgres
DB_PASSWORD=postgres
DB_NAME=whiz

# API Keys (optional)
GEMINI_API_KEY=
Run the server:
go run cmd/server/main.go
Frontend Setup
Navigate to the frontend directory:
cd frontend
Install dependencies:
npm install
Start the development server:
npm start
The frontend will be available at http://localhost:3000.

Project Structure
backend/ - Go backend server

cmd/ - Application entry points
migrations/ - SQL database migrations
internal/ - Internal packages
api/ - API handlers
db/ - Database access
ws/ - WebSocket server
frontend/ - React frontend

src/ - Source code
api/ - API client
components/ - React components
contexts/ - React contexts
utils/ - Utility functions
Postman Testing Data
You can use the following requests to test the API endpoints:

Channels
Get All Channels
Method: GET
URL: http://localhost:8080/api/channels
Create Channel
Method: POST
URL: http://localhost:8080/api/channels
Body (JSON):
{
  "name": "tech-talk",
  "description": "Technology discussions"
}
Get Channel by ID
Method: GET
URL: http://localhost:8080/api/channels/1
Update Channel
Method: PUT
URL: http://localhost:8080/api/channels/1
Body (JSON):
{
  "name": "tech-discussions",
  "description": "All about technology"
}
Delete Channel
Method: DELETE
URL: http://localhost:8080/api/channels/1
Messages
Get All Messages in Channel
Method: GET
URL: http://localhost:8080/api/messages?channel_id=1
Create Message
Method: POST
URL: http://localhost:8080/api/messages
Body (JSON):
{
  "channel_id": 1,
  "content": "Hello world!",
  "parent_id": null
}
Get Message by ID
Method: GET
URL: http://localhost:8080/api/messages/1
Update Message
Method: PUT
URL: http://localhost:8080/api/messages/1
Body (JSON):
{
  "content": "Updated message content"
}
Delete Message
Method: DELETE
URL: http://localhost:8080/api/messages/1
Get Message Context (AI-generated)
Method: GET
URL: http://localhost:8080/api/messages/1/context
Summaries
Get Channel Summary
Method: GET
URL: http://localhost:8080/api/summaries/channel/1
Get Missed Messages Summary
Method: GET
URL: http://localhost:8080/api/summaries/missed/1/1
Development Notes
The application uses mock AI responses when no Gemini API key is provided
Database functionality can be disabled for demo/testing purposes
WebSocket server runs on port 8081 by default for real-time message updates
