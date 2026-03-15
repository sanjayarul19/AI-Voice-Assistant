# AI-Voice-Assistant
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
    command =
r.recognize_google(audio) 
        print("You said:", command) 
    except: 
        speak("Sorry, I did not understand.") 
    return "none" 
   return command.lower() 
def run_assistant(): 
    speak("Hello Sanjay. I am your AI assistant. How can I help you?") 
   while True: 
       command = take_command() 
       if "hello" in command: 
           speak("Hello Sanjay, how are you?") 
       elif "time" in command: 
           time =datetime.datetime.now().strftime("%H:%M") 
           speak("The time is " + time) 
         elif "youtube" in command:
webbrowser.open("https://www.youtube.com")
        speak("opening youtube")
      else "google" in command:
webbrowser.open("https://www.google.com")
        speak("opening google")
      elif "stop" in command or "exite"
in command:
            speak("goodbye sanjay")
            break
run_assistant()






