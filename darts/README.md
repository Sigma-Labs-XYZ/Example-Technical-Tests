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
3. Given a **list of rounds** for a single player and a **starting score**, identify if the player would win.
   - `[(10, 10, 10), (0, 5, 0)], 35` -> `True`
   - `[(2, 2, 2), (2, (2, 'T'), 2)], 300` -> `False`
4. The game only ends on hitting exactly zero. If a round would take a player below zero, the player does not win
   - `[(0, 6, 1), (20, 20), (20, 20,), (1,)], 8` -> `False`
5. If a round would take a player to zero, but does not contain a bullseye, double, or triple, the player does not win
6. Given a dict of multiple players and their rounds, along with a starting score, identify which player would win first.
   - `{"red": [(0, 0, 1), (0, 0, 2), (0, 0, 3), (10, 0, 0)], "blue": [(5, 2), (1, 1), (0, 1)], "green": [(3, 3), (3, 3), (0, 1)]}, 10` -> `green`
