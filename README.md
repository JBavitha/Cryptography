# Cryptography

## Caesar cipher

The Caesar cipher is one of the simplest and oldest methods of encryption. It is a type of substitution cipher where each letter in the plaintext is shifted a certain number of places down or up the alphabet. For example, with a shift of 3, 'A' would be encrypted as 'D', 'B' would become 'E', and so on.However, due to its simplicity, the Caesar cipher can be easily cracked with modern techniques and is not secure for transmitting sensitive information.

**Encryption and Decryption**
```
Alphabet = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
Key = 3
def caesar_encrypt(plain_text):
   cipher_text = ''
   for c in plain_text:
     if c == ' ': 
       cipher_text += ' '
       continue
     index = Alphabet.find(c)
     index = (index + Key) % len(Alphabet)
     cipher_text += Alphabet[index]
   return cipher_text

def caesar_decrypt(cipher_text):
   plain_text = ''
   for c in cipher_text:
     if c == ' ': 
       plain_text += ' '
       continue
     index = Alphabet.find(c)
     index = (index - Key) % len(Alphabet)
     plain_text += Alphabet[index]
   return plain_text

plain_text = input("Enter the plaintext: ")
cipher_text = caesar_encrypt(plain_text.upper())
print("cipher text:", cipher_text)
plain_text = caesar_decrypt(cipher_text.upper())
print("plain_text:",plain_text)

```

**Result**

![image](https://github.com/JBavitha/Cryptography/assets/142578450/13009d4f-68b8-41de-abee-1b1727589b12)


## vigenere Cipher(with autokey)

The Vigenère cipher is a method of encrypting alphabetic text by using a simple form of polyalphabetic substitution. A polyalphabetic cipher uses multiple substitution alphabets to encode the message. The Vigenère cipher is more secure than a Caesar cipher, which shifts all letters by a fixed number.
**Here's how it works**
- Choose a keyword. For example, "KEY".
- Repeat the key to match the length of the plaintext message. For example, if the plaintext is "HELLO", repeat "KEY" to get "KEYKEY".
- Assign numbers to the letters of the key, A=0, B=1, ..., Z=25. For "KEY", it becomes "10 4 24".
- Encrypt each letter of the plaintext using the corresponding letter of the key. Use modular arithmetic (like we did in the Caesar cipher) to wrap around the alphabet.
- To decrypt take each letter of the ciphertext and subtract the corresponding letter of the key.
The strength of the Vigenère cipher comes from the fact that the key is repeated, making it more difficult to break than a simple substitution cipher. However, it can still be broken with frequency analysis if the key is too short or if there is enough known plaintext.


**Encryption(with autokey)**

```
Alphabet = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"

def vigenere_encrypt_autokey(plain_text,key):
   cipher_text = ''
   key_index = 0
   for c in plain_text:
     if c == ' ': 
       cipher_text += ' '
       continue
     index = (Alphabet.find(c)+Alphabet.find(key[key_index]))%len(Alphabet)     
     cipher_text += Alphabet[index]
     key_index += 1 

     if key_index == len(key):
        key_index = 0

   return cipher_text
plain_text = input("Enter the plaintext: ")
key = input("Enter the key: ")
cipher_text = vigenere_encrypt_autokey(plain_text.upper(),key.upper())
print("cipher text:", cipher_text)

```

**Result**

![image](https://github.com/JBavitha/Cryptography/assets/142578450/9bcfa8a1-f72a-4783-be8d-969f7e724aa6)

## vigenere Cipher(without autokey)

The Vigenère cipher without using an autokey where the plaintext itself is used as part of the key instead of repeating the key we will append the plaintext to the key to match the length of the plaintext.

**Encryption(without autokey)**

```
Alphabet = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"

def vigenere_encrypt_noautokey(plain_text, key):
    cipher_text = ''
    key_index = 0
    for c in plain_text:
        if c == ' ':
            cipher_text += ' '
            continue
        index = (Alphabet.find(c) + Alphabet.find(key[key_index])) % len(Alphabet)
        cipher_text += Alphabet[index]
        key_index += 1
        if key_index == len(key):
            key_index = 0
        key += c 
    
    return cipher_text

plain_text = input("Enter the plaintext: ")
key = input("Enter the key: ")
cipher_text = vigenere_encrypt_noautokey(plain_text.upper(), key.upper())
print("Cipher text:", cipher_text)

```

**Result**

![image](https://github.com/JBavitha/Cryptography/assets/142578450/62f8cfc8-1b54-4211-97e2-d912238accaa)


## To find Greatest Common Divisor(GCD) of two numbers 'a' and 'b'.

```
def gcd_recursion(a, b): 
    if a % b == 0:
        return b
    return gcd_recursion(b, a % b)

def gcd_iter(a, b):
    while a % b != 0:
        a, b = b, a % b
    return b
```

**gcd_recursion**: This function uses recursion to calculate the GCD. It checks if ```b``` divides ```a``` evenly (i.e., if a % b == 0), in which case ```b``` is the GCD. If not, it recursively calls itself with ```b``` and ```a % b``` until ```b``` divides ```a``` evenly.
**gcd_iter**: This function uses a while loop to iteratively calculate the GCD. It repeatedly updates ```a``` and ```b``` with ```b``` and ```a % b``` until ```b``` divides ```a``` evenly.












