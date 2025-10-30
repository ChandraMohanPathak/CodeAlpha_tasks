# CodeAlpha_tasks

🧩 TASK 1: Hangman Game
Goal: Simple text-based hangman game.
Python
import random

def hangman():
    words = ["apple", "banana", "grapes", "orange", "mango"]
    word = random.choice(words)
    guessed_letters = []
    attempts = 6
    print("Welcome to Hangman!")
    print("_ " * len(word))

    while attempts > 0:
        guess = input("\nGuess a letter: ").lower()

        if len(guess) != 1 or not guess.isalpha():
            print("Please enter only one letter.")
            continue

        if guess in guessed_letters:
            print("You already guessed that letter!")
            continue

        guessed_letters.append(guess)

        if guess in word:
            print("Good guess!")
        else:
            attempts -= 1
            print(f"Wrong guess! {attempts} attempts left.")

        display_word = "".join([letter if letter in guessed_letters else "_" for letter in word])
        print("Word:", " ".join(display_word))

        if "_" not in display_word:
            print("\n🎉 Congratulations! You guessed the word:", word)
            break
    else:
        print("\n😢 You ran out of attempts. The word was:", word)

hangman()

💹 TASK 2: Stock Portfolio Tracker
Goal: Calculate total investment using predefined stock prices.
Python
# Simple Stock Portfolio Tracker

stock_prices = {
    "AAPL": 180,
    "TSLA": 250,
    "GOOG": 140,
    "MSFT": 330
}

total_investment = 0
portfolio = {}

while True:
    stock = input("\nEnter stock symbol (or 'done' to finish): ").upper()
    if stock == "DONE":
        break

    if stock in stock_prices:
        quantity = int(input(f"Enter number of shares for {stock}: "))
        investment = stock_prices[stock] * quantity
        total_investment += investment
        portfolio[stock] = portfolio.get(stock, 0) + quantity
    else:
        print("Stock not found in list!")

print("\nYour Portfolio Summary:")
for stock, qty in portfolio.items():
    print(f"{stock}: {qty} shares @ ${stock_prices[stock]} each")

print(f"\nTotal Investment Value: ${total_investment}")

⚙️ TASK 3: Task Automation Script
Example: Move all .jpg files from one folder to another.
Python
import os
import shutil

source_folder = "source_images"
destination_folder = "moved_images"

# Create folders if they don't exist
os.makedirs(source_folder, exist_ok=True)
os.makedirs(destination_folder, exist_ok=True)

for file in os.listdir(source_folder):
    if file.endswith(".jpg"):
        shutil.move(os.path.join(source_folder, file), os.path.join(destination_folder, file))
        print(f"Moved: {file}")

print("✅ All .jpg files moved successfully!")
💡 To test this, create folders named source_images and moved_images in your project directory.

💬 TASK 4: Basic Chatbot
Goal: Rule-based chatbot with predefined replies.
Python
def chatbot():
    print("Chatbot: Hi! I'm your assistant. Type 'bye' to exit.")
    
    while True:
        user = input("You: ").lower()

        if user in ["hello", "hi"]:
            print("Chatbot: Hello there! How are you?")
        elif user in ["how are you", "how are you?"]:
            print("Chatbot: I'm just a program, but I'm doing great! 😊")
        elif user in ["i'm fine", "fine", "good"]:
            print("Chatbot: Nice to hear that!")
        elif user == "bye":
            print("Chatbot: Goodbye! Have a great day! 👋")
            break
        else:
            print("Chatbot: Sorry, I didn't understand that.")

chatbot()
