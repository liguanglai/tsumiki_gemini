# Tsumiki Gemini

Tsumiki is a Test Driven Development (TDD) framework originally designed for Claude Code, now adapted for Gemini CLI. It provides a set of custom commands to streamline the TDD workflow, from requirements gathering to refactoring.

## Installation

1. Clone this repository:
   ```bash
   git clone git@github.com:liguanglai/tsumiki_gemini.git
   ```

2. Configure Gemini CLI to recognize the commands.
   A `gemini-cli-config.toml` file has been provided in the repository root. This file contains the necessary configuration to include the Tsumiki commands.

   **Option A (Project-specific)**: Copy `gemini-cli-config.toml` into your project's `.gemini/` directory.
   ```bash
   cp tsumiki_gemini/gemini-cli-config.toml /path/to/your/project/.gemini/config.toml
   ```
   *Note: If you already have a `config.toml` in your project, you'll need to manually merge the `[commands]` section from `gemini-cli-config.toml` into your existing file.*

   **Option B (Global)**: Merge the content of `gemini-cli-config.toml` into your global gemini-cli configuration file (e.g., `~/.gemini/config.toml`).
   ```toml
   # Example of merging into your global ~/.gemini/config.toml
   [commands]
   include = ["/Users/ligl/02.workspaces/04.funny/tsumiki_gemini/commands"]
   ```
   *Always back up your global configuration before making changes.*

## Usage

Once installed, you can use the commands directly in Gemini CLI.

### Basic Workflow

1. **Initialize Tech Stack**:
   ```bash
   gemini /tsumiki:init-tech-stack
   ```

2. **Start TDD Cycle (Interactive Script)**:
   ```bash
   ./commands/tdd-cycle-full.sh "Implement user login"
   ```

3. **Manual Step-by-Step TDD**:

   - **Requirements**:
     ```bash
     gemini /tsumiki:tdd-requirements
     ```
   
   - **Red Phase (Write failing tests)**:
     ```bash
     gemini /tsumiki:tdd-red
     ```
   
   - **Green Phase (Implement code)**:
     ```bash
     gemini /tsumiki:tdd-green
     ```
   
   - **Refactor Phase**:
     ```bash
     gemini /tsumiki:tdd-refactor
     ```

### Available Commands

- `/tsumiki:auto-debug`: Automatically debug and fix test errors.
- `/tsumiki:direct-setup`: Setup project environment directly.
- `/tsumiki:kairo-design`: Design phase helper.
- `/tsumiki:kairo-implement`: Implementation phase helper.
- ... and more. Check the `commands/` directory for all available commands.

## Project Configuration

Tsumiki uses `GEMINI.md` (or `CLAUDE.md` for compatibility) in your project root to understand your project's context and tech stack.

Example `GEMINI.md`:
```markdown
# Project Name

## Tech Stack
- Frontend: React, TypeScript
- Backend: Python, FastAPI
- Database: PostgreSQL
```

## Agents

Includes `symbol-searcher` agent for code navigation.
