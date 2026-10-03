import random

def play_game():
    print("=== Welcome to the Number Guessing Game ===")
    print("I'm thinking of a number between 1 and 100.")
    
    # Generate a random secret number
    secret_number = random.randint(1, 100)
    attempts = 0
    max_attempts = 10

    while attempts < max_attempts:
        try:
            guess = int(input(f"\nAttempt {attempts + 1}/{max_attempts}. Enter your guess: "))
        except ValueError:
            print("Invalid input. Please enter a valid whole number.")
            continue
            
        attempts += 1

        # Check the player's guess
        if guess == secret_number:
            print(f"🎉 Congratulations! You guessed the number in {attempts} attempts!")
            return True
        elif guess < secret_number:
            print("Too low! Try a higher number.")
        else:
            print("Too high! Try a lower number.")
            
    print(f"\n😢 Game Over! You've run out of attempts. The number was {secret_number}.")
    return False

def main():
    playing = True
    while playing:
        play_game()
        choice = input("\nDo you want to play again? (yes/no): ").strip().lower()
        if choice not in ['yes', 'y']:
            playing = False
            print("Thanks for playing! Goodbye.")

if __name__ == "__main__":
    main()
