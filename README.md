AI_piano player

A small desktop app (Tkinter) that asks Gemini for the melody notes of a song, then sends them over serial to an Arduino with a buzzer that plays them. The user must type a song name and the Arduino plays it for you.

How it works
Open the app on the laptop (I have a shortcut for it)
Type in a song name and hit Play
The app asks the Gemini API for the notes and durations
Each note gets turned into a frequency and sent to the Arduino over USB
The Arduino sketch (.ino) reads them and plays the tones

The app only works if the Arduino is detected on the COM port. If it's not plugged in, it won't start.

Files
gui.py - the app window. It is the file that has to be run
gemini_notes.py - asks Gemini for the notes
arduino_sender.py - sends the notes to the Arduino
*.ino - the Arduino sketch that receives and plays them
background.png - background image for the window

Setup

Install the libraries:
pip install customtkinter pillow pyserial google-genai python-dotenv

Make a .env file next to the code with your Gemini key:

API_KEY=your_key_here

Upload the .ino sketch to the Arduino first.

Then check arduino_sender.py and change COM3 to whatever port your Arduino shows up on (Device Manager or the Arduino IDE will tell you). Baud rate is 9600 and it needs to match the sketch.

Run
python gui.py
Notes
The notes come from an AI, so they're not always the right melody. Some songs sound better than others. In general songs which are copyrighted won't sound that nice since the AI cannot give th eentire notes freely.
