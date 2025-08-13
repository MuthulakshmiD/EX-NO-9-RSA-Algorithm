# EX-NO-9-RSA-Algorithm

## AIM:
To Implement RSA Encryption Algorithm in Cryptography

## Algorithm:


Step 1: Design of RSA Algorithm  
The RSA algorithm is based on the mathematical difficulty of factoring the product of two large prime numbers. It involves generating a public and private key pair, where the public key is used for encryption, and the private key is used for decryption.

Step 2: Implementation in Python or C 
This algorithm can be implemented in languages like Python or C by performing large integer calculations for key generation, encryption, and decryption, utilizing libraries for modular arithmetic if necessary.

Step 3: Algorithm Description  
1. Key Generation:
   - Select two large prime numbers \( p \) and \( q \).
   - Calculate \( n = p \times q \), which will be used as the modulus.
   - Compute the totient \( \phi(n) = (p - 1)(q - 1) \).
   - Choose a public exponent \( e \) such that \( e \) is coprime with \( \phi(n) \).
   - Compute the private key \( d \), which is the modular inverse of \( e \) mod \( \phi(n) \).

2. Encryption:
   - Convert the plaintext message \( M \) into a numerical form \( m \) (such that \( 0 \le m < n \)).
   - Compute the ciphertext \( c \) using the formula: \( c = m^e \mod n \).

3. Decryption:
   - Use the private key \( d \) to recover \( m \) from \( c \) using: \( m = c^d \mod n \).
   - Convert \( m \) back into the original message \( M \).

Step 4: Mathematical Representation  
- Encryption: \( E(m) = m^e \mod n \)
- Decryption: \( D(c) = c^d \mod n \)

Step 5: **Security Foundation  
The security of RSA relies on the difficulty of factoring large numbers; thus, choosing sufficiently large prime numbers for \( p \) and \( q \) is crucial for security.

## Program:

Name:Muthulakshmi D
Reg:212223040122

```
#### 9 RSA
def gcd(a,b):
    while b: a,b = b, a%b
    return a

def mod_exp(b,e,m):
    r=1
    while e:
        if e&1: r=(r*b)%m
        b=(b*b)%m
        e>>=1
    return r

def mod_inv(e,phi):
    t,newt=0,1
    r,newr=phi,e
    while newr:
        q=r//newr
        t,newt=newt,t-q*newt
        r,newr=newr,r-q*newr
    return t+phi if t<0 else t if r==1 else -1

p,q=61,53
n=p*q
phi=(p-1)*(q-1)
e=17
if gcd(e,phi)!=1: exit("e and phi not coprime")

d=mod_inv(e,phi)
if d==-1: exit("No modular inverse")

print(f"Public Key: (e={e}, n={n})")
print(f"Private Key: (d={d}, n={n})")

msg=input("Message: ")
enc=[mod_exp(ord(c), e, n) for c in msg]
print("Encrypted:", *enc)

print("Decrypted:", ''.join(chr(mod_exp(c, d, n)) for c in enc))

```


## Output:

![image](https://github.com/user-attachments/assets/a39848c8-dff6-4597-b0ea-bfe248950466)


## Result:
 The program is executed successfully.
