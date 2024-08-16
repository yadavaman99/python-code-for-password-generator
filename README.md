# python-code-for-password-generator
import random
import string
def generate_password(length):
    letters = string.ascii_letters
    digits = string.digits
    special_characters = string.punctuation
    all_characters = letters + digits + special_characters
    if length < 4:
        print("Password length must be at least 4 to include all character types.")
        return None
    password = [
        random.choice(letters),
        random.choice(digits),
        random.choice(special_characters)
    ]
    password += random.choices(all_characters, k=length - len(password))
    random.shuffle(password)
    return ''.join(password)
while True:
    try:
        password_length = int(input("Enter the desired length of the password: "))
        if password_length < 1:
            print("Password length must be at least 1.")
        else:
            break
    except ValueError:
        print("Invalid input. Please enter a positive integer.")
password = generate_password(password_length)
if password:
    print("Generated password:", password)
