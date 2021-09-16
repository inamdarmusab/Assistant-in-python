# Assistant-in-python
this is Personal assistant made in python

import speech_recognition as sr
import pyttsx3
import datetime
import webbrowser
import wikipedia
import pyjokes
import os
import pywhatkit
import tkinter
from tkinter import *
# import PyAudio
from bs4 import BeautifulSoup
# import 


engine = pyttsx3.init('sapi5')
voices = engine.getProperty('voices')
engine.setProperty('voice', voices[1].id)
engine.setProperty('rate', 190)

def speak(audio):
    engine.say(audio)
    engine.runAndWait()

def wishMe():
    hour = (datetime.datetime.now().hour)
    if hour >= 0 and hour<12:
        speak("good morning")
    elif hour >= 12 and hour < 24:
        speak("good afternoon")
    else:
        speak("good evening")
    
    assname = ("glance")
    speak(f"i am your personal assistant{assname}")

def takeCommands():
    
    r = sr.Recognizer()
    with sr.Microphone() as source:
        print("Listening ...")
        speak("Listening ...")
        r.pause_threshold = 0.8
        r.energy_threshold = 300

        audio = r.listen(source)

    try:
        print("recognizing ...")
        query = r.recognize_google(audio , language='en-in')
        print(f"user said : {query} \n ")
    
    except Exception as e:
        print(e)
        print("say that again...")
        speak("say that again...")
        return "None"

    return query

if __name__ == '__main__':


    clear = lambda: os.system('cls')
    wishMe()

    while True :

        query = takeCommands()

        if 'glance' in query or 'glans' in query or '' in query:
        
            if 'open YouTube' in query:
                speak("openning youtube \n")
                webbrowser.open("www.youtube.com")

            if 'open Google' in query:
                speak("openning google \n")
                webbrowser.open("www.google.com")
                
            if 'open chrome' in query:
                speak("openning chrome \n")
                webbrowser.open("google.com")

            if 'stack overflow' in query:
                speak("openning stackoverflow \n")
                webbrowser.open("www.stackoverflow.com")

            if 'WhatsApp' in query:
                speak("openning whatsapp \n")
                webbrowser.open("https://web.whatsapp.com/")
            
            if 'kurulus Osman' in query:
                speak("openning kurulus osman \n")
                webbrowser.open("https://historicseries.com/kurulus-osman/")

            if 'saljuk' in query:
                speak("openning kurulus osman \n")
                webbrowser.open("https://historicseries.com/uyanis-buyuk-selcuklu/")
                        
            if 'Mendirman Jaloliddin' in query or '':
                speak("openning kurulus osman \n")
                webbrowser.open_new_tab("https://historicseries.com/mendirman-jalaluddin/")
                
            if 'hai' in query:
                speak("hii Sir how can i help you")
                
            if 'hello' in query:
                speak("hello Sir how can i help you")
                
            if 'glance' in query:
                speak("yes Sir how can i help you")
                
            if 'who are' in query or 'what is your name' in query or 'tell me about your self' in query:
                speak("i am glance. a personal assistant created by musab inamdar")

                
            if 'joke' in query:
                speak("which language you prefer")

                speak(pyjokes.get_joke())
                print(pyjokes.get_joke())
               

            if 'date' in query:
                date = datetime.datetime.now().strftime("%d-%m-%Y")
                speak("current date is")
                speak(date)
            
            
            if 'the time' in query:
                strTime = datetime.datetime.now().strftime("% H:% M:% S")   
                speak(f"Sir, the time is {strTime}")
                
            if 'play' in query or 'song' in query:
                song = query.replace('play','')
                speak("playing" + song)
                pywhatkit.playonyt(song)

            if 'what' in query or 'who' in query:
                a = pywhatkit.search(query)
                speak(a)
            
            if 'send message to musab' in query:
                speak('message will send to musab by given time')
                pywhatkit.sendwhatmsg(f"+91{9767255056}","hii how was your project going on",10,45)
                speak("message will be sent on 10:45")

            if 'shutdown' in query:
                speak('shutting down')
                pywhatkit.shutdown(time=1000)
                speak("pc will turn off in 1000 seconds ")

            if 'cancel shutdown' in query:
                pywhatkit.cancel_shutdown()
                speak("cancel shutdown")

            if 'Wikipedia' in query:
                speak('Searching Wikipedia...')
                query = query.replace("wikipedia", "")
                results = wikipedia.summary(query, sentences=2)
                speak("According to Wikipedia")
                print(results)
                speak(results)

            if 'vs code' in query or 'code' in query:
                path = "C:\\Users\\Musab Inamdar\\AppData\\Local\\Programs\\Microsoft VS Code\\Code.exe"
                os.startfile(path)
                
            if 'ok alexa' in query:
                speak("who is alexa")
                try:
                    speak("who is...alexa."   +  "go and ask her ")
                except:
                    pass
            
            if 'ok google' in query:                    
                speak("who is google")
                try:
                    speak("who is...google."  +  "go and ask her ")
                    exit()
                except:
                    pass

            if 'ok siri' in query:
                speak("who is siri")
                try:
                    speak("who is...siri."   +  "go and ask her ")
                except:
                    pass
            
            
            
            
            if 'quit' in query or 'exit' in query:
                exit()
