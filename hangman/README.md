# Hangman

Hangman is a classic word-guessing game where a player attempts to guess a hidden word by suggesting letters within a limited number of attempts.

For this challenge, you will build a console-based Hangman game step by step, starting from core logic through to a configurable CLI.

## ⚠️ Note

There is far too much work here to be done in the time you've been given. You are not expected to complete the whole challenge.

## Tasks

Work through the following tasks in order.

Each task should be completed before moving on to the next. Completing a later task should not invalidate the solution for an earlier one.

1. Core masking logic: given a secret word and a set of guessed letters, render the masked word.

   - Treat the game as case-insensitive. The output should use uppercase letters.
   - Only letters A-Z are maskable. All other characters (spaces, hyphens, apostrophes, numbers, punctuation) should be shown as-is and should not need to be guessed.
   - Unrevealed letters should be displayed as `_`.
   - Examples:
     - secret: `OPAL`, guesses: `{'A', 'O'}` --> `O _ A _`
     - secret: `WOLVES`, guesses: `{'E', 'S', 'W'}` --> `W _ _ _ E S`
     - secret: `SEA-LION`, guesses: `{'S', 'A', 'O'}` --> `S _ A - _ _ O _`
     - secret: `O'CLOCK`, guesses: `{'C', 'L'}` --> `_ ' C L _ C _`
     - secret: `BEE 123`, guesses: `{'B'}` --> `B _ _ 1 2 3`

2. Guess processing: given the current game state, process a new guess character and update the state.

   - Accept only single alphabetic characters A-Z. Non-letters should be rejected with a clear error.
   - Normalise input to uppercase.
   - If the letter has already been guessed, return a no-op state change and indicate it was a duplicate.
   - Examples, starting with secret `WOLVES`, remaining_lives 6:
     - state: guessed_correct `{W}`, guessed_incorrect `{}`, guess: `o` --> correct, guessed_correct becomes `{W, O}`, remaining_lives stays 6.
     - state: guessed_correct `{W, O, L, E, S}`, guessed_incorrect `{}`, guess: `X` --> incorrect, guessed_incorrect becomes `{X}`, remaining_lives becomes 5.
     - state: guessed_correct `{W, O}`, guessed_incorrect `{X}`, guess: `x` --> duplicate incorrect guess, no change, remaining_lives stays 5.
     - state: guessed_correct `{W}`, guessed_incorrect `{X}`, guess: `!` --> invalid input, reject with error, no change.

3. Win and loss detection: determine when the game has ended.

   - Win condition: all letters A-Z in the secret word have been revealed by `guessed_correct` (case-insensitive).
   - Loss condition: `remaining_lives` drops to 0 after processing an incorrect guess.
   - The game should not end on duplicate guesses or invalid inputs.
   - Examples:
     - secret: `BEE`, guessed_correct `{B, E}`, remaining_lives 3 --> win.
     - secret: `SEA-LION`, guessed_correct contains all letters in `SEALION`, remaining_lives 1 --> win.
     - secret: `OPAL`, guessed_correct `{O, A}`, guessed_incorrect `{X, Y, Z, Q, R, T}`, remaining_lives 0 --> loss.

4. Visual feedback: render a gallows or lives indicator corresponding to the number of incorrect guesses.

   - Provide an ASCII art rendering for at least 7 stages from full health to game over, or a simple hearts/counters display if you prefer.
   - The rendering should be purely a function of `max_lives` and `remaining_lives`.
   - Example stages for `max_lives = 6`:

     - 6 lives:
       `

       +---+
       | |
       |
       |
       |
       |
       ========
       `

     - 5 lives:
       `

       +---+
       | |
       O |
       |
       |
       |
       ========
       `

     - 4 lives:
       `

       +---+
       | |
       O |
       | |
       |
       |
       ========
       `

     - 3 lives:
       `

       +---+
       | |
       O |
       /| |
       |
       |
       ========
       `

     - 2 lives:
       `

       +---+
       | |
       O |
       /|\ |
       |
       |
       ========
       `

     - 1 life:
       `

       +---+
       | |
       O |
       /|\ |
       / |
       |
       ========
       `

     - 0 lives:
       `

       +---+
       | |
       O |
       /|\ |
       / \ |
       |
       ========
       `

5. Interactive CLI: build a command-line game loop that ties everything together.

   - Behaviour:
     - On start, show the masked word, remaining lives, incorrect guesses, and gallows.
     - Prompt the user for a guess each turn.
     - After each valid guess, update and re-render the state.
     - On win or loss, display an appropriate message and reveal the full word.
   - Input handling:
     - Case-insensitive.
     - Reject multi-character inputs and non-letters with a clear message.
     - Treat empty input as invalid and prompt again.
   - Configuration:
     - Allow `--secret` to specify a secret word directly, for deterministic testing.
     - If `--secret` is not provided, load a word at random from a built-in list or a provided `--wordlist` file path.
     - Support `--lives` to set the number of lives. Default 6.
     - Optional `--seed` to make random selection reproducible.
   - Example session:
     - Secret: `OPAL`, lives: 6
       - Display:
         - Mask: `O _ _ _`
         - Incorrect: `-`
         - Lives: 6
         - Gallows: stage 6
       - Input: `a` -> Mask `O _ A _`, Lives 6
       - Input: `x` -> Incorrect `X`, Lives 5
       - Input: `l` -> Mask `O _ A L`, Lives 5
       - Input: `p` -> Win. Reveal `OPAL`.

6. Advanced options and extensibility.
   - Whole-word guesses:
     - Allow the user to guess the entire word by entering more than one alphabetic character.
     - A correct whole-word guess immediately wins.
     - An incorrect whole-word guess should decrement lives by 1 by default, or optionally by `--word-penalty` if provided.
   - Display options:
     - `--hidden-symbol` to change the placeholder for unrevealed letters (default `_`), e.g. `--hidden-symbol "*"`.
     - `--space-symbol` to change how spaces are displayed inside the mask (default actual space), e.g. `--space-symbol "/"`.
     - `--show-duplicates` to either penalise duplicate guesses or not, e.g. `--show-duplicates=ignore|warn|penalise` where penalise decrements lives on duplicate incorrect guesses.
   - I/O variants:
     - Support non-interactive mode via `--play <sequence>`, where `<sequence>` is a comma-separated list of guesses to process in order, useful for automated tests.
     - Example:
       - `--secret WOLVES --play w,o,x,l,e,s`
       - Output final result and transcript.

Notes and clarifications

- Only letters A-Z should be guessable. The game should never require guessing punctuation, digits, or spaces, and these should display as given.
- Normalise secrets from external sources to uppercase A-Z plus allowed non-letters. Accented characters may be stripped or rejected based on your design, but document the choice.
- The masking and rendering functions should be pure where practical to simplify testing.
- Provide unit tests for:
  - Masking logic, including mixed case and non-letters.
  - Guess processing, including duplicates and invalid input.
  - Win/loss detection.
  - Gallows rendering boundaries at 0 and max lives.
