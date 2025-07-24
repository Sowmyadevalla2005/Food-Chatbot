# Food Chatbot

A simple food ordering chatbot built with FastAPI (Python backend), MySQL, Dialogflow, and a web frontend. This project demonstrates how to integrate a conversational AI with a restaurant ordering system.

---

## Features
- Place new food orders via chat
- Track existing orders
- Menu-based ordering with quantity
- Dialogflow Messenger integration for web chat
- MySQL database for order storage and tracking

---

## Screenshot
Here is what the chatbot looks like in action:

![ChatBot Screenshot](frontend/image.png)

---

## Project Structure
- `backend/` — FastAPI backend code
- `db/` — MySQL database dump (`pandeyji_eatery.sql`)
- `dialogflow_assets/` — Dialogflow training phrases and assets
- `frontend/` — Website files (HTML, CSS, images)

---

## Setup Instructions

### 1. Install Python Dependencies
```sh
pip install -r backend/requirements.txt
```

### 2. Set Up the Database
- Open MySQL Workbench (or your preferred MySQL client).
- Create a database named `pandeyji_eatery`.
- Import `db/pandeyji_eatery.sql` into your MySQL server.
- Update `backend/db_helper.py` with your MySQL username and password if needed.

### 3. Start the Backend Server
```sh
cd backend
uvicorn main:app --reload
```
- The backend will run at [http://127.0.0.1:8000](http://127.0.0.1:8000)

### 4. (Optional) Expose Backend to Internet (for Dialogflow)
- Download ngrok from [ngrok.com](https://ngrok.com/download)
- Run:
  ```sh
  ngrok http 8000
  ```
- Use the HTTPS URL provided by ngrok as your webhook URL in Dialogflow.

### 5. Set Up Dialogflow
- Create a Dialogflow agent.
- Add intents and training phrases (see `dialogflow_assets/training_phrases.txt` for examples).
- In Fulfillment, set the webhook URL to your ngrok HTTPS URL (ending with `/`).
- Enable webhook for relevant intents.

### 6. Run the Frontend
- Open `frontend/home.html` in your web browser.
- You will see a chat bubble (Dialogflow Messenger) to interact with the bot.

---

## Troubleshooting
- **Database errors:** Check your MySQL credentials and that the database is imported.
- **Dialogflow returns default responses:** Improve your intent training phrases and entity annotations.
- **Webhook not called:** Ensure ngrok and backend server are running, and the webhook URL is correct in Dialogflow.

---

## License
This project is for educational purposes. Feel free to use and modify it for your own learning or projects.
