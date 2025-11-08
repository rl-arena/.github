# Contributing to RL-Arena

Thank you for your interest in contributing to RL-Arena! This document provides guidelines and instructions for contributing to the project.

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [How Can I Contribute?](#how-can-i-contribute)
- [Getting Started](#getting-started)
- [Development Process](#development-process)
- [Pull Request Process](#pull-request-process)
- [Coding Standards](#coding-standards)
- [Testing Guidelines](#testing-guidelines)
- [Documentation](#documentation)
- [Community](#community)

## Code of Conduct

### Our Pledge

We are committed to providing a welcoming and inclusive environment for all contributors, regardless of background or experience level.

### Our Standards

**Positive behavior includes:**
- Using welcoming and inclusive language
- Being respectful of differing viewpoints
- Accepting constructive criticism gracefully
- Focusing on what's best for the community
- Showing empathy towards others

**Unacceptable behavior includes:**
- Harassment, trolling, or discriminatory comments
- Personal attacks or insults
- Publishing others' private information
- Other conduct inappropriate in a professional setting

## How Can I Contribute?

### Reporting Bugs

**Before submitting a bug report:**
1. Check the [existing issues](https://github.com/rl-arena/rl-arena-backend/issues) to avoid duplicates
2. Verify the bug exists in the latest version
3. Collect information about your environment

**When submitting a bug report, include:**
- **Clear title** - Descriptive summary of the issue
- **Steps to reproduce** - Detailed steps to trigger the bug
- **Expected behavior** - What should happen
- **Actual behavior** - What actually happens
- **Environment details** - OS, versions, configuration
- **Screenshots/logs** - If applicable

**Example:**
```markdown
### Bug: Match not created despite eligible agents

**Steps to Reproduce:**
1. Submit two agents to Pong environment
2. Both agents build successfully
3. Wait 5 minutes

**Expected:** Match should be created automatically

**Actual:** No match created after 10 minutes

**Environment:**
- OS: Ubuntu 22.04
- Go: 1.21.5
- PostgreSQL: 15.3
- Backend commit: abc123

**Logs:**
```
[ERROR] matchmaking: no eligible agents found
```
```

### Suggesting Features

**Before suggesting a feature:**
1. Check if it's already proposed in [discussions](https://github.com/rl-arena/rl-arena/discussions)
2. Consider if it aligns with project goals
3. Think about implementation complexity

**Feature request template:**
```markdown
### Feature: Add Chess environment

**Problem:** Users want to train agents for Chess

**Solution:** Implement Chess as a new environment using python-chess library

**Benefits:**
- Attracts chess AI enthusiasts
- More diverse environment library
- Demonstrates RL-Arena flexibility

**Implementation ideas:**
- Use python-chess for game logic
- Action space: from_square + to_square encoding
- Observation: board state as 8x8x12 tensor (6 piece types × 2 colors)

**Alternatives considered:**
- Simplified chess variant (too limiting)
- Existing chess RL libraries (less control)
```

### Contributing Code

We welcome code contributions! Here are areas where you can help:

#### 1. New Game Environments
Add new competitive environments (Chess, Go, Card games, etc.)

**Requirements:**
- Gymnasium-compatible API
- Two-player competitive gameplay
- Clear observation and action spaces
- Replay generation support (HTML + JSON)
- Comprehensive tests

**See:** [Development Guide - Add New Environment](https://github.com/rl-arena/rl-arena-docs/blob/main/DEVELOPMENT.md#add-new-environment)

#### 2. Backend Features
Improve the Go API server

**Examples:**
- Tournament system
- Advanced matchmaking algorithms
- Admin dashboard
- Analytics endpoints
- Performance optimizations

#### 3. Executor Improvements
Enhance match execution engine

**Examples:**
- Better resource management
- Multi-environment support
- Execution monitoring
- Error recovery mechanisms

#### 4. Frontend Enhancements
Improve the React web interface

**Examples:**
- Better replay visualization
- Mobile responsiveness
- Advanced filtering/search
- User profile pages
- Real-time statistics

#### 5. Documentation
Help make RL-Arena more accessible

**Examples:**
- Tutorial videos
- Blog posts
- API examples
- Translation to other languages
- Fixing typos and clarifications

## Getting Started

### 1. Fork the Repository

Click the "Fork" button on the repository you want to contribute to:
- [rl-arena-backend](https://github.com/rl-arena/rl-arena-backend)
- [rl-arena-executor](https://github.com/rl-arena/rl-arena-executor)
- [rl-arena-web](https://github.com/rl-arena/rl-arena-web)
- [rl-arena-env](https://github.com/rl-arena/rl-arena-env)

### 2. Clone Your Fork

```bash
git clone https://github.com/YOUR_USERNAME/REPOSITORY_NAME.git
cd REPOSITORY_NAME
```

### 3. Set Up Development Environment

Follow the [Development Guide](https://github.com/rl-arena/rl-arena-docs/blob/main/DEVELOPMENT.md) for your repository.

### 4. Create a Branch

```bash
git checkout -b feature/your-feature-name
```

Branch naming conventions:
- `feature/` - New features
- `fix/` - Bug fixes
- `docs/` - Documentation changes
- `refactor/` - Code refactoring
- `test/` - Test improvements
- `chore/` - Maintenance tasks

**Examples:**
```bash
git checkout -b feature/chess-environment
git checkout -b fix/matchmaking-cooldown
git checkout -b docs/api-examples
```

## Development Process

### 1. Write Code

Follow our [Coding Standards](#coding-standards) for your language.

### 2. Write Tests

**Backend (Go):**
```go
func TestNewFeature(t *testing.T) {
    // Arrange
    service := NewService()
    
    // Act
    result := service.NewFeature()
    
    // Assert
    assert.Equal(t, expected, result)
}
```

**Executor (Python):**
```python
def test_new_feature():
    # Arrange
    runner = MatchRunner()
    
    # Act
    result = runner.new_feature()
    
    # Assert
    assert result.status == "SUCCESS"
```

**Web (React):**
```jsx
import { render, screen } from '@testing-library/react';

test('renders new feature', () => {
    render(<NewFeature />);
    expect(screen.getByText('Feature Title')).toBeInTheDocument();
});
```

### 3. Run Tests Locally

```bash
# Backend
go test ./...

# Executor
pytest

# Web
npm test
```

### 4. Run Linters

```bash
# Backend
golangci-lint run

# Executor
black .
ruff check .

# Web
npm run lint
```

### 5. Update Documentation

If your changes affect:
- **API** - Update API_REFERENCE.md
- **Setup** - Update GETTING_STARTED.md or DEVELOPMENT.md
- **Architecture** - Update ARCHITECTURE.md
- **Features** - Update README.md

### 6. Commit Changes

Use [Conventional Commits](https://www.conventionalcommits.org/):

```bash
git commit -m "feat: add chess environment"
git commit -m "fix: resolve matchmaking cooldown bug"
git commit -m "docs: add API examples for agents endpoint"
git commit -m "refactor: simplify ELO calculation logic"
git commit -m "test: add tests for rate limiting"
```

**Commit message format:**
```
<type>(<scope>): <subject>

<body>

<footer>
```

**Types:**
- `feat` - New feature
- `fix` - Bug fix
- `docs` - Documentation
- `style` - Code style (formatting, no logic change)
- `refactor` - Code refactoring
- `test` - Tests
- `chore` - Maintenance
- `perf` - Performance improvement

**Example:**
```
feat(env): add Chess environment

- Implement Chess game logic using python-chess
- Add board state observation encoding
- Create HTML replay visualization
- Add comprehensive tests

Closes #123
```

## Pull Request Process

### 1. Push Your Branch

```bash
git push origin feature/your-feature-name
```

### 2. Create Pull Request

1. Go to the original repository on GitHub
2. Click "Pull requests" → "New pull request"
3. Click "compare across forks"
4. Select your fork and branch
5. Fill out the PR template

### 3. PR Template

```markdown
## Description
Brief description of changes

## Type of Change
- [ ] Bug fix (non-breaking change that fixes an issue)
- [ ] New feature (non-breaking change that adds functionality)
- [ ] Breaking change (fix or feature that breaks existing functionality)
- [ ] Documentation update

## Changes Made
- Specific change 1
- Specific change 2
- Specific change 3

## Testing
- [ ] Added/updated unit tests
- [ ] All tests pass locally
- [ ] Tested manually (describe how)

## Screenshots (if applicable)
[Add screenshots for UI changes]

## Checklist
- [ ] My code follows the project's style guidelines
- [ ] I have performed a self-review of my code
- [ ] I have commented my code where necessary
- [ ] I have updated the documentation
- [ ] My changes generate no new warnings
- [ ] I have added tests that prove my fix/feature works
- [ ] New and existing tests pass locally

## Related Issues
Closes #123
Relates to #456
```

### 4. Code Review Process

**What to expect:**
- Maintainers will review your PR within 1-3 days
- You may receive feedback and change requests
- Address feedback by pushing new commits
- Once approved, your PR will be merged

**Tips for faster review:**
- Keep PRs focused and reasonably sized
- Write clear commit messages
- Add tests for new functionality
- Update documentation
- Respond promptly to feedback

### 5. After Merge

1. **Delete your branch:**
   ```bash
   git branch -d feature/your-feature-name
   git push origin --delete feature/your-feature-name
   ```

2. **Update your fork:**
   ```bash
   git checkout main
   git pull upstream main
   git push origin main
   ```

## Coding Standards

### Go (Backend)

**Style:**
- Use `gofmt` and `goimports`
- Follow [Effective Go](https://golang.org/doc/effective_go)
- Run `golangci-lint run`

**Best Practices:**
```go
// ✅ Good
func (s *AgentService) GetAgent(id string) (*models.Agent, error) {
    agent, err := s.repo.FindByID(id)
    if err != nil {
        return nil, fmt.Errorf("failed to get agent: %w", err)
    }
    return agent, nil
}

// ❌ Bad
func (s *AgentService) GetAgent(id string) (*models.Agent, error) {
    agent, _ := s.repo.FindByID(id)  // Ignoring errors
    return agent, nil
}
```

### Python (Executor, Environment)

**Style:**
- Use `black` for formatting (88 char line length)
- Use `ruff` for linting
- Use type hints
- Follow [PEP 8](https://pep8.org/)

**Best Practices:**
```python
# ✅ Good
def run_match(self, agent1_id: str, agent2_id: str) -> MatchResult:
    """
    Run a match between two agents.
    
    Args:
        agent1_id: ID of first agent
        agent2_id: ID of second agent
        
    Returns:
        MatchResult with winner and replay data
    """
    # Implementation
    return result

# ❌ Bad
def run_match(self, agent1_id, agent2_id):  # No type hints, no docstring
    return result
```

### JavaScript/React (Web)

**Style:**
- Use ESLint configuration
- Follow React best practices
- Use functional components with hooks
- Use PropTypes for type checking

**Best Practices:**
```jsx
// ✅ Good
import PropTypes from 'prop-types';

function AgentCard({ agent, onSelect }) {
    return (
        <div className="agent-card" onClick={() => onSelect(agent.id)}>
            <h3>{agent.name}</h3>
            <p>ELO: {agent.elo_rating}</p>
        </div>
    );
}

AgentCard.propTypes = {
    agent: PropTypes.shape({
        id: PropTypes.string.isRequired,
        name: PropTypes.string.isRequired,
        elo_rating: PropTypes.number.isRequired,
    }).isRequired,
    onSelect: PropTypes.func.isRequired,
};

export default AgentCard;

// ❌ Bad
function AgentCard(props) {  // No destructuring, no PropTypes
    return <div>{props.agent.name}</div>;
}
```

## Testing Guidelines

### Test Coverage Requirements

- **Backend**: Minimum 70% coverage for new code
- **Executor**: Minimum 70% coverage for new code
- **Web**: Minimum 60% coverage for new components

### Testing Principles

1. **Arrange-Act-Assert** pattern
2. Test both success and failure cases
3. Use meaningful test names
4. Keep tests independent
5. Mock external dependencies

### Example Tests

**Backend (Go):**
```go
func TestELOService_CalculateRating(t *testing.T) {
    tests := []struct {
        name           string
        currentRating  int
        opponentRating int
        won            bool
        matchesPlayed  int
        expectedMin    int
        expectedMax    int
    }{
        {
            name:           "win increases rating",
            currentRating:  1200,
            opponentRating: 1200,
            won:            true,
            matchesPlayed:  5,
            expectedMin:    1200,
            expectedMax:    1250,
        },
        {
            name:           "loss decreases rating",
            currentRating:  1200,
            opponentRating: 1200,
            won:            false,
            matchesPlayed:  5,
            expectedMin:    1150,
            expectedMax:    1200,
        },
    }

    service := NewELOService()
    for _, tt := range tests {
        t.Run(tt.name, func(t *testing.T) {
            result := service.CalculateRating(
                tt.currentRating,
                tt.opponentRating,
                tt.won,
                tt.matchesPlayed,
            )
            assert.GreaterOrEqual(t, result, tt.expectedMin)
            assert.LessOrEqual(t, result, tt.expectedMax)
        })
    }
}
```

**Executor (Python):**
```python
import pytest
from executor.match_runner import MatchRunner

def test_match_runner_success():
    """Test successful match execution"""
    runner = MatchRunner()
    result = runner.run_match("agent1", "agent2")
    
    assert result.status == "SUCCESS"
    assert result.winner_agent_id in ["agent1", "agent2"]
    assert len(result.replay_data) > 0

def test_match_runner_timeout():
    """Test match timeout handling"""
    runner = MatchRunner(timeout=1)
    
    with pytest.raises(TimeoutError):
        runner.run_match("slow_agent1", "slow_agent2")
```

**Web (React):**
```jsx
import { render, screen, fireEvent } from '@testing-library/react';
import AgentCard from './AgentCard';

describe('AgentCard', () => {
    const mockAgent = {
        id: '123',
        name: 'TestAgent',
        elo_rating: 1500,
    };

    test('renders agent information', () => {
        render(<AgentCard agent={mockAgent} onSelect={jest.fn()} />);
        
        expect(screen.getByText('TestAgent')).toBeInTheDocument();
        expect(screen.getByText('ELO: 1500')).toBeInTheDocument();
    });

    test('calls onSelect when clicked', () => {
        const onSelect = jest.fn();
        render(<AgentCard agent={mockAgent} onSelect={onSelect} />);
        
        fireEvent.click(screen.getByText('TestAgent'));
        expect(onSelect).toHaveBeenCalledWith('123');
    });
});
```

## Documentation

### Code Documentation

**Go:**
```go
// AgentService handles agent-related business logic
type AgentService struct {
    repo *AgentRepository
}

// CreateAgent creates a new agent for the user
//
// Returns an error if:
// - Agent name is already taken
// - User has reached maximum agent limit
func (s *AgentService) CreateAgent(userID, name string) (*models.Agent, error) {
    // Implementation
}
```

**Python:**
```python
class MatchRunner:
    """Executes matches between two agents in isolated environments."""
    
    def run_match(self, agent1_id: str, agent2_id: str) -> MatchResult:
        """
        Run a match between two agents.
        
        Args:
            agent1_id: UUID of the first agent
            agent2_id: UUID of the second agent
            
        Returns:
            MatchResult containing winner, scores, and replay data
            
        Raises:
            AgentNotFoundError: If either agent doesn't exist
            ExecutionError: If match execution fails
        """
        # Implementation
```

### README Updates

When adding features, update the relevant README:
- New environment → Update `rl-arena-env/README.md`
- New API endpoint → Update `rl-arena-backend/README.md`
- New UI feature → Update `rl-arena-web/README.md`

### Documentation Files

Update documentation in `rl-arena-docs`:
- `GETTING_STARTED.md` - Installation and first steps
- `ARCHITECTURE.md` - System design changes
- `API_REFERENCE.md` - New API endpoints
- `DEVELOPMENT.md` - Development process changes

## Community

### Communication Channels

- **GitHub Issues** - Bug reports and feature requests
- **GitHub Discussions** - General questions and ideas
- **Pull Requests** - Code contributions and reviews

### Getting Help

**Stuck on something?**
1. Check the [documentation](https://github.com/rl-arena/rl-arena-docs)
2. Search [existing issues](https://github.com/rl-arena/rl-arena-backend/issues)
3. Ask in [discussions](https://github.com/rl-arena/rl-arena/discussions)
4. Create a new issue with details

### Recognition

Contributors are recognized in:
- Repository contributors page
- Release notes
- Project documentation

Thank you for contributing to RL-Arena! 🎮🤖

---

**Quick Links:**
- [Development Guide](https://github.com/rl-arena/rl-arena-docs/blob/main/DEVELOPMENT.md)
- [Architecture Overview](https://github.com/rl-arena/rl-arena-docs/blob/main/ARCHITECTURE.md)
- [API Reference](https://github.com/rl-arena/rl-arena-docs/blob/main/API_REFERENCE.md)
