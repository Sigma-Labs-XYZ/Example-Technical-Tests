# Run-Length Encoding

[Run-Length Encoding](https://en.wikipedia.org/wiki/Run-length_encoding) (RLE) is a method for compressing data. Repeated datapoints in sequence (a "run") are instead replaced with a single instance of the datapoint and a count.

## Examples

- `aaabbc` -> `a3b2c1`
- `bbbaaabac` -> `b3a3b1a1c1`

## ⚠️ Note

There is **far** too much work here to be done in the time you've been given. You are **not** expected to complete the whole challenge. 

## Rules

- You **can** use Google to help you
- You **can** ask the Coach for guidance, but we can't solve the problem for you
- You **cannot** use AI in this assessment

## Tasks

Work through the following tasks **in order**. 

Each task should be completed **before** moving on to the next. Completing a later task should not invalidate the solution for a later one.

1. Given an RLE-encoded message, decompress it to its original form
2. Given a message, compress it using RLE
3. Compression should be possible in both short (no inclusion of `1` after short runs) and long (inclusion of `1` after short runs)
4. Given a message Calculate the percentage potential compression using RLE
5. Encoding and decoding should be able to handle run lengths between 1 and 1000
