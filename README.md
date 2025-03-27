# CRYPTOGRAPHY
HILL CIPHER
EX. NO: 1(C)

## NAME : KARTHICK KISHORE T
## REG NO : 212223220042
## DATE : 27-03-2025

## AIM:
 
 IMPLEMENTATION OF HILL CIPHER
 
## To write a Python program to implement the hill cipher substitution techniques.

## DESCRIPTION:

Each letter is represented by a number modulo 26. Often the simple scheme A = 0, B
= 1... Z = 25, is used, but this is not an essential feature of the cipher. To encrypt a message, each block of n letters is  multiplied by an invertible n × n matrix, against modulus 26. To
decrypt the message, each block is multiplied by the inverse of the m trix used for
 
encryption. The matrix used
 
for encryption is the cipher key, and it sho
 
ld be chosen
 
randomly from the set of invertible n × n matrices (modulo 26).


## ALGORITHM:

STEP-1: Read the plain text and key from the user. STEP-2: Split the plain text into groups of length three. STEP-3: Arrange the keyword in a 3*3 matrix.
STEP-4: Multiply the two matrices to obtain the cipher text of length three.
STEP-5: Combine all these groups to get the complete cipher text.

## PROGRAM 

```
import numpy as np

def get_key_matrix(key, size):
    key_matrix = []
    key = key.replace(" ", "").upper()
    key_values = [ord(char) - ord('A') for char in key]
    
    if len(key_values) != size * size:
        raise ValueError("Invalid key length. Key must be of size NxN.")
    
    key_matrix = np.array(key_values).reshape(size, size)
    return key_matrix

def text_to_numbers(text):
    text = text.upper().replace(" ", "")
    return [ord(char) - ord('A') for char in text]

def numbers_to_text(numbers):
    return ''.join(chr(num + ord('A')) for num in numbers)

def encrypt(plaintext, key):
    size = int(len(key) ** 0.5)
    key_matrix = get_key_matrix(key, size)
    text_numbers = text_to_numbers(plaintext)
    
    while len(text_numbers) % size != 0:
        text_numbers.append(0)  # Padding with 'A'
    
    text_matrix = np.array(text_numbers).reshape(-1, size)
    encrypted_matrix = np.dot(text_matrix, key_matrix) % 26
    
    encrypted_text = numbers_to_text(encrypted_matrix.flatten())
    return encrypted_text

def main():
    plaintext = input("Enter the plaintext: ")
    key = input("Enter the key (NxN characters): ")
    
    try:
        encrypted_text = encrypt(plaintext, key)
        print(f"Encrypted Text: {encrypted_text}")
    except ValueError as e:
        print(f"Error: {e}")

if __name__ == "__main__":
    main()
```

## OUTPUT

![crypto 3 py](https://github.com/user-attachments/assets/9c6fa72d-4c97-4aee-982d-0cfb09e03541)

## RESULT
 THE HILL CIPHER SUBSTITUTION TECHNIQUES WAS IMPLENMENTED BY WRITING A PYTHON PROGRAM
