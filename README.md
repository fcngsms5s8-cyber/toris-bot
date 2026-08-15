import speech_recognition as sr
import pyttsx3

# Set up the robot's voice
robot = pyttsx3.init()
robot.setProperty("rate", 170)

def speak(text):
    print("Robot:", text)
    robot.say(text)
    robot.runAndWait()

# Set up microphone and speech recognition
recognizer = sr.Recognizer()

speak("Hello! I am ready to listen.")

while True:
    try:
        with sr.Microphone() as source:
            print("Listening...")
            recognizer.adjust_for_ambient_noise(source, duration=0.5)
            audio = recognizer.listen(source)

        command = recognizer.recognize_google(audio)
        print("You:", command)

        if command.lower() in ["stop", "goodbye", "shut down"]:
            speak("Goodbye!")
            break

        # Basic responses
        if "hello" in command.lower():
            speak("Hello! Nice to meet you.")

        elif "your name" in command.lower():
            speak("I am your robot.")

        elif "how are you" in command.lower():
            speak("I am doing great!")

        else:
            speak("You said " + command)

    except sr.UnknownValueError:
        speak("Sorry, I didn't understand that.")

    except sr.RequestError:
        speak("I can't connect to the speech recognition service.")# toris-bot