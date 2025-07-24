# Pandeyji ChatBot Project - Quick Start Guide

## Project Structure
- backend/: Python FastAPI backend code
- db/: MySQL database dump (pandeyji_eatery.sql)
- dialogflow_assets/: Dialogflow training phrases and assets
- frontend/: Website files (HTML, CSS, images)

## ChatBot Screenshot
Here is what the chatbot looks like in action:

![ChatBot Screenshot](frontend/chatbot_screenshot.png)

## Setup Instructions

1. **Install Python Dependencies**
   - Open a command prompt.
   - Run: `pip install -r backend/requirements.txt`

2. **Set Up the Database**
   - Open MySQL Workbench (or your preferred MySQL client).
   - Create a database named `pandeyji_eatery`.
   - Import `db/pandeyji_eatery.sql` into your MySQL server.
   - Update `backend/db_helper.py` with your MySQL username and password if needed.

3. **Start the Backend Server**
   - In the command prompt, go to the backend directory:
     `cd backend`
   - Start the server:
     `uvicorn main:app --reload`
   - The backend will run at http://127.0.0.1:8000

4. **(Optional) Expose Backend to Internet (for Dialogflow)**
   - Download ngrok from https://ngrok.com/download
   - Run: `ngrok http 8000`
   - Use the HTTPS URL provided by ngrok as your webhook URL in Dialogflow.

5. **Set Up Dialogflow**
   - Create a Dialogflow agent.
   - Add intents and training phrases (see `dialogflow_assets/training_phrases.txt` for examples).
   - In Fulfillment, set the webhook URL to your ngrok HTTPS URL (ending with /).
   - Enable webhook for relevant intents.

6. **Run the Frontend**
   - Open `frontend/home.html` in your web browser.
   - You will see a chat bubble (Dialogflow Messenger) to interact with the bot.

## Troubleshooting
- If you get database errors, check your MySQL credentials and that the database is imported.
- If Dialogflow returns default responses, improve your intent training phrases and entity annotations.
- If the webhook is not called, check your ngrok and backend server are running, and the webhook URL is correct.

Enjoy using ChatBot!
