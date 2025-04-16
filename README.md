# caesar_cipher.py

def encrypt(text, shift):
    result = ""
    for char in text:
        if char.isalpha():
            base = ord('A') if char.isupper() else ord('a')
            result += chr((ord(char) - base + shift) % 26 + base)
        else:
            result += char
    return result

def decrypt(text, shift):
    return encrypt(text, -shift)

def main():
    print("=== Caesar Cipher Encryption ===")
    choice = input("Do you want to (E)ncrypt or (D)ecrypt? ").strip().lower()
    
    if choice not in ['e', 'd']:
        print("Invalid choice. Please select E or D.")
        return

    text = input("Enter the text: ")
    try:
        shift = int(input("Enter the shift value (integer): "))
    except ValueError:
        print("Shift must be an integer.")
        return

    if choice == 'e':
        encrypted = encrypt(text, shift)
        print(f"Encrypted Text: {encrypted}")
    else:
        decrypted = decrypt(text, shift)
        print(f"Decrypted Text: {decrypted}")

if __name__ == "__main__":
    main()
