# Palindromes

A palindrome is a string that reads the same backwards and forwards. In this challenge, you'll identify palindromes and use an API to look up their definitions.

## ⚠️ Note

There is **far** too much work here to be done in the time you've been given. You are **not** expected to complete the whole challenge. 

## Tasks

Work through the following tasks **in order**. 

Each task should be completed **before** moving on to the next:

1. Identify if a string is a **palindrome** (reads the same backwards as forwards) or not. For example, "aha" is a palindrome but "camel" is not.
   - Reversing the string is not permitted in any form. This includes using `reverse()`, using slicing, writing a function that manually reverses it, or any other way of reversing a string).
3. When determining if a string is a palindrome, strings should be treated as case-insensitive and all punctuation other than spaces should be ignored. For example, "racecar", "cror;c" and "Yay!" are palindromes, but "race car" and "sprout?" are not.
4. Given a list of words, return only the ones that are palindromes. For example, an input of `["oh", "hah", "yep", "mm"]` would return `["hah", "mm"]`.
5. Using the [Dictionary API](https://dictionaryapi.dev/), look up a given word and return a `dict` of information on that word. If the word is not found in the dictionary, raise a `ValueError`.
6. Given a list of strings, return only those which are both nouns and palindromes.
7. You can find a list of words in the `words.txt` file. Load this data, and answer the following questions:
   - What is the longest palindrome?
   - What is the longest palindromic noun?
   - What part of speech has the most palindromes?
   - What palindrome has the most separate meanings?
