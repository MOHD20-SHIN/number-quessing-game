# number-quessing-game

import random


def choose_level():
    """Ask the player to pick a difficulty and return (max_number, max_attempts)."""
    print("Choose a level:")
    print("  1. Easy   (1-10,  5 attempts)")
    print("  2. Medium (1-50,  7 attempts)")
    print("  3. Hard   (1-100, 7 attempts)")

    while True:
        choice = input("Enter 1, 2 or 3: ").strip()
        if choice == "1":
            return 10, 5
        elif choice == "2":
            return 50, 7
        elif choice == "3":
            return 100, 7
        else:
            print("Invalid choice. Please type 1, 2 or 3.")


def play_game():
    """Play one round of the game."""
    max_number, max_attempts = choose_level()
    secret = random.randint(1, max_number)
    attempts = 0

    print(f"\nI'm thinking of a number between 1 and {max_number}.")
    print(f"You have {max_attempts} attempts. Good luck!\n")

    while attempts < max_attempts:
        guess_text = input(f"Attempt {attempts + 1}/{max_attempts} - Your guess: ")

        # Make sure the player typed a number
        if not guess_text.isdigit():
            print("Please enter a valid whole number.\n")
            continue

        guess = int(guess_text)
        attempts += 1

        if guess == secret:
            print(f"\n🎉 Correct! You guessed it in {attempts} attempt(s).")
            return
        elif guess < secret:
            print("Too low! Try a bigger number.\n")
        else:
            print("Too high! Try a smaller number.\n")

    print(f"\n😢 Out of attempts! The number was {secret}.")


def main():
    print("=== Welcome to the Number Guessing Game ===\n")
    while True:
        play_game()
        again = input("\nPlay again? (y/n): ").strip().lower()
        if again != "y":
            print("Thanks for playing. Goodbye!")
            break
        print()


if __name__ == "__main__":
    main()
