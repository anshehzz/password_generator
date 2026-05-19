# Password Generator 

A beginner Python project that generates secure, randomized passwords 
based on user preferences. Built as part of my journey learning 
Python and cybersecurity fundamentals.

## What it does

- Asks the user for a minimum password length
- Asks whether to include numbers and/or special characters
- Generates a random password that **guarantees** at least one number 
  and one special character if selected — not just randomly maybe

## How to run

Make sure you have Python installed, then:

```bash
python password_generator.py
```

Example interaction:
```
Enter the minimum length: 12
Do you want to have numbers (y/n)? y
Do you want to have special characters (y/n)? y
The generated password is: kR7#mXq2!Lds
```

## How it works

The script builds a pool of characters based on your choices:
- Always includes uppercase and lowercase letters
- Optionally adds digits (0–9)
- Optionally adds special characters (!@#$%^&* etc.)

It then randomly picks characters one at a time until:
1. The password meets the minimum length
2. All required character types are present

This ensures the password always satisfies the rules, 
not just by chance.

## Code

```python
def generate_password(min_length, numbers=True, special_characters=True):
    import string
    import random

    letters = string.ascii_letters
    digits = string.digits
    special = string.punctuation

    characters = letters
    if numbers:
        characters += digits
    if special_characters:
        characters += special

    pwd = ""
    meets_criteria = False
    has_number = False
    has_special = False

    while not meets_criteria or len(pwd) < min_length:
        new_char = random.choice(characters)
        pwd += new_char

        if new_char in digits:
            has_number = True
        elif new_char in special:
            has_special = True

        meets_criteria = True
        if numbers:
            meets_criteria = has_number
        if special_characters:
            meets_criteria = meets_criteria and has_special

    return pwd
```

## What I learned building this

- Python functions, parameters, and return values
- Working with the `string` and `random` modules
- Using `while` loops with multiple conditions
- Boolean logic for validating character requirements
- Taking and handling user input

## Possible improvements (future)
- [ ] Add a GUI using Tkinter
- [ ] Let user copy password to clipboard automatically
- [ ] Add password strength indicator
- [ ] Save generated passwords to an encrypted file

## Tech used
- Python 3
- `string` module (character sets)
- `random` module (random selection)

## Author
Anaan Shehzadha Mohammed Jazeer  
