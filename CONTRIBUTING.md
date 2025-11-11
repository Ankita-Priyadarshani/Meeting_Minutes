# How to Contribute

Bug reports and pull requests from users are what keep this project working. We welcome contributions to the Meeting Minutes application! Whether you're fixing bugs, improving documentation, or proposing new features, your help is appreciated.

## Basics

1. Create an issue and describe your idea
2. [Fork the repository](https://github.com/your-org/meeting-minutes/fork)
3. Create your feature branch (`git checkout -b feature/my-new-feature`)
4. Commit your changes (`git commit -am 'feat: add some feature'`)
5. Publish the branch (`git push origin feature/my-new-feature`)
6. Create a new Pull Request
7. Respond to code review feedback

## Running for Development

Make sure you have the required dependencies installed locally.

### Prerequisites

- **Node.js**: v16 or higher
- **pnpm**: v10.11.1 or higher
- **Java**: JDK 1.8 or higher
- **Maven**: 3.6 or higher
- **PostgreSQL**: v12 or higher with `pmomm` schema
- **SEMOSS/CFG AI Instance**: With access credentials configured

### Step 1: Install Frontend Dependencies

```bash
cd assets/client
pnpm install
```

### Step 2: Install Backend Dependencies

```bash
cd assets/meeting-minutes-be
mvn clean install
```

### Step 3: Configure Environment

Create `.env` file in `assets/client/`:

```env
MODULE="/Monolith"
ENDPOINT="https://your-govconnect-instance.ai"
APP="your-meeting-minutes-app-id"
MODEL="your-llm-model-id"
```

### Step 4: Run Development Server

```bash
cd assets/client
pnpm run dev
```

The application will be available at [http://localhost:3001](http://localhost:3001)

### Step 5: Test Your Changes

```bash
# Run linting and type checks
pnpm lint
pnpm type-check

# Fix formatting and linting issues automatically
pnpm fix
```

## Checking Your Work

You can test your changes in several ways:

### Run the Test Suite

```bash
cd assets/client
pnpm test
```

### Check Code Style

You can run ESLint and TypeScript checks:

```bash
pnpm lint        # Check for linting errors
pnpm type-check  # Check TypeScript types
pnpm fix         # Auto-fix formatting and linting issues
```

### Test in Different Browsers

If you're making UI changes, test on multiple browsers:
- Chrome/Edge (Chromium-based)
- Firefox
- Safari (if available)

### Verify Backend Changes

```bash
cd assets/meeting-minutes-be
mvn clean test
mvn clean package
```

## Code Quality Standards

All contributions must meet these quality standards:

### TypeScript/JavaScript Code

- All code must pass ESLint checks
- TypeScript types must be properly defined (no `any` types without justification)
- Components should not exceed 750 lines
- Follow semantic naming conventions
- Use `styled` components instead of inline styles
- Include proper error handling with try/catch blocks
- Add JSDoc comments for complex functions

**Example:**

```typescript
/**
 * Generates meeting minutes from a transcript using AI
 * @param transcript - The meeting transcript text
 * @param options - Configuration options for generation
 * @returns Promise resolving to generated meeting minutes
 * @throws Error if transcript is empty or AI service fails
 */
async function generateMinutes(
  transcript: string,
  options: GenerateOptions
): Promise<MeetingMinutes> {
  try {
    if (!transcript.trim()) {
      throw new Error('Transcript cannot be empty');
    }
    // Implementation...
  } catch (error) {
    console.error('Failed to generate minutes:', error);
    throw error;
  }
}
```

### Java Code

- Follow standard Java coding conventions
- Use meaningful variable and method names
- Add JavaDoc comments for public methods and classes
- Implement proper exception handling
- Write unit tests for new functionality

**Example:**

```java
/**
 * Stores meeting minutes in the PostgreSQL database
 * @param meeting The meeting object containing minutes and metadata
 * @return The stored meeting with generated ID
 * @throws DatabaseException if storage operation fails
 */
public Meeting storeMeeting(Meeting meeting) throws DatabaseException {
    try {
        // Implementation...
    } catch (SQLException e) {
        throw new DatabaseException("Failed to store meeting", e);
    }
}
```

### Git Commit Messages

Follow the [Conventional Commits](https://www.conventionalcommits.org/) specification:

```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

**Types:**
- `feat:` - New feature
- `fix:` - Bug fix
- `docs:` - Documentation changes
- `style:` - Code style changes (formatting, missing semicolons, etc.)
- `refactor:` - Code refactoring without functionality changes
- `perf:` - Performance improvements
- `test:` - Adding or updating tests
- `chore:` - Maintenance tasks, dependency updates

**Examples:**

```bash
feat: add export to Excel functionality
fix: resolve action item date parsing issue
docs: update installation instructions for Windows
refactor: simplify meeting minutes generation logic
```

## Pull Request Process

1. **Update Documentation**: Ensure the README.md and other docs are updated if you've made changes to functionality
2. **Code Review**: Your PR will be reviewed by at least two core team members
3. **Automated Checks**: All automated checks (lint, type-check, tests) must pass
4. **Breaking Changes**: Breaking changes require discussion and approval from the team lead
5. **Respond to Feedback**: Address all review comments and questions promptly

### Pull Request Checklist

Before submitting your PR, ensure:

- [ ] Code follows the project's coding standards
- [ ] All tests pass locally
- [ ] New features include appropriate tests
- [ ] Documentation is updated (README, code comments, etc.)
- [ ] Commit messages follow conventional commits format
- [ ] No merge conflicts with the main branch
- [ ] Changes have been tested in development environment
- [ ] Browser compatibility verified (if UI changes)

## Reporting Bugs

When reporting bugs, please include:

### Required Information

- **Application Name**: Meeting Minutes
- **Environment**: Development, staging, or production
- **Steps to Reproduce**: Detailed steps to recreate the issue
- **Expected Behavior**: What should happen
- **Actual Behavior**: What actually happens
- **Screenshots/Logs**: Any relevant error messages or console output
- **Browser & Version**: e.g., Chrome 119, Firefox 120, Edge 118
- **Date/Time**: When the issue occurred
- **User Role**: If relevant to permissions/access

### Optional but Helpful

- Browser console logs
- Network request/response details
- Recent changes or updates
- Workarounds attempted
- Related issues or patterns

### Bug Report Template

```markdown
**Environment**: [Development/Staging/Production]

**Steps to Reproduce**:
1. Navigate to...
2. Click on...
3. Enter...
4. Observe error...

**Expected Behavior**:
The application should...

**Actual Behavior**:
Instead, the application...

**Screenshots**:
[Attach screenshots if applicable]

**Console Logs**:
```
[Paste relevant console output]
```

**Browser**: Chrome 119 (Windows 11)
**Date/Time**: 2025-11-11 14:30 EST
```

## Suggesting Enhancements

For feature requests and enhancements:

1. **Describe the Problem**: What problem are you trying to solve?
2. **Proposed Solution**: Explain your proposed solution in detail
3. **Alternatives Considered**: Discuss alternative approaches
4. **Impact Analysis**: How will this affect existing functionality?
5. **Mockups/Examples**: Include visual examples if applicable
6. **Use Cases**: Provide specific use cases or scenarios

### Feature Request Template

```markdown
**Problem Statement**:
As a [user type], I want to [action] so that [benefit].

**Proposed Solution**:
[Detailed description of your proposed solution]

**Alternatives Considered**:
1. [Alternative 1]
2. [Alternative 2]

**Impact on Existing Features**:
[How this might affect current functionality]

**Mockups**:
[Attach mockups, wireframes, or examples]
```

## Write Documentation

This project has documentation in several places:

### Introduction and Usage

The main `README.md` provides an overview and getting started guide for many audiences.

### Code Style Guide

`assets/client/CodeStyle.md` contains detailed coding standards and best practices.

### Component Documentation

- `assets/client/src/components/README.md` - Component architecture
- `assets/client/src/stores/README.md` - State management patterns

### API Documentation

- JSDoc comments in TypeScript code
- JavaDoc comments in Java code
- Comprehensive documentation in `_PMO_Documentation.pptx`

### Inline Comments

Add inline comments for complex logic:

```typescript
// Calculate action item priority based on keywords and due date
// High priority: contains "urgent", "critical", or due within 3 days
// Medium priority: due within 7 days
// Low priority: all others
const priority = calculatePriority(item, dueDate);
```

## Issue and Pull Request Labels

We use labels to categorize and prioritize issues and PRs:

| Label | Description |
|-------|-------------|
| `bug` | Something isn't working |
| `enhancement` | New feature or request |
| `documentation` | Improvements or additions to documentation |
| `good first issue` | Good for newcomers |
| `help wanted` | Extra attention is needed |
| `priority: high` | High priority issue |
| `priority: medium` | Medium priority issue |
| `priority: low` | Low priority issue |
| `status: blocked` | Blocked by another issue or external dependency |
| `status: in progress` | Currently being worked on |
| `status: review needed` | Ready for code review |
| `wontfix` | This will not be worked on |

## Recognition

Contributors who make significant improvements will be:

- Added to the Acknowledgments section in the README
- Credited in release notes
- Mentioned in project documentation

## Questions or Need Help?

If you have questions about contributing:

- **Check Documentation**: Review the README and code style guide
- **Ask the Team**: Reach out in team communication channels
- **Create an Issue**: Open a discussion issue for general questions
- **Contact Support**: Email dha-pmo-support@example.mil

## Additional Links

- [README.md](README.md) - Project overview and setup
- [Code Style Guide](assets/client/CodeStyle.md) - Coding standards
- [Issues](https://github.com/your-org/meeting-minutes/issues) - Bug reports and feature requests
- [Pull Requests](https://github.com/your-org/meeting-minutes/pulls) - Proposed changes
- [SEMOSS Documentation](https://semoss.org/docs) - Platform documentation

---

Thank you for contributing to the Meeting Minutes application! 🎉

Thank you for contributing to Meeting Minutes! :heart:
