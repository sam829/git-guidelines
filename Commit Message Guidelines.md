# Commit Message Guidelines

## Overview

This document provides guidelines and best practices for writing clear, consistent, and informative commit messages. Good commit messages help team collaboration, code review, and project maintenance.

## Basic Structure

A good commit message consists of three parts:
- A short, concise title (subject line)
- An optional detailed description
- Optional references or context

### Commit Message Template

```
<type>(<scope>): Short, descriptive title

Detailed description of changes:
- Specific modification 1
- Specific modification 2
- Reason for change

Breaking changes (if applicable):
- Detail any breaking modifications

Refs: #issueNumber
```

## Commit Types

| Type       | Description                                    |
|------------|------------------------------------------------|
| `feat`     | New feature or enhancement                     |
| `fix`      | Bug fix                                        |
| `docs`     | Documentation changes                          |
| `style`    | Formatting, missing semi-colons                |
| `refactor` | Code restructuring                             |
| `test`     | Adding/modifying tests                         |
| `chore`    | Maintenance tasks, dependency updates          |
| `perf`     | Performance improvements                       |
| `security` | Security-related changes                       |

## Examples of Good Commit Messages

### 1. Feature Addition
```
feat(auth): Add user login functionality

- Implement email/password authentication
- Create login form with validation
- Add error handling for login attempts
- Integrate with backend authentication service
```

### 2. Bug Fix
```
fix(payment): Resolve credit card validation error

- Correct regex pattern for card number validation
- Handle edge cases with international card formats
- Add comprehensive unit tests
- Improve error messaging
```

### 3. Refactoring
```
refactor(state-management): Migrate from BLoC to Riverpod

- Replace existing BLoC implementations
- Simplify state management code
- Improve dependency injection
- Reduce boilerplate code
```

### 4. Performance Improvement
```
perf(image-loading): Optimize image caching mechanism

- Implement more efficient caching strategy
- Reduce memory footprint of image loading
- Add lazy loading for images
- Improve initial load time
```

### 5. Complex Change
```
feat(chat): Implement real-time messaging system

This commit adds a comprehensive real-time messaging feature:

- WebSocket integration for instant messaging
- Offline message queue and synchronization
- Read receipts and typing indicators
- End-to-end encryption for message privacy
- Support for media attachments

Breaking changes:
- Requires backend API version 2.0
- Deprecates old messaging endpoint
```

## Best Practices

1. **Use Imperative Mood**
   - Write as if giving a command
   - "Add feature" instead of "Added feature"
   - "Fix bug" instead of "Fixed bug"

2. **Be Concise but Descriptive**
   - First line should be < 50-72 characters
   - Provide context in the body
   - Explain the "why" behind the change

3. **Reference Issues**
   - Include issue numbers when applicable
   - Use standard references like "Fixes #123"

4. **Separate Concerns**
   - One commit should do one thing
   - Avoid mixing multiple unrelated changes

5. **Provide Context**
   - Explain motivation for the change
   - Describe impact on the system
   - Note any side effects

## What to Avoid

❌ Bad Commit Messages:
- "Fixed stuff"
- "Updated code"
- "Made changes"
- Extremely long, rambling descriptions
- Messages without clear purpose

## Tools and Automation

Consider using tools to enforce commit message standards:
- Commitlint
- Husky
- Conventional Commits

## Conclusion

Well-crafted commit messages are a form of documentation. They tell a story about the evolution of your codebase and help future developers (including yourself) understand the reasoning behind changes.

