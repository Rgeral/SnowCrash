# SnowCrash Level 09

## Introduction
Welcome to SnowCrash Level 09! In this level, we encounter the executable file `level09` and a mysterious token. Let's unravel the mystery together.

## Initial Observation
Upon executing `level09` with the token, we received the following output: `'tpmhr'`. Quickly discerning a pattern, we realized that the program was performing a simple Caesar cipher with a shift of +1 on each letter.

## Deciphering the Token
Understanding the encryption mechanism, we swiftly devised a Python script to reverse the effect of the program:
```
def decrypt_token(hex_chars):
    result = []
    for i, hex_char in enumerate(hex_chars):
        decimal_value = int(hex_char, 16)
        decrypted_value = decimal_value - i
        result.append(chr(decrypted_value))
    return ''.join(result)

hex_chars = ['66', '34', '6b', '6d', '6d', '36', '70', '7c', '3d', '82', '7f', '70', '82', '6e', '83', '82', '44', '42', '83', '44', '75', '7b', '7f', '8c', '89']
decrypted_result = decrypt_token(hex_chars)
print(decrypted_result)
```
The decrypted token obtained from `cat token` was: `f4kmm6p|=�p�n��DB�Du{��`.

## Success
We substituted the decrypted token into the program and received: `f3iji1ju5yuevaus41q1afiuq`. Success! We obtained the flag for Level 09.

## Obtaining the Token
After logging in as `flag09` and executing `getflag`, we obtained our token:
```
flag09@SnowCrash:~$ getflag 
Check flag. Here is your token: s5cAJpM8ev6XHw998pRWG728z
```
Congratulations! You have successfully conquered Level 09. Keep up the great work!

