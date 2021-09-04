# Light-bot-
light bot created by python codes

from typing import ContextManager
from urllib.parse import uses_query
import pyttsx3
import speech_recognition as sr
import datetime
import wikipedia
import webbrowser
import os
import smtplib

engine=pyttsx3.init('sapi5')
voices=engine.getProperty('voices')
# print(voices[0].id)

def speak(audio):
    engine.say(audio)
    engine.runAndWait()

def wishMe():
    hour = int(datetime.datetime.now().hour)
    if hour>=0 and hour<12:
        speak("good morning!")

    elif hour>=12 and hour<18:
        speak("Good afternoon!")

    else:
        speak("good evening!")

    speak("i am light sir. please tell me how may i help you")

def takecommand():
    #it take microphone input from the user and return string output

    r=sr.Recognizer()
    with sr.Microphone() as source:.....")
        r.pause_threshold =1
        print("listening
        audio=r.listen(source)

    try:
        print("recognizing")
        query = r.recognize_google(audio, language='en-in')
        print(f"user said: {query}\n")

    except Exception as e:
        #print(e)
        print("say that again please...")
        return "None"
     
    return query         

def new_func():
    return "play music"

def sendemail(do, content):
    server = smtplib.SMTP('smtp.gmail.com', 587)
    server.ehlo()
    server.starttls()
    server.login('anirudhjoshi.36@gmail.com', 'your password')
    server.sendmail('receiveremail@gmail.com', to , content)
    server.close()

if __name__ == "__main__":
   wishMe()
   #while True:
   if 1:
       query = takecommand().lower()

       if 'wikipedia' in query:
           speak ('Searching wikipedia.....')
           query=query.replace("Wikipedia","")
           results = wikipedia.summary(query, sentences=2)
           speak("According to wikipedia")
           speak(results)

       elif 'open youtube' in query:
            webbrowser.open("youtube.com")

       elif 'open google' in query:
            webbrowser.open("google.com")

       elif 'the time' in query:
           strTime = datetime.datetime.now().strftime("%H:%M:%S")
           speak(f"sir, the time is {strTime}")



       elif 'open code' in query:
           codePath ="C:\\Program Files\\Microsoft VS Code\\Code.exe"
           os.startfile(codePath)

       elif 'email to varun' in query:
           try:
               speak("what should i say")
               Content = takecommand()
               to = "receiver email@gmail.com"
               sendemail(to, Content)
               speak("Email has been sent!")
           except Exception as e:
                print(e)
                speak("sorry my friend anirudh bhai i am not able to send this email")
