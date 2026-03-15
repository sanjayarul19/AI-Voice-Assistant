# AI Voice Assistant

import speech_recognition as sr
import pyttsx3
import datetime
import webbrowser

# Initialize voice engine
engine = pyttsx3.init()

def speak(text):
    engine.say(text)
    engine.runAndWait()

def take_command():
    r = sr.Recognizer()

    with sr.Microphone() as source:
        print("Listening...")
        r.pause_threshold = 1
        audio = r.listen(source)

    try:
        print("Recognizing...")
        command = r.recognize_google(audio)
        print("You said:", command)
        return command.lower()

    except Exception as e:
        print("Error:", e)
        speak("Sorry, I did not understand.")
        return "none"


def run_assistant():
    speak("Hello Sanjay. I am your AI assistant. How can I help you?")

    while True:
        command = take_command()

        if "hello" in command:
            speak("Hello Sanjay, how are you?")

        elif "time" in command:
            time = datetime.datetime.now().strftime("%H:%M")
            speak("The time is " + time)

        elif "youtube" in command:
            webbrowser.open("https://www.youtube.com")
            speak("Opening YouTube")

        elif "google" in command:
            webbrowser.open("https://www.google.com")
            speak("Opening Google")

        elif "stop" in command or "exit" in command:
            speak("Goodbye Sanjay")
            break


run_assistant()







