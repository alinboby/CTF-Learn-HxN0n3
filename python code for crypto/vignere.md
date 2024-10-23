### Vigenère decryption with key and cipher:

    def vigenere_decrypt(ciphertext, key):
        alphabet = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
        decrypted_text = []
        key_length = len(key)
        for i, letter in enumerate(ciphertext):
            letter_pos = alphabet.index(letter)
            key_pos = alphabet.index(key[i % key_length])
            decrypted_pos = (letter_pos - key_pos) % 26
            decrypted_letter = alphabet[decrypted_pos]
            decrypted_text.append(decrypted_letter)
        return ''.join(decrypted_text)
    
    ciphertext = "UFJKXQZQUNB"
    key = "SOLVECRYPTO"
    decrypted_message = vigenere_decrypt(ciphertext, key)
    flag = f"QUESTCON{{{decrypted_message}}}"
    print("Decoded Flag:", flag)


Change ciphertext, key and flag-format (if need add) to decode vigenere cipher
