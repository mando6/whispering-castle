Validate a password with at least 8 characters, one uppercase, one lowercase, and one number

```
^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)[A-Za-z\d]{8,}$
```

```
def validate_password(password):pattern = r'^(?=.*[a-z])(?= .*[A-Z])(?=.*\d)[A-Za-z\d]{8,}$'
return bool(re.match(pattern, password))# Example usage print(validate_password("Password1")) # True print(validate_password("pass1")) # False
```

```
Breakdown

**^**

Start of the string

**(?=.*[a-z])**

Positive lookahead for at least one lowercase letter

**(?=.*[A-Z])**

Positive lookahead for at least one uppercase letter

**(?=.*d)**

Positive lookahead for at least one digit

**[A-Za-zd]{8,}**

Match 8 or more characters that are either letters (uppercase or lowercase) or digits

**$**

End of the string
```

Find all phone numbers

```
\b\d{3}[-.\s]?\d{3}[-.\s]?\d{4}\b
```

```
Breakdown

**d{3}**

Matches exactly 3 digits

**[-.s]?**

Matches an optional separator which can be a hyphen, dot, or space

**d{3}**

Matches exactly 3 digits

**[-.s]?**

Matches an optional separator which can be a hyphen, dot, or space

**d{4}**

Matches exactly 4 digits

```

Validate an email address

```
^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$
```

```
`email = "example@example.com"``pattern = r'^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$'``if re.match(pattern, email):``print("Valid email address")``else:``print("Invalid email address")`
```

```
Breakdown

**^**

Start of the string

**[a-zA-Z0-9._%+-]+**

One or more alphanumeric characters, dots, underscores, percent signs, pluses, or hyphens (local part of the email)

**@**

At symbol separating local part and domain

**[a-zA-Z0-9.-]+**

One or more alphanumeric characters, dots, or hyphens (domain part)

**\.**

Literal dot separating domain and top-level domain

**[a-zA-Z]{2,}**

Two or more alphabetic characters (top-level domain)

**$**

End of the string
```

