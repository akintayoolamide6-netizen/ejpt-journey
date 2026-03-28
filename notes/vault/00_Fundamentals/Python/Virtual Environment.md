# Python Virtual Environment — Quick Notes

## Activate Virtual Environment

Windows: venv\Scripts\activate before (for clean environment)
Run above before: auto.py


---

## If Anything Breaks

Install dependencies:

pip install -r requirements.txt


---

## Common Issue

Package installs outside virtual environment.

Example: Requirement already satisfied in:   
C:\users\trade\appdata\local\programs\python\python311\lib\site-packages

This means package installed **globally**, not inside venv.

---

## Correct Fix

Use: python -m pip install gtts

This installs inside **active virtual environment**