# Rock-Paper-Scissors
To design and implement a Rock Paper Scissors game where the user plays against the  computer. The system should take user input, generate a computer choice randomly,  decide the winner, and display the result along with maintaining the score and history. 
🎮 Rock Paper Scissors Game using Python

An interactive Rock Paper Scissors game where the user plays against the computer. This project is built using Python and demonstrates core programming concepts like Object-Oriented Programming (OOP), loops, and conditional logic.

🚀 Features
👤 User vs Computer gameplay
🎲 Random computer choice
🏆 Score tracking system
🔁 Multiple rounds support
📜 Game history tracking
🧠 Clean and modular OOP design
🛠️ Technologies Used
Python 3
VS Code / IDLE
📌 How It Works
The game starts by displaying rules
User enters number of rounds
For each round:
User selects rock, paper, or scissors
Computer randomly selects a choice
Winner is decided based on game logic
Score is updated
After all rounds, final result and history are displayed
▶️ How to Run
python your_file_name.py
💻 Code
import random
import time

class Player:
    def __init__(self, name):
        self.name = name
        self.score = 0

    def add_point(self):
        self.score += 1


class Game:
    def __init__(self):
        self.choices = ["rock", "paper", "scissors"]
        self.user = Player("You")
        self.computer = Player("Computer")
        self.history = []

    def display_intro(self):
        print("\n🎮 WELCOME TO ROCK PAPER SCISSORS 🎮")
        print("-------------------------------------")
        print("Rules:")
        print("Rock beats Scissors")
        print("Paper beats Rock")
        print("Scissors beats Paper\n")

    def get_user_choice(self):
        while True:
            choice = input("Enter rock, paper, or scissors: ").lower()
            if choice in self.choices:
                return choice
            print("Invalid choice! Try again.")

    def get_computer_choice(self):
        return random.choice(self.choices)

    def decide_winner(self, user_choice, comp_choice):
        if user_choice == comp_choice:
            return "tie"
        elif (user_choice == "rock" and comp_choice == "scissors") or \
             (user_choice == "paper" and comp_choice == "rock") or \
             (user_choice == "scissors" and comp_choice == "paper"):
            return "user"
        else:
            return "computer"

    def update_score(self, winner):
        if winner == "user":
            self.user.add_point()
        elif winner == "computer":
            self.computer.add_point()

    def display_round_result(self, user_choice, comp_choice, winner):
        print(f"\nYou chose: {user_choice}")
        print(f"Computer chose: {comp_choice}")

        if winner == "tie":
            print("It's a tie!")
        elif winner == "user":
            print("You win this round!")
        else:
            print("Computer wins this round!")

    def save_history(self, user_choice, comp_choice, winner):
        self.history.append({
            "user": user_choice,
            "computer": comp_choice,
            "winner": winner
        })

    def show_score(self):
        print("\nSCOREBOARD")
        print(f"You: {self.user.score} | Computer: {self.computer.score}")

    def show_history(self):
        print("\nGAME HISTORY")
        for i, game in enumerate(self.history, start=1):
            print(f"Round {i}: You({game['user']}) vs Computer({game['computer']}) → {game['winner']}")

    def play(self):
        self.display_intro()
        
        rounds = int(input("Enter number of rounds: "))
        
        for i in range(1, rounds + 1):
            print(f"\nRound {i}")
            user_choice = self.get_user_choice()
            comp_choice = self.get_computer_choice()

            print("Computer is thinking...")
            time.sleep(1)

            winner = self.decide_winner(user_choice, comp_choice)
            self.update_score(winner)
            self.display_round_result(user_choice, comp_choice, winner)
            self.save_history(user_choice, comp_choice, winner)

            self.show_score()

        self.end_game()

    def end_game(self):
        print("\nGAME OVER")
        self.show_score()

        if self.user.score > self.computer.score:
            print("You are the overall winner!")
        elif self.user.score < self.computer.score:
            print("Computer is the overall winner!")
        else:
            print("It's an overall tie!")

        self.show_history()


if __name__ == "__main__":
    game = Game()
    game.play()
    <img width="1913" height="997" alt="Screenshot 2026-03-24 092259" src="https://github.com/user-attachments/assets/bd9c7501-aebd-4014-bbcc-3c548d372c04" />

📊 Sample Output
User selects option
Computer generates random choice
Round result displayed
Final winner + history shown
🎯 Learning Outcomes
Understanding OOP concepts (Classes & Objects)
Using loops and conditionals effectively
Building interactive console applications
Implementing real-world game logic
🙌 Conclusion

This project demonstrates how Python can be used to build simple yet interactive games while strengthening programming fundamentals.
