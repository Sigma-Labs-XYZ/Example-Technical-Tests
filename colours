# Colours

In this challenge, you'll process complex strings to identify colours.

## ⚠️ Note

There is **far** too much work here to be done in the time you've been given. You are **not** expected to complete the whole challenge. 

## Tasks

Work through the following tasks **in order**. 

Each task should be completed **before** moving on to the next:

1. Create a function that accepts a string of case-insensitive space-separated words. It should return the number of colours in the rainbow (red, orange, yellow, green, blue, indigo, violet) present in the string. Empty strings should raise a ValueError
   - "red" --> 1
   - "red blue" --> 2
   - "red ghost green" --> 2
2. The function should accept an optional argument (default `False`). If this argument is `True`, the function should return the number of *unique* colours.
   - "red blue" --> 2
   - "red red" --> 1
3. Create a function that accepts a list of colour strings, and returns the unique colours of the string with the most colours (non-unique) in it. These strings should be sorted in alphabetical order. In the event of two strings with the same number of non-unique colours, the first one in the list should be used.
   - ["red", "red blue"] --> ["blue", "red"]
   - ["green x f", "violet violet violet", "red red"] --> ["violet"]
4. The colour strings now contain hex codes as well as written strings. Add any **valid** hex codes to the count for a given colour string.
5. Hex codes may appear with or without a preceding `#`, and may be 3 or 6 characters in length.
6. The function should be able to handle a string where colour words are separated by *any* non-alphanumeric character (except an octothorpe (`#`))
