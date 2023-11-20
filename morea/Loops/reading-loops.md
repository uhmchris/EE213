---
title: "Loops"
published: true
morea_id: reading-loops
morea_summary: "loops"
morea_type: reading
morea_labels:
---

While loops:
A while loop in Python is a control structure that repeatedly executes a block of code as long as a specified condition remains True. The loop continues to run until the condition becomes False. while loops are used when the number of iterations is not known beforehand or when you need to continuously perform an action until a certain condition is met.

```python
# Using a while loop to count and display numbers
count = 1
while count <= 5:
    print(count)
    count += 1
```

In this example, the while loop counts and displays numbers from 1 to 5. While loops are useful for scenarios where you need to repeatedly execute a block of code while a condition remains True, and they provide flexibility for creating dynamic and interactive programs.

For loops:
A for loop in Python is a control structure used to iterate over a sequence of elements, such as lists, tuples, strings, or ranges. It executes a block of code for each element in the sequence, allowing you to process data, perform calculations, or automate tasks efficiently.

```python
# Using a for loop to iterate over a list
fruits = ['apple', 'banana', 'cherry']
for fruit in fruits:
    print(fruit)

# Using a for loop with the range() function
for i in range(5):
    print(i)

# Using a for loop to iterate over characters in a string
word = 'Python'
for char in word:
    print(char)
```

In this example, the for loop is used to iterate over different types of sequences, such as lists, and strings. It allows you to process each element in the sequence one by one, making it a versatile tool for various programming tasks. The range() function is commonly used to generate a sequence of numbers for iteration. 

Nested loops:
Nested loops in Python refer to the practice of using one loop inside another loop. This allows you to perform more complex iterations, such as iterating over multiple sequences simultaneously or creating patterns with multiple levels of repetition. Nested loops are used to solve problems that involve multidimensional data or require repeated actions within a larger context.

```python
# Using nested loops to create a multiplication table
for i in range(1, 6):
    for j in range(1, 6):
        result = i * j
        print(f'{i} * {j} = {result}')
    print()  # Add a blank line after each row

# Using nested loops to process a list of lists (matrix)
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

for row in matrix:
    for element in row:
        print(element, end=' ')
    print()  # Move to the next row
```

Nested loops can be used to create a multiplication table and process a matrix (list of lists). Nested loops provide a way to handle multidimensional data structures and perform repetitive tasks within a larger context. However, be mindful of the potential complexity and performance implications when using deeply nested loops.

#Break and continue
Break and continue are two control statements in Python that allow you to modify the behavior of loops.
The break statement is used to prematurely exit a loop, ending the loop's execution even if the loop's condition is still true.
The continue statement is used to skip the rest of the current iteration of a loop and move on to the next iteration.

```python
# Using break to exit a loop prematurely
numbers = [1, 2, 3, 4, 5]
for num in numbers:
    if num == 3:
        break
    print(num)

# Using continue to skip specific iterations
numbers = [1, 2, 3, 4, 5]
for num in numbers:
    if num == 3:
        continue
    print(num)
```

The break statement is used to exit the loop as soon as the value 3 is encountered, resulting in only 1 and 2 being printed.
The continue statement is used to skip the iteration when the value 3 is encountered, so only 1, 2, 4, and 5 are printed.
Break and continue are useful when you need to control the flow of a loop based on certain conditions or when you want to avoid processing specific elements in a loop iteration.
