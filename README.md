# Rule Engine with Flask, SQLAlchemy, and GUI Interface

## Overview
This project implements a rule engine using Flask, SQLAlchemy, and a Tkinter-based GUI. The application allows creating, combining, modifying, and evaluating conditional rules based on simple logical expressions like AND/OR and comparisons.

## Features
- **Create Rule:** Define logical rules using expressions.
- **Combine Rules:** Merge existing rules using AND logic.
- **Evaluate Rule:** Evaluate a rule using a set of data.
- **Modify Rule:** Update an existing rule's logic.

## Project Structure
- `app.py`: Main Flask API for managing rules.
- `gui.py`: GUI-based interface for user interactions.
- `test_script.py`: CLI test script for automated testing.
- `README.md`: This file.

## Setup

### Prerequisites
- **Python 3.7+**
- **Flask**
- **SQLAlchemy**
- **Requests** (for `test_script.py`)
- **Tkinter** (usually included with Python installations)

### Installation
1. **Clone Repository:**
   ```bash
   git clone https://github.com/your-repo-url.git
   cd rule-engine
   ```

2. **Install Dependencies:**
   ```bash
   pip install flask sqlalchemy requests
   ```

3. **Set Up Database:**
   The database is SQLite-based. Running the Flask app will automatically create `rules.db` in the project directory if it doesn’t exist.

### Running the Application
1. **Start Flask Server:**
   ```bash
   python app.py
   ```
   Flask will run on `http://127.0.0.1:5000`.

2. **Run GUI Interface:**
   In a new terminal window, execute:
   ```bash
   python gui.py
   ```
   This opens a GUI window for interacting with the Rule Engine.

3. **Run Test Script (Optional):**
   The `test_script.py` file runs through example cases.
   ```bash
   python test_script.py
   ```

## API Endpoints
- **POST `/create_rule`**: Creates a new rule.
   - **Request:** `{"rule_string": "(age > 30 AND department = 'Sales')"}`
   - **Response:** `{ "id": 1, "ast": "<AST in JSON format>" }`

- **POST `/combine_rules`**: Combines multiple rules with AND logic.
   - **Request:** `{"rule_ids": [1, 2]}`
   - **Response:** `{ "id": 3, "combined_ast": "<Combined AST in JSON format>" }`

- **POST `/evaluate_rule`**: Evaluates a rule with provided data.
   - **Request:** `{"rule_id": 3, "data": {"age": 35, "department": "Sales", "salary": 60000, "experience": 6}}`
   - **Response:** `{ "result": true }`

- **POST `/modify_rule`**: Modifies an existing rule.
   - **Request:** `{"rule_id": 1, "new_rule_string": "age > 40 AND department = 'HR'"}`

## GUI Usage
- **Create Rule:** Input a rule string, e.g., `"(age > 30 AND department = 'Sales')"`
- **Combine Rules:** Provide rule IDs separated by commas, e.g., `1, 2`.
- **Evaluate Rule:** Enter a rule ID and JSON data for evaluation.
- **Modify Rule:** Input a rule ID and new rule string.

## Testing
Use `test_script.py` to run through basic operations:
1. Creates two rules.
2. Combines the rules.
3. Evaluates the combined rule.
4. Modifies a rule and evaluates again.

## Troubleshooting
- **Database Connection Issues:** Ensure SQLite dependencies are correctly installed.
- **Flask Errors:** Check `app.py` for port conflicts or dependencies.
- **GUI Issues:** Ensure Tkinter is installed (should be included with most Python installations).
