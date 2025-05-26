import random
import time

def choose_difficulty():
    print("Select difficulty level:")
    print("1. Easy (1-50, 10 attempts)")
    print("2. Medium (1-100, 7 attempts)")
    print("3. Hard (1-200, 5 attempts)")

    while True:
        choice = input("Enter your choice (1/2/3): ").strip()
        if choice == '1':
            return 1, 50, 10
        elif choice == '2':
            return 1, 100, 7
        elif choice == '3':
            return 1, 200, 5
        else:
            print("Invalid choice. Please enter 1, 2, or 3.")

def play_game():
    lower, upper, attempts_allowed = choose_difficulty()
    number_to_guess = random.randint(lower, upper)
    attempts = 0

    print(f"\nI'm thinking of a number between {lower} and {upper}.")
    print(f"You have {attempts_allowed} attempts to guess it!\n")

    start_time = time.time()

    while attempts < attempts_allowed:
        try:
            guess = int(input(f"Attempt {attempts + 1}: Enter your guess: "))
        except ValueError:
            print("⚠️ Please enter a valid integer.\n")
            continue

        if guess < lower or guess > upper:
            print(f"⚠️ Please guess a number between {lower} and {upper}.\n")
            continue

        attempts += 1

        if guess < number_to_guess:
            print("Too low!\n")
        elif guess > number_to_guess:
            print("Too high!\n")
        else:
            end_time = time.time()
            print(f"🎉 Correct! You guessed it in {attempts} attempts.")
            print(f"⏱️ Time taken: {end_time - start_time:.2f} seconds.\n")
            return

    end_time = time.time()
    print(f"😢 Out of attempts! The number was {number_to_guess}.")
    print(f"⏱️ Time taken: {end_time - start_time:.2f} seconds.\n")

def main():
    while True:
        play_game()
        again = input("Do you want to play again? (yes/no): ").strip().lower()
        if again not in ("yes", "y"):
            print("Thanks for playing! Goodbye!")
            break

if __name__ == "__main__":
    main()# Python-
