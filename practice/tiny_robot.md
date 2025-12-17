# Tiny robot

```
  __I__
 [@ _ @]            ____
>-|___|-<          |    |
  ooooo            |____|
```

A tiny robot can carry up to **five** items without malfunctioning. Robot instructions are represented as strings, where

- `v` means 'put down one held item'
- `^` means 'pick up one item'

## Task 1

**Given a string of valid robot instructions (e.g. `^^^....v..^.v`), how many items is the robot carrying at the end of the instructions?**

Examples:

- `^^^....v..^.v` -> 2
- `.................^` -> 1
- `.^.^.^.^.^` -> 5
- `....v..v` -> 0
- `....^vvvvv^.` -> 1 
- `vvv...^` -> 1
- `^^..vv..^^..v..^` -> 2

## Task 2

**Given a list of instruction sets, find the index of the instruction set that causes the robot to carry the _heaviest load at any point_?**

Examples:

- `["^^", "^"]` -> 0
- `["^v^", "^^", "^^^^^vvvvv"]` -> 2
- `["^^^^^^", "^^^^", "vvvv^^"]` -> 1
- `["^^^^vvvvv^^", "^^^."]` -> 0

## Task 3

`.` represents a standard unit of distance for the robot.

**Given a string of instructions, what is the longest distance travelled under the maximum load for that journey?**

Examples:

- `......` -> 6
- `^...^.` -> 1
- `.....^^.v..` -> 1

## Task 4

The robot uses 1 unit of energy to transport 1 item 1 distance unit.

**Given a string of instructions, how much energy is required for the full trip?**

Examples:

- `^.` -> 1
- `^^..` -> 4
- `^..^..^..` -> 12
