# Cryptography
## Encryption, Decryption & Hacking

One of the earliest encryption techniques is the Caesar Cipher, 

### Encrypting a message
for example : 
messsage : SECRET MEETING AT THE PALACE
look : 
Here's what that might look like encrypted:

The Caesar Cipher is a simple substitution cipher which replaces each original letter with a different letter in the alphabet by shifting the alphabet by a certain amount.

### Decrypting a message
the same concept but miror 

### Cracking the cipher
message : 
RZ VMZ WMDIBDIB VGG AJMXZN OJ EJDI RDOC XGZJKVOMV OJ YZAZVO OCZ ZIZHT LPZZI VO OCZ IDGZ YZGOV

That enemy does not know that Caesar always uses a shift of 3, so he must attempt to "crack" the cipher without knowing the shift.
techniques  : 
1.  frequency analysis
2. known plaintext
3. brute force.

##### Frequency analysis
 
Human languages tend to use some letters more than others. For example, "E" is the most popular letter in the English language. We can analyze the frequency of the characters in the message and identify the most likely "E" and narrow down the possible shift amounts based on that.

##### Known plaintext

Another term for the original unencrypted message is plaintext. If the enemy already knew some part of the plaintext, it will be easier for them to crack the rest of the encrypted version.
#### Brute force
There are only 25 possible shifts (not 26 — why not?). The enemy could take some time to try out each of them and find one that yielded a sensible message. They wouldn't even need to try the shifts on the entire message, just the first word or two.

#### Summary 
Encryption: scrambling the data according to a secret key (in this case, the alphabet shift).
Decryption: recovering the original data from scrambled data by using the secret key.
Code cracking: uncovering the original data without knowing the secret, by using a variety of clever techniques.

## Ceasar Cipher
in addition to the previous chapter , 
we can related The encryption can also be represented using modular arithmetic by first transforming the letters into numbers, according to the scheme, A → 0, B → 1, ..., Z → 25.[2] Encryption of a letter x by a shift n can be described mathematically as,[3]


The Caesar cipher can be easily broken even in a ciphertext-only scenario. Two situations can be considered:

an attacker knows (or guesses) that some sort of simple substitution cipher has been used, but not specifically that it is a Caesar scheme;
an attacker knows that a Caesar cipher is in use, but does not know the shift value.

note , crypto + graphy = secret writing 

Resources : 
* [Encryption, Decryption & Hacking](https://www.khanacademy.org/computing/computers-and-internet/xcae6f4a7ff015e7d:online-data-security/xcae6f4a7ff015e7d:data-encryption-techniques/a/encryption-decryption-and-code-cracking)
* [Ceasar Cipher](https://en.wikipedia.org/wiki/Caesar_cipher)
* [Cryptography Crash Course](https://www.youtube.com/watch?v=jhXCTbFnK8o)
* [Introduction to Cryptography](https://thebestvpn.com/cryptography/)
* [How Computers Generate Random Numbers](https://www.howtogeek.com/183051/htg-explains-how-computers-generate-random-numbers/)