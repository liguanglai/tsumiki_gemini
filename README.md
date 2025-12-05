# Tsumiki Gemini

Tsumiki is a Test Driven Development (TDD) framework originally designed for Claude Code, now adapted for Gemini CLI. It provides a set of custom commands to streamline the TDD workflow, from requirements gathering to refactoring.

## Installation

### Global Installation (Recommended)

This method installs Tsumiki globally into your `~/.gemini/` directory, making it available in all your projects.

1. **Clone the repository:**
   ```bash
   git clone git@github.com:liguanglai/tsumiki_gemini.git
   ```

2. **Install to `~/.gemini/`:**
   Move the cloned folder into your Gemini configuration directory.
   ```bash
   # Create the directory if it doesn't exist
   mkdir -p ~/.gemini
   
   # Move and rename the folder to 'tsumiki'
   mv tsumiki_gemini ~/.gemini/tsumiki
   ```

3. **Configure Gemini CLI:**
   Add the Tsumiki commands path to your global configuration file (`~/.gemini/config.toml`).

   **If you don't have a config file yet:**
   Copy the provided config file:
   ```bash
   cp ~/.gemini/tsumiki/gemini-cli-config.toml ~/.gemini/config.toml
   ```

   **If you already have a `~/.gemini/config.toml`:**
   Edit it to add the Tsumiki commands path:
   ```toml
   [commands]
   include = ["~/.gemini/tsumiki/commands"]
   ```
   *Note: Ensure you append this to your existing `[commands]` section if one exists.*

## Usage

Once configured, you can use these commands within an active Gemini CLI session.
First, start your Gemini CLI session (e.g., by running `gemini` or simply interacting with this agent), then type the commands as shown below.

### Basic Workflow

1. **Initialize Tech Stack**:
   ```
   /tsumiki:init-tech-stack
   ```

2. **Start TDD Cycle (Interactive Workflow)**:
   The `tdd-cycle-full.sh` script in `commands/` is provided for users of Gemini CLI environments that support direct external invocation of commands (e.g., via a `gemini -p "..."` shell command). For this interactive Gemini CLI, you would manually execute the TDD phases as described below, or adapt the script to your specific environment's automation capabilities.

3. **Manual Step-by-Step TDD**:

   - **Requirements**:
     ```
     /tsumiki:tdd-requirements
     ```
   
   - **Red Phase (Write failing tests)**:
     ```
     /tsumiki:tdd-red
     ```
   
   - **Green Phase (Implement code)**:
     ```
     /tsumiki:tdd-green
     ```
   
   - **Refactor Phase**:
     ```
     /tsumiki:tdd-refactor
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
