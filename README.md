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
```
#include <stdio.h>

long long gcd(long long a, long long b)
{
    while (b != 0)
    {
        long long temp = b;
        b = a % b;
        a = temp;
    }
    return a;
}

long long powerMod(long long base, long long exp, long long mod)
{
    long long result = 1;

    while (exp > 0)
    {
        result = (result * base) % mod;
        exp--;
    }

    return result;
}

int main()
{
    long long p, q, n, phi;
    long long e, d;
    long long message, encrypted, decrypted;

    printf("Enter two prime numbers: ");
    scanf("%lld %lld", &p, &q);

    n = p * q;
    phi = (p - 1) * (q - 1);

    printf("Enter public key exponent e: ");
    scanf("%lld", &e);

    while (gcd(e, phi) != 1)
    {
        printf("e is not valid. Enter another e: ");
        scanf("%lld", &e);
    }

    /* Find d such that (d * e) mod phi = 1 */
    d = 1;

    while ((d * e) % phi != 1)
    {
        d++;
    }

    printf("\nPublic Key  : (%lld, %lld)", e, n);
    printf("\nPrivate Key : (%lld, %lld)", d, n);

    printf("\n\nEnter message (number): ");
    scanf("%lld", &message);

    encrypted = powerMod(message, e, n);

    printf("Encrypted Message: %lld", encrypted);

    decrypted = powerMod(encrypted, d, n);

    printf("\nDecrypted Message: %lld\n", decrypted);

    return 0;
}
```



## Output:
<img width="1869" height="822" alt="image" src="https://github.com/user-attachments/assets/72038ad6-42f3-448d-abf2-9043ef7ee0d4" />



## Result:
 The program is executed successfully.
