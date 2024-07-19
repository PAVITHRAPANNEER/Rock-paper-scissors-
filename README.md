class RockPaperScissorsGame:
    def __init__(self):
        self.user_score = 0
        self.computer_score = 0
        self.choices = ['rock', 'paper', 'scissors']
        self.computer_choice_index = 0  

    def get_computer_choice(self):
        choice = self.choices[self.computer_choice_index]
        self.computer_choice_index = (self.computer_choice_index + 1) % len(self.choices)
        return choice

    def determine_winner(self, user_choice, computer_choice):
        if user_choice == computer_choice:
            return 'draw'
        elif (user_choice == 'rock' and computer_choice == 'scissors') or \
             (user_choice == 'paper' and computer_choice == 'rock') or \
             (user_choice == 'scissors' and computer_choice == 'paper'):
            return 'user'
        else:
            return 'computer'

    def play_round(self):
        user_choice = input("Enter your choice (rock, paper, or scissors): ").lower()
        while user_choice not in self.choices:
            print("Invalid choice. Please try again.")
            user_choice = input("Enter your choice (rock, paper, or scissors): ").lower()

        computer_choice = self.get_computer_choice()
        print(f"Computer chose: {computer_choice}")

        winner = self.determine_winner(user_choice, computer_choice)
        if winner == 'user':
            print("You win this round!")
            self.user_score += 1
        elif winner == 'computer':
            print("Computer wins this round!")
            self.computer_score += 1
        else:
            print("This round is a draw!")

    def display_scores(self):
        print(f"User Score: {self.user_score} | Computer Score: {self.computer_score}")

    def play_game(self):
        print("Welcome to Rock-Paper-Scissors Game!")
        while True:
            self.play_round()
            self.display_scores()
            play_again = input("Do you want to play again? (yes/no): ").lower()
            if play_again != 'yes':
                break
        print("Thanks for playing! Final scores:")
        self.display_scores()

if __name__ == "__main__":
    game = RockPaperScissorsGame()
    game.play_game()
