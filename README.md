# Tsumiki Gemini

Tsumiki is a Test Driven Development (TDD) framework originally designed for Claude Code, now adapted for Gemini CLI. It provides a set of custom commands to streamline the TDD workflow, from requirements gathering to refactoring.

## Installation

1. Clone this repository:
   ```bash
   git clone git@github.com:liguanglai/tsumiki_gemini.git
   ```

2. Configure Gemini CLI to recognize the commands.
   Depending on your Gemini CLI version, you might need to:
   - **Option A**: Symlink or copy the files in `commands/` to your global Gemini commands directory (e.g., `~/.gemini/commands` or `~/.gemini/prompts`).
   - **Option B**: Add the path to this repository's `commands` directory in your Gemini configuration file.

   For example, if using a configuration file (like `config.toml` or `.gemini/config`), add:
   ```toml
   [commands]
   include = ["/path/to/tsumiki_gemini/commands"]
   ```

   *Note: Adjust the installation method based on your specific Gemini CLI environment.*

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
