# Rod Cutting Problem - Dynamic Programming

## Problem Statement

You are given a rod of length `n` and a list of prices where `price[i]` denotes the price of a rod of length `i + 1`. Your task is to determine the **maximum total value** you can obtain by cutting the rod into pieces (or leaving it whole).

You may cut the rod in any number of pieces, and each piece's price is determined by its length from the given list.

---

## Input

- `price[]`: An array where `price[i]` is the price of a rod of length `i + 1`
- `n`: Total length of the rod

---

## Output

- The maximum total revenue obtainable by cutting up the rod and selling the pieces.

---

## Example

**Input:**
```cpp
price = {1, 5, 8, 9, 10, 17, 17, 20}
n = 8
