# Darts

The game of [darts](https://en.wikipedia.org/wiki/Darts) involves players trying to reduce their score from an initial starting total by throwing 3 darts each round. Rounds continue until the first player hits zero exactly.

## ⚠️ Note

There is **far** too much work here to be done in the time you've been given. You are **not** expected to complete the whole challenge. 

## Tasks

Work through the following tasks **in order**. 

Each task should be completed **before** moving on to the next:

1. Given a round of dart scores, return an overall score. Some scores are more complicated than just a number; you should also be able to handle doubles, triples, and bullseyes (50 points).
   - `(10, 10, 9)` -> `29` (10, 10, 9)
   - `(2, 5)` -> `7` (2 and 5)
   - `((10, 'T'), (3, 'D'), 5)` -> `41` (triple 10, double 3, and 5)
   - `('BE', 1, (2, 'D'))` -> `55` (bullseye, 1, double 2)
2. Given a **list of rounds** for a single player and a **starting score**, identify if the player would win. The game only ends on hitting exactly zero. If a round would take a player below zero, the player does not win.
   - `[(10, 10, 10), (0, 5, 0)], 35` -> `True`
   - `[(2, 2, 2), (2, (2, 'T'), 2)], 300` -> `False`
   - `[(2, 2, 2), (2, (2, 'T'), 2)], 5` -> `False`
3. If a round would take a player to zero, but does not contain a bullseye, double, or triple, the player does not win.
   - `[(10, 10, 10)], 30` -> `False` (hits zero but no special dart)
   - `[(10, 10, (5, 'D'))], 30` -> `True` (hits zero with a double)
   - `[(5, (5, 'T'), 10)], 30` -> `True` (hits zero with a triple)
   - `[(1, (24, 'D'), 'BE')], 75` -> `True` (hits zero with a bullseye)
4. Given a list of rounds for **two players** and a starting score, return which player wins. If neither player wins, return `None`.
   - `p1=[(10, 10, 10), (0, 5, 0)], p2=[(20, 5, 5), (5, 5, 5)], start=35` -> `"p1"`
   - `p1=[(10, 10, 10)], p2=[(10, 10, (5, 'D'))], start=30` -> `"p2"` (p1 hits zero but no special dart)
   - `p1=[(1, 1, 1)], p2=[(2, 2, 2)], start=100` -> `None`
5. In a real game, once a player reaches exactly zero, the game stops — any remaining rounds are not played. Update your two-player game to track **how many rounds were played** before the game ended, and return both the winner and the round count.
   - `p1=[(10, 10, 10), (0, 5, 0)], p2=[(20, 5, 5), (5, 5, 5)], start=35` -> `("p1", 2)`
   - `p1=[(1, 1, 1)], p2=[(2, 2, 2)], start=100` -> `(None, 1)`
6. Extend the game to support **any number of players**. Given a dictionary mapping player names to their list of rounds, and a starting score, return the name of the winner (or `None` if there is no winner).
   - `{"Alice": [(10, 10, (5, 'D'))], "Bob": [(10, 10, 10)], "Carol": [(1,1,1)]}, start=30` -> `"Alice"`
   - `{"Alice": [(1,1,1)], "Bob": [(2,2,2)]}, start=100` -> `None`
