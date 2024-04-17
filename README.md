# Cryptography
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













