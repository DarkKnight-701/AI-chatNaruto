from colorama import Fore, init
responses = {
    "hello": [
        "Hello! How can I help you?",
        "Hi there!",
        "Hey! Nice to meet you."
    ],

    "how are you": [
        "I'm doing great!",
        "All systems operational.",
        "I am fine. Thanks for asking!"
    ],

    "your name": [
        "My name is Naruto AI.",
        "I am Nexus, your AI assistant."
    ],

    "time": [
        f"Current time is {datetime.datetime.now().strftime('%H:%M:%S')}"
    ],

    "date": [
        f"Today's date is {datetime.datetime.now().strftime('%d-%m-%Y')}"
    ],

    "python": [
        "Python is a powerful programming language.",
        "Python is excellent for AI and automation projects."
    ],

    "mit": [
        "MIT values creativity, projects, and strong academics.",
        "Building projects is a great way to strengthen your MIT profile."
    ]
}

# Save chat history
history_file = open("chat_history.txt", "a")

while True:
    user_input = input(Fore.GREEN + "You: ").lower()

    history_file.write(f"User: {user_input}\n")

    if user_input == "bye":
        print(Fore.RED + "Naruto AI: Goodbye! Have a great day.")
        history_file.write("Bot: Goodbye!\n")
        break

    found = False

    for key in responses:
        if key in user_input:
            bot_response = random.choice(responses[key])
            print(Fore.CYAN + "Naruto AI:", bot_response)
            history_file.write(f"Bot: {bot_response}\n")
            found = True
            break

    if not found:
        default_response = random.choice([
            "Interesting! Tell me more.",
            "I am still learning.",
            "Can you explain that differently?",
            "That's cool!"
        ])

        print(Fore.CYAN + "Naruto AI:", default_response)
        history_file.write(f"Bot: {default_response}\n")

history_file.close()
