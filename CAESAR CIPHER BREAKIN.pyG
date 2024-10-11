import string

def decrypt_caesar_cipher(ciphertext, shift):
    """
    Decrypts a Caesar cipher using the given shift.
    
    Parameters:
    ciphertext (str): The encrypted message.
    shift (int): The shift used in the Caesar cipher.
    
    Returns:
    str: The decrypted message.
    """
    decrypt_text = []
    for char in ciphertext:
        if char in string.ascii_letters:
            shifted_index = ord(char) - shift
            if char.islower():
                decrypt_text.append(chr((shifted_index - ord('a')) % 26 + ord('a')))
            else:
                decrypt_text.append(chr((shifted_index - ord('A')) % 26 + ord('A')))
        else:
            decrypt_text.append(char)
    return ''.join(decrypt_text)

def break_caesar_cipher(ciphertext):
    """
    Tries all possible shifts to break the Caesar cipher and returns all possible plaintexts.
    
    Parameters:
    ciphertext (str): The encrypted message.
    
    Returns:
    dict: A dictionary mapping shift values to their corresponding decrypted messages.
    """
    possible_decryptions = {}
    for shift in range(1, 26):  # There are 25 possible shifts for the Caesar cipher
        decrypt_text = decrypt_caesar_cipher(ciphertext, shift)
        possible_decryptions[shift] = decrypt_text
    return possible_decryptions

def encrypt_caesar_cipher(plaintext, shift):
    """
    Encrypts text using the Caesar cipher with the given shift.
    
    Parameters:
    plaintext (str): The message to be encrypted.
    shift (int): The shift to be used in the Caesar cipher.
    
    Returns:
    str: The encrypted message.
    """
    return decrypt_caesar_cipher(plaintext, -shift)

def encrypt_vigenere_cipher(plaintext, key):
    """
    Encrypts text using the Vigenère cipher with the given key.
    
    Parameters:
    plaintext (str): The message to be encrypted.
    key (str): The key to be used in the Vigenère cipher.
    
    Returns:
    str: The encrypted message.
    """
    key = key.lower()
    encrypt_text = []
    key_index = 0
    for char in plaintext:
        if char in string.ascii_letters:
            shift = ord(key[key_index % len(key)]) - ord('a')
            if char.islower():
                encrypt_text.append(chr((ord(char) + shift - ord('a')) % 26 + ord('a')))
            else:
                encrypt_text.append(chr((ord(char) + shift - ord('A')) % 26 + ord('A')))
            key_index += 1
        else:
            encrypt_text.append(char)
    return ''.join(encrypt_text)

def decrypt_vigenere_cipher(ciphertext, key):
    """
    Decrypts text using the Vigenère cipher with the given key.
    
    Parameters:
    ciphertext (str): The encrypted message.
    key (str): The key to be used in the Vigenère cipher.
    
    Returns:
    str: The decrypted message.
    """
    key = key.lower()
    decrypt_text = []
    key_index = 0
    for char in ciphertext:
        if char in string.ascii_letters:
            shift = ord(key[key_index % len(key)]) - ord('a')
            if char.islower():
                decrypt_text.append(chr((ord(char) - shift - ord('a')) % 26 + ord('a')))
            else:
                decrypt_text.append(chr((ord(char) - shift - ord('A')) % 26 + ord('A')))
            key_index += 1
        else:
            decrypt_text.append(char)
    return ''.join(decrypt_text)

# Example usage
ciphertext = "hello, welcome to cyberworld"  # Encrypted message
possible_decryptions = break_caesar_cipher(ciphertext)

# Print all possible decryptions
for shift, decrypt_text in possible_decryptions.items():
    print(f'Shift {shift}: {decrypt_text}')

plaintext = "hello, welcome to cyberworld"
caesar_encrypted = encrypt_caesar_cipher(plaintext, 3)
print(f'Caesar Encrypted: {caesar_encrypted}')

vigenere_key = "key"
vigenere_encrypted = encrypt_vigenere_cipher(plaintext, vigenere_key)
print(f'Vigenere Encrypted: {vigenere_encrypted}')

vigenere_decrypted = decrypt_vigenere_cipher(vigenere_encrypted, vigenere_key)
print(f'Vigenere Decrypted: {vigenere_decrypted}')
