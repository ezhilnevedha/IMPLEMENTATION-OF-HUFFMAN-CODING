# EXP 11 : IMPLEMENTATION OF HUFFMAN CODING
## Aim
To implement Huffman coding to compress the data using Python.

## Software Required
1. Anaconda - Python 3.7

## Algorithm:
### Step1: Count frequency
Read the input string and count how many times each character appears.
<br>


### Step2: Sort characters by frequency
Arrange the characters in increasing order of their frequency.
<br>

### Step3: Build Huffman Tree
Pick the two characters with the lowest frequency, join them into a binary tree node, and replace them with their combined frequency. Repeat this until only one tree remains.
<br>

### Step4: Assign binary codes
Traverse the Huffman tree. Assign:

 - 0 for every left branch

 - 1 for every right branch
   
The generated path becomes the Huffman code for each character.
<br>

### Step5: Generate compressed output
Replace characters in the input string with their Huffman codes to produce the compressed binary output.
<br>

 
## Program:

``` Python
# Developed by
# Ezhil Nevedha K
# 212223230055
# Step 1: Get the input string
input_string = "EZHIL NEVEDHA"  # Example input string
# Step 2: Calculate frequency of each character in the input string
frequency = {}
for char in input_string:
    if char in frequency:
        frequency[char] += 1
    else:
        frequency[char] = 1
# Step 3: Create tree nodes
nodes = [[char, freq] for char, freq in frequency.items()]
# Step 4: Main function to implement Huffman coding
while len(nodes) > 1:
    # Sort nodes based on frequency
    nodes = sorted(nodes, key=lambda x: x[1])

    # Pick two smallest nodes
    left = nodes.pop(0)
    right = nodes.pop(0)

    # Create a new node with combined frequency
    new_node = [[left, right], left[1] + right[1]]
    nodes.append(new_node)

# The final node is the Huffman tree
huffman_tree = nodes[0]
# Step 5: Generate Huffman codes
huffman_codes = {}

def generate_codes(tree, code=""):
    if isinstance(tree[0], str):  # If it's a leaf node
        huffman_codes[tree[0]] = code
    else:  # If it's an internal node, recurse
        generate_codes(tree[0][0], code + "0")
        generate_codes(tree[0][1], code + "1")

generate_codes(huffman_tree)
# Step 6: Print the characters and their Huffman codes
print("Character | EZHIL NEVEDHA")
print("-------------------------")
for char, code in huffman_codes.items():
    print(f"    {char}    |    {code}")

```
## Output:

### Print the characters and its huffmancode
<img width="197" height="215" alt="image" src="https://github.com/user-attachments/assets/1df6854d-785c-4d04-adb1-a4dbb471c502" />


<br>
<br>



## Result
Thus the huffman coding was implemented to compress the data using python programming.
