def robot_reply(message):
    message = message.lower()

    if "hello" in message:
        return "Hello! 👋"
    elif "your name" in message:
        return "I'm your robot!"
    elif "how are you" in message:
        return "I'm doing great!"
    elif "bye" in message:
        return "Goodbye!"
    else:
        return "You said: " + message


print("Robot: Hi! Type something to me.")
print("Type 'quit' to stop.\n")

while True:
    message = input("You: ")

    if message.lower() == "quit":
        print("Robot: Goodbye!")
        break

    print("Robot:", robot_reply(message))