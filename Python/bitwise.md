## Bitwise operators
Sure! Bitwise operators in Python are used to perform operations on individual 
bits of integers. There are six bitwise operators in Python:  

1. AND (&): Takes two numbers as operands and performs a bitwise AND operation. 
It sets each bit to 1 if both bits are 1, otherwise, it sets the bit to 0.  

3. OR (|): Takes two numbers as operands and performs a bitwise OR operation. It 
sets each bit to 1 if at least one of the corresponding bits is 1.  

5. XOR (^): Takes two numbers as operands and performs a bitwise XOR (exclusive 
OR) operation. It sets each bit to 1 if only one of the corresponding bits is 1.  

7. NOT (~): Takes one number as an operand and performs a bitwise NOT operation. 
It inverts all the bits of the number, i.e., changes 1s to 0s and 0s to 1s.  

9. Left Shift (<<): Takes two numbers, the first one is the number to be 
1shifted, and the second one is the number of positions to shift the bits to the
left. It shifts all bits to the left by a specified number of positions, adding 
zeroes from the right.  

11. Right Shift (>>): Takes two numbers, the first one is the number to be
shifted, and the second one is the number of positions to shift the bits to the 
right. It shifts all bits to the right by a specified number of positions, 
discarding bits shifted beyond the rightmost position.

Examples:
```
# Bitwise AND
result_and = 5 & 3  # 0101 & 0011 = 0001
print(result_and)  # Output: 1

# Bitwise OR
result_or = 5 | 3   # 0101 | 0011 = 0111
print(result_or)   # Output: 7

# Bitwise XOR
result_xor = 5 ^ 3  # 0101 ^ 0011 = 0110
print(result_xor)  # Output: 6

# Bitwise NOT
result_not = ~5     # ~0101 = 1010
print(result_not)   # Output: -6

# Left Shift
result_left_shift = 5 << 1  # 0101 << 1 = 1010
print(result_left_shift)    # Output: 10

# Right Shift
result_right_shift = 5 >> 1  # 0101 >> 1 = 0010
print(result_right_shift)     # Output: 2
```
