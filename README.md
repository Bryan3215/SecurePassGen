# SecurePassGen
This script allows users to specify the length of the password and choose whether to include uppercase letters, digits, and special characters. It then generates a strong and random password based on the provided criteria.

# password_generator.py

import random
import string

def generate_password(length=12, include_uppercase=True, include_digits=True, include_special_chars=True):
    """
    Generate a strong and random password.

    Args:
    - length (int): The length of the password. Default is 12.
    - include_uppercase (bool): Include uppercase letters. Default is True.
    - include_digits (bool): Include digits. Default is True.
    - include_special_chars (bool): Include special characters. Default is True.

    Returns:
    - str: The generated password.
    """
    # Define character sets
    lowercase_chars = string.ascii_lowercase
    uppercase_chars = string.ascii_uppercase if include_uppercase else ''
    digit_chars = string.digits if include_digits else ''
    special_chars = string.punctuation if include_special_chars else ''

    # Combine character sets
    all_chars = lowercase_chars + uppercase_chars + digit_chars + special_chars

    # Check if at least one character set is included
    if not all_chars:
        raise ValueError("At least one character set (uppercase, digits, or special characters) must be included.")

    # Generate password
    password = ''.join(random.choice(all_chars) for _ in range(length))

    return password

if __name__ == "__main__":
    # Input: Password length and options
    length = int(input("Enter the desired password length: "))
    include_uppercase = input("Include uppercase letters? (y/n): ").lower() == 'y'
    include_digits = input("Include digits? (y/n): ").lower() == 'y'
    include_special_chars = input("Include special characters? (y/n): ").lower() == 'y'

    try:
        # Generate password
        password = generate_password(length, include_uppercase, include_digits, include_special_chars)

        # Display the generated password
        print("\nGenerated Password:")
        print(password)

    except ValueError as e:
        print(f"Error: {e}")
