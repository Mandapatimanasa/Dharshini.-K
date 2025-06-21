import random

def hangman():
    # Step 1: Predefined list of words
    word_list = ['apple', 'banana', 'grape', 'orange', 'mango']
    word_to_guess = random.choice(word_list)
    guessed_letters = []
    attempts_left = 6

    # Step 2: Game loop
    print("🎮 Welcome to Hangman!")
    
    while attempts_left > 0:
        # Step 3: Show current word state
        display_word = ""
        for letter in word_to_guess:
            if letter in guessed_letters:
                display_word += letter
            else:
                display_word += "_"
        
        print("Word: " + " ".join(display_word))
        print(f"Guessed Letters: {', '.join(guessed_letters)}")
        print(f"Attempts Left: {attempts_left}")

        # Step 4: Get user input
        guess = input("Guess a letter: ").lower()

        if len(guess) != 1 or not guess.isalpha():
            print("⚠️ Please enter a single letter.")
            continue

        if guess in guessed_letters:
            print("❗ You already guessed that letter.")
            continue

        guessed_letters.append(guess)

        if guess in word_to_guess:
            print("✅ Good guess!")
        else:
            print("❌ Wrong guess!")
            attempts_left -= 1

        # Step 5: Check win condition
        if all(letter in guessed_letters for letter in word_to_guess):
            print(f"\n🎉 Congratulations! You guessed the word: {word_to_guess}")
            break
    else:
        print(f"\n💀 Game Over! The word was: {word_to_guess}")

# Run the game
hangman()
