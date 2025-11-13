# Meeting Minutes Application

The Meeting Minutes application automates the generation and storage of structured meeting minutes and action items from uploaded meeting transcripts. Built for the Defense Health Agency (DHA) as part of the SEMOSS PMO Portal.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Key Features](#key-features)
- [Technology Stack](#technology-stack)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [Deployment](#deployment)
- [Documentation](#documentation)
- [Contributing](#contributing)
- [License](#license)
- [Acknowledgments](#acknowledgments)

---

## Overview

The Meeting Minutes application automates the generation and storage of structured meeting minutes and action items from uploaded meeting transcripts. It leverages AI to process transcripts, extract key information, create professional meeting summaries, and maintain a historical database of all meetings. The application supports team management, topic organization, and collaborative workflows for distributed teams.

---

## Key Features

- **AI-Powered Generation**: Automatically generate meeting minutes from transcripts including title, attendees, executive summary, and action items
- **Transcript Upload**: Support for PDF, DOCX, and TXT formats with automatic text extraction
- **Action Item Tracking**: Extract and track action items with assignments, deadlines, and priority levels
- **Team & Topic Management**: Organize meetings by teams and topics with access control
- **Vector Database Storage**: Store transcripts in FAISS for semantic search and retrieval
- **PostgreSQL Database**: Persistent storage of meeting metadata, teams, and action items
- **Export Functionality**: Generate Word documents from meeting minutes
- **Search & Archive**: Search and access historical meeting records

---

## Technology Stack

- **Frontend**: React 18.3.1, TypeScript, Material UI v5
- **State Management**: MobX 6
- **Backend**: Java 8 with Maven
- **Database**: PostgreSQL v12+, FAISS vector database
- **Document Processing**: Mammoth.js, Marked v5, React-MDE v11
- **AI**: SEMOSS LLM integration
- **Build Tools**: pnpm v10.11.1, Webpack 5

---

## Installation

### 1. Database Setup

Create and configure the PostgreSQL database:

```bash
# Create PostgreSQL database
createdb pmo_meeting_minutes

# Connect to database and create schema
psql -U your_username -d pmo_meeting_minutes

# Create the pmomm schema (run SQL script if available)
CREATE SCHEMA pmomm;

# Create required tables for teams, topics, meetings, action items, etc.
# (Refer to schema.sql if provided)
```

### 2. Frontend Setup

```bash
# Navigate to client directory
cd assets/client

# Install dependencies using pnpm
pnpm install
```

### 3. Backend Setup

```bash
# Navigate to backend directory
cd assets/meeting-minutes-be

# Clean and install Maven dependencies
mvn clean install
```

---

## Configuration

Create `.env` file in `assets/client`:
```env
MODULE="/Monolith"
ENDPOINT="https://your-govconnect-instance.ai"
APP="your-meeting-minutes-app-id"
MODEL="your-llm-model-id"
EMBEDDER_ENGINE="your-embedder-engine-id"
NODE_ENV=development
PORT=3001
```

Edit `assets/meeting-minutes-be/project.properties`:
```properties
client=Meeting_Minutes
version=0.0.1
projectId=your-app-id-here
```

---

## Usage

### Starting Development Server

```bash
# In assets/client directory
pnpm install
pnpm run dev

# Application will be available at http://localhost:3001
```

### Workflow

1. **Setup**: Create or join teams and subscribe to topics
2. **Create**: Enter meeting name, date, team, and topic
3. **Upload**: Upload transcript file (PDF, DOCX, TXT)
4. **Generate**: AI processes transcript and creates meeting minutes with action items
5. **Review & Edit**: Review and modify generated minutes in markdown editor
6. **Save & Export**: Save to database and export to Word document
7. **Archive**: Search and access historical meeting records

### Building for Production

```bash
# Build frontend
cd assets/client
pnpm build
# Output: portals/ directory with compiled assets

# Build backend
cd assets/meeting-minutes-be
mvn clean package
# Output: target/meetingminutes-0.0.1.jar
```

---

## Deployment

Deploy to Govconnect.ai following standard SEMOSS deployment process:
1. Build frontend and backend
2. Create deployment package with portals, assets, and metadata files
3. Upload to Govconnect.ai and configure environment variables
4. Compile reactors and publish the application

---

## Documentation

- **Code Style Guide**: `assets/client/CodeStyle.md` - Coding standards and best practices
- **SEMOSS Documentation**: [https://semoss.org/docs](https://semoss.org/docs) - SEMOSS SDK reference
- **React Documentation**: [https://react.dev](https://react.dev) - React framework guide
- **Material UI Documentation**: [https://mui.com](https://mui.com) - UI component library

---

## Contributing

Contributions are welcome! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for detailed guidelines on how to contribute to this project.

---

## License

This project is proprietary software developed for the Defense Health Agency (DHA). All rights reserved.

This software is licensed for use exclusively by Defense Health Agency (DHA) personnel, authorized contractors, and government entities with proper authorization.

---

## Acknowledgments

This project is built using the following technologies:

**Core Technologies**:
- [React](https://react.dev) 18.3.1 with [TypeScript](https://www.typescriptlang.org)
- [Material UI](https://mui.com) v5 for UI components
- [MobX](https://mobx.js.org) 6 for state management
- [SEMOSS](https://semoss.org) AI platform for LLM integration
- [PostgreSQL](https://www.postgresql.org) v12+ and FAISS for data storage
- Java 8 with [Apache Maven](https://maven.apache.org) for backend services

---
