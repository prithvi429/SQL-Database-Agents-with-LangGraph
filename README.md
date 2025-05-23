# SQL Database Agents with LangGraph

This project demonstrates how to build a SQL database agent using LangGraph and LangChain, with a workflow for natural language to SQL query generation, validation, and execution.

## Features
- SQLite database with multiple related tables (USERS, DEPARTMENTS, PROJECTS, etc.)
- Data population for demo purposes
- LangChain and LangGraph integration for agent workflow
- LLM-powered SQL query generation and validation
- Tool-based execution and error handling
- Visual workflow diagram

## Project Structure
- `SQL_agent.ipynb`: Main notebook with all code, workflow, and documentation
- `company_emp_.db`: SQLite database file
- `requirements.txt`: Python dependencies

## How to Use
1. **Install dependencies**
   ```sh
   pip install -r requirements.txt
   ```
2. **Open `SQL_agent.ipynb` in VS Code or Jupyter**
3. **Run all cells** to:
   - Create and populate the database
   - Set up the agent workflow
   - Interact with the agent for SQL tasks
   - Visualize the workflow

## Workflow Overview
The agent follows this process:
1. List tables
2. Get schema
3. Generate SQL query from user question
4. Validate and correct the query
5. Execute the query
6. Return the answer

See the notebook for a detailed diagram and code.

## Model Structure Diagram

Below is a simple diagram of the main tables and their relationships in the database:

```
USERS (emp_id PK)
  |\
  |  \
  |   +--< EMPLOYEES_DEPARTMENTS (emp_id, dept_id PK, FK)
  |         |
  |         +--< DEPARTMENTS (dept_id PK)
  |
  +--< ASSIGNMENTS (assignment_id PK, emp_id FK, project_id FK)
  |         |
  |         +--< PROJECTS (project_id PK)
  |
  +--< ATTENDANCE (attendance_id PK, emp_id FK)
```

- PK = Primary Key
- FK = Foreign Key
- One-to-many and many-to-many relationships are shown via connecting lines.

See the notebook for schema details and code.

## Requirements
- Python 3.10+
- See `requirements.txt` for all packages

## Credits
- Built with [LangChain](https://github.com/langchain-ai/langchain) and [LangGraph](https://github.com/langchain-ai/langgraph)

---

For questions or issues, please open an issue in this repository.