# 🧪 Local LLM Test Case Generator

A secure, local-first application that generates professional QA test suites from feature requirements using **Ollama** and **Python**. No data leaves your machine.

---

## 🏗️ Architecture Diagram

```mermaid
graph TD
    User([👤 User]) -->|Enters Requirement| UI[💻 Streamlit Frontend]
    UI -->|Sends Prompt| Logic[⚙️ Backend Generator]
    Logic -->|API Call (JSON Mode)| Ollama[🦙 Ollama Local Server]
    
    subgraph Local Machine
        Ollama -->|Inference| Model{🧠 LLM Model}
        Model -->|gemma3:1b / llama3.2| Ollama
    end
    
    Ollama -->|Structured JSON| Logic
    Logic -->|Parsed Test Cases| UI
    UI -->|Visual Cards / CSV Export| User
```

---

## 🚀 Features
*   **100% Local**: Uses Ollama API; no cloud tokens or internet required for generation.
*   **Structured Output**: Generates strict JSON for reliable parsing.
*   **Multi-Model Support**: Switch between `gemma3:1b`, `llama3.2`, `mistral`, etc.
*   **Export Ready**: Download test cases as **CSV** or copy as **JSON**.
*   **Premium UI**: Dark mode, distinct priority badges, and tabbed views.

## 📂 Project Structure
```bash
Project1-LocalTestCaseGenerator/
├── architecture/        # SOPs and Logic Blueprints
├── backend/             # Core Logic
│   ├── generator.py     # Ollama interaction & parsing logic
│   └── requirements.txt # Python dependencies
├── frontend/            # User Interface
│   └── app.py           # Streamlit Application
├── tools/               # Utility Scripts
│   └── verify_ollama.py # Connection Test Script
└── README.md            # Documentation
```

## 🛠️ Prerequisites
1.  **Ollama**: [Download Ollama](https://ollama.com/) and run it.
2.  **Pull a Model**:
    ```bash
    ollama pull gemma3:1b
    # OR
    ollama pull llama3.2
    ```
3.  **Python 3.10+**

## ⚡ Quick Start

1.  **Install Dependencies**
    ```bash
    pip install -r backend/requirements.txt
    ```

2.  **Run the App**
    ```bash
    streamlit run frontend/app.py
    ```

3.  **Generate Tests**
    *   Open `http://localhost:8501`.
    *   Select your model in the sidebar.
    *   Type a requirement (e.g., *"Signup page with email verification"*).
    *   Export your results!

---

## 🛡️ License
MIT
