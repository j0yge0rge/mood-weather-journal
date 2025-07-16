🌤 Mood & Weather Journal with n8n, Telegram & Google Sheets
This project is an automation workflow built using n8n that lets you log your daily mood along with Cairo's current weather in a Google Sheet — all triggered by a simple message to a Telegram bot.

🚀 Features
✅ Telegram bot collects your daily mood

🌦️ Pulls real-time weather data for Cairo, Egypt from OpenWeather API

🧾 Logs mood + weather + timestamp to Google Sheets

⏰ Optional: can be extended to auto-check-in daily at 9am

🔧 Tools & Integrations
n8n (self-hosted or cloud)

Telegram Bot (via BotFather)

Google Sheets

OpenWeatherMap API

🛠 Setup Instructions
Create a new Telegram bot via BotFather

Set up a Google Sheet with columns:
Date & Time | Mood | Weather | Temperature (°C)

In n8n:

Add a Telegram Trigger node (On Message)

Add an HTTP Request node with OpenWeatherMap API:

bash
Copy code
https://api.openweathermap.org/data/2.5/weather?q=Cairo,EG&appid=YOUR_API_KEY&units=metric
Add a Google Sheets node → Append Row

Use the following expressions:

Field	Expression
Date & Time	{{$now}}
Mood	{{$node["Telegram Trigger"].json.message.text}}
Weather	{{$node["HTTP Request"].json.weather[0].main}}
Temperature (°C)	{{$node["HTTP Request"].json.main.temp}}

📷 Sample Output
A Google Sheet row will look like this:

Date & Time	Mood	Weather	Temp (°C)
2025-07-16 08:30:00	feeling tired but hopeful	Clear	29.7

📈 Extensions Ideas
Daily reminders via Telegram using Cron + Telegram Send Message node

Visualize mood trends with Data Studio or Looker

Use ChatGPT API to summarize your mood every week

💡 Why I Built This
To learn automation with n8n and build something useful, personal, and fun! It helps track mental state and see how weather might influence it 🌤🧠

