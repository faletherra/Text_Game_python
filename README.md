# Text_Game_python

import random

# Define dictionary of game options
game_options = {
    "1": "rock",
    "2": "paper",
    "3": "scissors",
    "4": "lizard",
    "5": "spock"
}

# Define dictionary of game rules
game_rules = {
    "rock": ["scissors", "lizard"],
    "paper": ["rock", "spock"],
    "scissors": ["paper", "lizard"],
    "lizard": ["spock", "paper"],
    "spock": ["rock", "scissors"]
}

game_results = {
    "win": "You win!",
    "lose": "You lose!",
    "draw": "It's a draw!"
}

# Define function to get user input
def get_user_input():
    user_input = input("Enter your choice: ").lower()
    while user_input not in game_options.keys() and user_input not in game_options.values():
        print("Invalid choice. Please try again")
        user_input = input("Enter your choice: ").lower()
    
    # Convert numeric input to corresponding game option
    if user_input in game_options.keys():
        return game_options[user_input]
    return user_input

# Define function to get computer input
def get_computer_input():
    return random.choice(list(game_options.values()))

# Define function to determine game result
def get_game_result(user_input, computer_input):
    if user_input == computer_input:
        return game_results["draw"]
    elif computer_input in game_rules[user_input]:
        return game_results["win"]
    else:
        return game_results["lose"]

# Define function to display game result
def display_game_result(result, user_input, computer_input):
    print(f"User choice: {user_input}")
    print(f"Computer choice: {computer_input}")
    print(result)

# Define main function
def main():
    # Display welcome message
    print("Welcome to Rock-paper-scissors-lizard-spock game!")
    # Display game options
    print("Game options: ")
    for key, value in game_options.items():
        print(f"{key}: {value}")
    # Get user input
    user_input = get_user_input()
    computer_input = get_computer_input()
    result = get_game_result(user_input, computer_input)
    display_game_result(result, user_input, computer_input)

# Call main function
main()

