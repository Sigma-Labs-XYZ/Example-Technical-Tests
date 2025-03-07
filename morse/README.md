# Morse Code

[Morse Code](https://en.wikipedia.org/wiki/Morse_code) is a way of encoding data using sequences of dots and dashes.

For this challenge, use the following Morse code specification.

```py
'A':'.-', 'B':'-...', 'C':'-.-.', 'D':'-..', 'E':'.',
'F':'..-.', 'G':'--.', 'H':'....', 'I':'..', 'J':'.---',
'K':'-.-', 'L':'.-..', 'M':'--', 'N':'-.', 'O':'---',
'P':'.--.', 'Q':'--.-', 'R':'.-.', 'S':'...', 'T':'-',
'U':'..-', 'V':'...-', 'W':'.--', 'X':'-..-', 'Y':'-.--',
'Z':'--..', '1':'.----', '2':'..---', '3':'...--',
'4':'....-', '5':'.....', '6':'-....', '7':'--...',
'8':'---..', '9':'----.', '0':'-----'
```

## ⚠️ Note

There is **far** too much work here to be done in the time you've been given. You are **not** expected to complete the whole challenge. 

## Tasks

Work through the following tasks **in order**. 

Each task should be completed **before** moving on to the next:

1. Given a string of dots and dashes, translate it into the appropriate letter/digit. Invalid sequences should raise an error.
    - `.` --> `E`
    - `-..` --> `D`
    - `--...` --> `7`
2. Given a space-separated string of dots and dashes, translate it into the appropriate sequence. Any untranslateable characters should be replaced with `?`.
    - `-... . .` --> `BEE`
    - `--- .--. .- .-..` --> `OPAL`
    - `...-- .---- --...` --> `317`
    - `.-- --- .-.. .-.-.-- . ...` --> `WOL?ES`
3. Given a slash-separated string of sequences, translate it into the appropriate full message.
    - `.. / .- -- / -. --- - / .- ..-. .-. .- .. -.. / --- ..-. / .-- --- .-.. ...- . ...` --> `I AM NOT AFRAID OF WOLVES`
    - `-- ..- ... .. -.-. / .. ... / .- / -.- .. -. -.. .-.. -.-- / -... .-. . ...- . -` --> `MUSIC IS A KINDLY BREVET`
4. Given a message written in English, produce a slash-separated Morse code string. All non-alphanumeric characters should be ignored, and the message should be treated as case-insensitive.
5. Morse code uses `STOP` to represent the end of a sentence. When decoding messages, the word `STOP` should be displayed as `.`. When encoding messages, any full stops should be rendered as the Morse code version of the word `STOP`.
6. Create a CLI tool that translates between Morse code and English. Users should not have to specify what form their input is in.
7. Adapt the CLI tool so that it accepts optional encoding arguments, so that symbols other than `.`, `-`, and `/` can be used to encode the message as Morse code.
