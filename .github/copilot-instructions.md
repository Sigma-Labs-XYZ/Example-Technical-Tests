# Copilot Instructions: Coding Exercise Repository

## Purpose

This is a collection of **45-60 minute pair programming exercises** designed for technical interviews. Each exercise is self-contained in its own directory and intended to be solved incrementally with an interviewer as navigator and candidate as driver.

## Key Characteristics

### Progressive Difficulty

- **Every exercise uses incremental tasks**: Start simple, add complexity progressively
- Tasks are numbered and **must be completed in order**
- Later tasks build on earlier ones without invalidating previous solutions
- Most exercises have **deliberately more work than can be completed** in the time limit (explicitly noted with ⚠️ warnings)

### Problem Structure Patterns

**Incremental complexity exercises** (`colours`, `darts`, `digits`, `morse`, `palindromes`, `scrabble`, `hangman`):

- Start with a pure function solving a simple case
- Add optional parameters and edge cases
- Introduce external data (files, APIs)
- Build interactive CLIs or advanced features
- Example: `morse` goes from translating single sequences → handling sentences → encoding → CLI tool → configurable symbols

**State management exercises** (`21s`, `connect4`, `fruit-machine`, `game-of-life`, `warehouse-robot`):

- Model game state/entities first
- Implement core rules/logic
- Add win/loss conditions
- Handle edge cases and constraints
- Extend with variants or optimizations
- Example: `warehouse-robot` starts with simple grid movement → add crate lifting → optimize with diagonal paths

**Data processing exercises** (`election-results`, `snack-shack`, `split-the-treasure`):

- Parse/transform input data
- Handle malformed data gracefully
- Add business logic constraints
- Implement scheduling or resource management
- Example: `election-results` processes CSV-like data → validates → combines override files → calculates swings

## Implementation Guidelines

### When implementing solutions:

1. **Read the entire README** for the exercise to understand the full progression
2. **Solve tasks sequentially** - do not jump ahead or try to solve everything at once
3. **Keep solutions simple** - these are meant to demonstrate problem-solving approach, not production-ready code
4. **Focus on core logic first** - error handling and edge cases are secondary unless explicitly required
5. **Use test-driven approach** when possible - exercises often include example inputs/outputs

### Common patterns:

- **Case-insensitive string handling** (morse, hangman, palindromes, colours)
- **Working with external data files** - many exercises include sample data (e.g., `dictionary.txt`, `codes.csv`, `sample_results.txt`, `words.txt`)
- **Input validation** - rejecting invalid inputs with clear error messages
- **State machines** - tracking game state, player turns, resource availability
- **ASCII art rendering** - visual feedback for games (hangman gallows, game of life grid)
- **Scheduling/sequencing** - time-based operations (snack-shack)

### Data file locations:

- `morse/codes.csv` - Morse code mappings
- `scrabble/dictionary.txt` - Valid Scrabble words
- `palindromes/words.txt` - Word list for analysis
- `election-results/sample_results.txt` - Sample election data

## Language Choice

These exercises are **language-agnostic**. Solutions can be in Python, JavaScript, Java, etc. Choose based on candidate preference or interviewer requirements.

## Testing Approach

While not all exercises specify tests, **TDD is encouraged**:

- Use examples from README as test cases
- Build incrementally, validating each step
- Exercises often provide specific input → output examples to guide testing

## Interactive Elements

Several exercises require interactive components:

- **CLI loops** (hangman, connect4, morse CLI)
- **REPL-based gameplay** (connect4)
- **User prompts** (hangman guesses)
- Keep these **simple and text-based** - no GUI required

## External Dependencies

Some exercises use external services:

- **Dictionary API** (`palindromes` - https://dictionaryapi.dev/)
- Handle API failures gracefully with `ValueError` or similar

## Constraints to Respect

Several exercises have **explicit prohibitions**:

- `palindromes`: Cannot use `reverse()`, slicing, or any string reversal
- `colours`: Must handle varying non-alphanumeric delimiters (except `#`)
- `hangman`: Only A-Z are maskable; preserve spaces, hyphens, apostrophes, numbers

## Time Management

For 45-60 minute sessions:

- Expect to complete 2-4 tasks in most exercises
- Don't aim for completion - demonstrate thinking and problem-solving
- Prioritize clean, working solutions over rushing through all tasks
