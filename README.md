# SQL Database Agents with LangGraph

This project demonstrates how to build a smart, interactive SQL database agent using LangGraph and LangChain. The agent can answer natural language questions, validate and execute SQL queries, and visualize its workflow—all in a single notebook!

---

## 🚀 Features
- **Rich SQLite schema**: Multiple related tables (USERS, DEPARTMENTS, PROJECTS, etc.)
- **Demo data**: Pre-populated for instant experimentation
- **LangChain + LangGraph**: Modern agent workflow with LLM-powered reasoning
- **Automatic SQL generation**: Ask questions in English, get SQL answers
- **Query validation**: LLM double-checks and corrects queries before execution
- **Error handling**: Robust tool fallback and error messaging
- **Visual workflow**: See the agent's logic as a diagram
- **Schema diagram**: Understand the data model at a glance

---

## 📁 Project Structure
- `SQL_agent.ipynb`: Main notebook (run this!)
- `company_emp_.db`: SQLite database file
- `requirements.txt`: Python dependencies

---

## 🛠️ How to Use
1. **Install dependencies**
   ```sh
   pip install -r requirements.txt
   ```
2. **Open `SQL_agent.ipynb`** in VS Code or Jupyter
3. **Run all cells** to:
   - Create and populate the database
   - Set up the agent workflow
   - Interact with the agent for SQL tasks
   - Visualize the workflow and schema

---

## 💡 Real-Time Use Case: Integrate with Your App
Want to use this agent in a real-world application? Here’s how you can adapt it:

1. **Convert the notebook logic to a Python module** (e.g., `sql_agent.py`).
2. **Wrap the agent in a web API** using FastAPI or Flask:
   ```python
   from fastapi import FastAPI, Request
   from sql_agent import agent_workflow  # Your workflow logic

   app = FastAPI()

   @app.post("/ask")
   async def ask_sql(request: Request):
       data = await request.json()
       question = data["question"]
       result = agent_workflow.invoke({"messages": [question]})
       return {"answer": result}
   ```
3. **Deploy** the API (e.g., on Azure, AWS, or Heroku).
4. **Connect** your frontend, chatbot, or business app to the API endpoint.

**Use cases:**
- Internal analytics chatbot for HR, sales, or project management
- Self-serve data exploration for business users
- Automated reporting tools

---

## 🧠 Workflow Overview
The agent follows this process:
1. List tables
2. Get schema
3. Generate SQL query from user question
4. Validate and correct the query
5. Execute the query
6. Return the answer

See the notebook for a detailed diagram and code.

---

## 🗂️ Model Structure Diagram

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

---

## 📦 Requirements
- Python 3.10+
- See `requirements.txt` for all packages

---

## 🙏 Credits
- Built with [LangChain](https://github.com/langchain-ai/langchain) and [LangGraph](https://github.com/langchain-ai/langgraph)

---

For questions or issues, please open an issue in this repository.