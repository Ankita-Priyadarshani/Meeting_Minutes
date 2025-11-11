# Meeting Minutes Application

The Meeting Minutes application automates the generation and storage of structured meeting minutes and action items from uploaded meeting transcripts. Built for the Defense Health Agency (DHA) as part of the SEMOSS PMO Portal.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Key Features](#key-features)
- [Technology Stack](#technology-stack)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [Deployment](#deployment)
- [Quick Start](#quick-start)
- [Documentation](#documentation)
- [Contributing](#contributing)
- [License](#license)
- [Contact & Support](#contact--support)
- [Acknowledgments](#acknowledgments)

---

## Overview

The Meeting Minutes application automates the generation and storage of structured meeting minutes and action items from uploaded meeting transcripts. It leverages AI to process transcripts, extract key information, create professional meeting summaries, and maintain a historical database of all meetings. The application supports team management, topic organization, and collaborative workflows for distributed teams.

---

## Key Features

- **Transcript Upload & Processing**: Upload meeting transcripts in multiple formats (PDF, DOCX, TXT) with automatic text extraction
- **AI-Powered Generation**: Automatically generate comprehensive meeting minutes including:
  - Meeting title and purpose
  - Table of attendees
  - Executive summary with key decisions
  - Structured action items with assignees, due dates, and priorities
- **Vector Database Storage**: Store transcripts in FAISS vector databases for semantic search and retrieval
- **Team & Topic Management**: Organize meetings by teams and topics with granular access control
- **Action Item Tracking**: Extract and track action items with assignments, deadlines, and priority levels
- **PostgreSQL Database**: Persistent storage of meeting metadata, attendees, teams, and topics
- **Search & Archive**: Search historical meeting records and access past minutes
- **Export Functionality**: Generate professional Word documents from meeting minutes
- **User Management**: Role-based access with team membership and topic subscriptions
- **Collaborative Workflow**: Multiple users can create, view, and manage meetings within their teams

---

## Technology Stack

- **Frontend**: React 18.3.1, TypeScript, Material UI v5
- **State Management**: MobX 6 with MobX React Lite
- **Form Handling**: React Hook Form v7
- **Backend**: Java 8 with Maven
- **Database**: PostgreSQL v12+ for relational data
- **Vector Storage**: FAISS (Facebook AI Similarity Search) via SEMOSS
- **Document Processing**: Mammoth.js (DOCX), PDF parsing libraries
- **Markdown Rendering**: Marked v5, React-MDE v11
- **AI Models**: SEMOSS LLM integration (Guanaco or custom models)
- **Build Tools**: pnpm v10.11.1, Webpack 5
- **HTTP Client**: Axios v0.24.0

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

**Frontend Configuration** - Create `.env` file in `assets/client`:
```env
# SEMOSS Configuration
MODULE="/Monolith"
ENDPOINT="https://your-govconnect-instance.ai"
APP="your-meeting-minutes-app-id"

# Model Configuration
MODEL="your-llm-model-id"
EMBEDDER_ENGINE="your-embedder-engine-id"

# Optional: Development settings
NODE_ENV=development
PORT=3001
```

**Backend Configuration** - Edit `assets/meeting-minutes-be/project.properties`:
```properties
client=Meeting_Minutes
version=0.0.1
projectId=your-app-id-here
SemossProjectPath=/path/to/semoss/project
```

**Database Configuration** - Update database connection in backend configuration:
```properties
# PostgreSQL connection details
DB_HOST=localhost
DB_PORT=5432
DB_NAME=pmo_meeting_minutes
DB_USER=your_username
DB_PASSWORD=your_password
DB_SCHEMA=pmomm
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

**1. Login & Team Setup**
   - Log in to the application using your credentials
   - Navigate to Team Management to create or join teams
   - Subscribe to relevant topics within your teams

**2. Create New Meeting Minutes**
   - Navigate to the Meeting Minutes creation page
   - Select your team and topic from dropdowns
   - Enter meeting name and date

**3. Upload Meeting Transcript**
   - Click "Upload Document" or drag-and-drop your transcript file
   - Supported formats: PDF, DOCX, TXT
   - The application will extract text automatically

**4. Generate Meeting Minutes**
   - Click "Generate Minutes" to process the transcript with AI
   - The system will create:
     - Meeting title and purpose
     - Attendee list
     - Executive summary with key decisions
     - Action items table with assignments

**5. Review & Edit**
   - Review the generated minutes in the markdown editor
   - Make any necessary edits or corrections
   - The markdown preview updates in real-time

**6. Create Action Items**
   - Extracted action items are automatically parsed
   - Review and assign action items to team members
   - Set priorities (Low, Medium, High) and due dates
   - Action items are stored in PostgreSQL for tracking

**7. Save & Export**
   - Save the meeting minutes to the database
   - The transcript is stored in a vector database for semantic search
   - Export to Word document for distribution

**8. Access Archive**
   - Navigate to Meeting Archive to view past meetings
   - Search by team, topic, date, or keywords
   - Access full meeting minutes and action items

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

Follow the standard SEMOSS deployment process to Govconnect.ai:
1. Build the application (frontend and backend)
2. Set up PostgreSQL database and run schema initialization
3. Create deployment package with portals, assets, and metadata files
4. Upload to Govconnect.ai and configure environment variables (including database credentials)
5. Compile reactors and publish the application

---

## Documentation

### Additional Resources

- **Comprehensive Documentation**: See `_PMO_Documentation.pptx` in the project root for detailed information about the application, including architecture diagrams, user guides, and deployment procedures
- **Code Style Guide**: Review `assets/client/CodeStyle.md` for coding standards and best practices
- **SEMOSS SDK Documentation**: [https://semoss.org/docs](https://semoss.org/docs) - Official SDK documentation
- **Material UI Documentation**: [https://mui.com](https://mui.com) - Component library reference
- **React Documentation**: [https://react.dev](https://react.dev) - React framework guide
- **TypeScript Documentation**: [https://www.typescriptlang.org/docs](https://www.typescriptlang.org/docs) - TypeScript language reference
- **MobX Documentation**: [https://mobx.js.org](https://mobx.js.org) - State management guide
- **React Hook Form**: [https://react-hook-form.com](https://react-hook-form.com) - Form handling documentation

---

## Contributing

Contributions are welcome! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for detailed guidelines on how to contribute to this project

---

## License

This project is proprietary software developed for the Defense Health Agency (DHA). All rights reserved.

### Usage Rights

This software is licensed for use exclusively by:
- Defense Health Agency (DHA) personnel
- Authorized contractors working on DHA projects
- Government entities with proper authorization

### Restrictions

- **No Redistribution**: This software may not be redistributed, in whole or in part, without explicit written permission
- **No Modifications**: Modifications may only be made by authorized developers
- **Confidential**: All code, documentation, and associated materials are confidential
- **Government Use Only**: This software is intended solely for government use

### Third-Party Licenses

This project uses open-source components. See individual component licenses:
- **React**: MIT License
- **Material UI**: MIT License
- **MobX**: MIT License
- **TypeScript**: Apache License 2.0
- **Webpack**: MIT License
- **SEMOSS SDK**: Proprietary (Deloitte)

For questions regarding licensing, contact the DHA PMO Development Team.

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

**Additional Libraries**:
- [React Hook Form](https://react-hook-form.com), [Axios](https://axios-http.com), [Mammoth.js](https://github.com/mwilliamson/mammoth.js), [Marked](https://marked.js.org), [React-MDE](https://github.com/andrerpena/react-mde)

Special thanks to the Defense Health Agency (DHA), Deloitte SEMOSS Team, and the open-source community.

---

