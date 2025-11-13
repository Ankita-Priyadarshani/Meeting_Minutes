# Contributing to Meeting Minutes

Thank you for your interest in contributing to Meeting Minutes! We welcome bug reports and pull requests to help improve this project.

---

## Table of Contents

- [Basics](#basics)
- [Reporting Bugs](#reporting-bugs)
- [Suggesting Enhancements](#suggesting-enhancements)
- [Pull Requests](#pull-requests)
- [Development Workflow](#development-workflow)
- [Testing Your Work](#testing-your-work)
- [Write Documentation](#write-documentation)
- [Releasing a New Version](#releasing-a-new-version)

---

## Basics

1. Create an issue and describe your idea
2. Fork the repository
3. Create your feature branch (`git checkout -b my-new-feature`)
4. Commit your changes (`git commit -am 'Add some feature'`)
5. Publish the branch (`git push origin my-new-feature`)
6. Create a new Pull Request

---

## Reporting Bugs

Before creating a bug report, please check existing issues to avoid duplicates.

When filing a bug report, include:

- **Clear title**: Describe the issue concisely
- **Steps to reproduce**: Provide detailed steps to reproduce the bug
- **Expected behavior**: What you expected to happen
- **Actual behavior**: What actually happened
- **Environment**: Browser, OS, versions of dependencies
- **Screenshots**: If applicable
- **Error messages**: Full error messages and stack traces

**Example:**
```
Title: Meeting Minutes fails to upload PDF transcripts larger than 10MB

Steps to reproduce:
1. Navigate to /meeting-minutes/new
2. Attempt to upload a PDF transcript larger than 10MB
3. Click "Generate Minutes"

Expected: File uploads successfully
Actual: Upload fails with "File too large" error

Environment: Chrome 119, Windows 11, React 18.3
```

### Suggesting Enhancements

Enhancement suggestions are welcome! Please provide:

- **Clear description**: What enhancement you'd like to see
- **Use case**: Why this enhancement would be valuable
- **Proposed solution**: Your ideas on how to implement it
- **Alternatives considered**: Other approaches you've thought about

### Pull Requests

Pull requests are the best way to contribute code. Please follow these steps:

1. **Create an issue first**: Discuss your proposed changes
2. **Fork the repository**: Create your own fork
3. **Create a branch**: Use a descriptive branch name
4. **Make your changes**: Follow our coding standards
5. **Test thoroughly**: Ensure all tests pass
6. **Update documentation**: If needed
7. **Submit the PR**: With a clear description

---

## Development Workflow

### Step 1: Install Requirements

```bash
# Install frontend dependencies
cd assets/client
pnpm install

# Install backend dependencies
cd ../meeting-minutes-be
mvn clean install
```

### Step 2: Configure Environment

Create `.env` file in `assets/client/`:

```env
MODULE="/Monolith"
ENDPOINT="https://your-govconnect-instance.ai"
APP="your-meeting-minutes-app-id"
MODEL="your-llm-model-id"
EMBEDDER_ENGINE="your-embedder-engine-id"
NODE_ENV=development
PORT=3001
```

Update `assets/meeting-minutes-be/project.properties`:

```properties
client=Meeting_Minutes
version=0.0.1
projectId=your-app-id-here
SemossProjectPath=/path/to/semoss/project
```

Set up PostgreSQL database:

```bash
# Create database and schema
createdb pmo_meeting_minutes
psql -U your_username -d pmo_meeting_minutes -c "CREATE SCHEMA pmomm;"
```

### Step 3: Run & Debug

```bash
# Start development server
cd assets/client
pnpm dev

# Application will be available at http://localhost:3001
```

### Step 4: Test It

```bash
# Lint code
pnpm lint

# Type check
pnpm type-check

# Fix formatting issues
pnpm fix

# Build frontend
pnpm build

# Build backend
cd ../meeting-minutes-be
mvn clean package
```

---

## Testing Your Work

You can test your changes by running the application locally and verifying:

- The application builds without errors
- Linting passes: `pnpm lint`
- Type checking passes: `pnpm type-check`
- The workflow functions as expected
- No regressions in existing features

```bash
# Run checks
pnpm lint
pnpm type-check
pnpm build

# Backend build
cd assets/meeting-minutes-be
mvn clean package
```

---

## Write Documentation

This project has documentation in a few places:

### README.md
The main README provides an overview, installation instructions, and usage guidelines. Update this file when adding major features or changing how the application works.

### Code Comments
Add clear comments for complex logic. Use JSDoc style for functions and components:

```typescript
/**
 * Generates meeting minutes from a transcript using AI
 * 
 * @param transcript - The meeting transcript text
 * @param options - Configuration options for generation
 * @returns Promise resolving to the generated meeting minutes
 */
async function generateMinutes(transcript: string, options: GenerateOptions): Promise<MeetingMinutes> {
    // Implementation
}
```

---

## Releasing a New Version

1. Ensure all tests pass and the build is successful
2. Update version number in `package.json` and `pom.xml`
3. Create a Git tag: `git tag -a v0.1.0 -m "Release version 0.1.0"`
4. Push the changes: `git push`
5. Push the tag: `git push --tags`
6. Build the application:
   ```bash
   cd assets/client
   pnpm build
   
   cd ../meeting-minutes-be
   mvn clean package
   ```
7. Create deployment package with required files
8. Deploy to Govconnect.ai following deployment instructions in README.md

---
