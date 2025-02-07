# Split the treasure

A crew of treasure hunters have acquired a chest of valuable gems. However, they are so progressive they will only take the treasure if it can be split equally between them. Otherwise, they will just bury it again.

Each gem is represented by an integer which represents its value and the treasure chest can be represented by a list of all the values.

For example:

- `[4, 4, 4]` represents a chest of three gems, each with a value of `4`
- `[21]` represents a chest containing one gem with the value of `21`

## Tasks

1. Write a program that identifies whether a given treasure chest can be split between a given number of treasure hunters, and how to split the gems
  -  `[4,4,4]` can be split between `3` treasure hunters with each receiving one gem (`[4, 4, 4]`)
  -  `[27,7,20]` can be split between `2` (`[27, (7, 20)]`)
  -  `[3,2,7,7,14,5,3,4,9,2]` can be split between `4` (`[14, (7, 7), (5, 9), (3, 2, 3, 4, 2)]`)
2. Write a program that identifies how many different numbers of treasure hunters (maximum 5) can split a chest
  - `[6,3,2,4,1]` can be split between `1` and `2` treasure hunters (`[(6, 2), (3, 4, 1)]`)
  - `[21]` can only be taken by `1` treasure hunter
  - `[4, 4, 4, 4]` can be split by `1`, `2`, or `4` treasure hunters
