# EX-NO-10-Diffie-Hellman-Key-Exchange-Algorithm

## AIM:
To Implement Diffie Hellman Key Exchange Algorithm 

## Algorithm:

1. Diffie-Hellman Key Exchange is used for securely sharing a secret key between two parties over an insecure channel.

2. Initialization: Agree on a large prime number \( p \) and a primitive root \( g \) modulo \( p \) (both are public values).

3. Key Exchange Process: 
   - Each party selects a private key and calculates their public key using the formula \( g^{\text{private key}} \mod p \).
   - Each party then shares their public key with the other.

4. Secret Key Computation: 
   - Each party computes the shared secret key using the received public key and their own private key.

5. Security: The difficulty of computing discrete logarithms ensures that the shared key remains secure even if public values are intercepted.

## Program:

```
#include <stdio.h>

long long powerMod(long long base, long long exponent, long long mod)
{
    long long result = 1;

    while(exponent > 0)
    {
        result = (result * base) % mod;
        exponent--;
    }

    return result;
}

int main()
{
    long long p, g;
    long long privateA, privateB;
    long long publicA, publicB;
    long long secretA, secretB;

    printf("Enter a prime number (p): ");
    scanf("%lld", &p);

    printf("Enter a primitive root (g): ");
    scanf("%lld", &g);

    printf("Enter Alice's private key: ");
    scanf("%lld", &privateA);

    printf("Enter Bob's private key: ");
    scanf("%lld", &privateB);

    /* Calculate public keys */
    publicA = powerMod(g, privateA, p);
    publicB = powerMod(g, privateB, p);

    /* Calculate shared secret keys */
    secretA = powerMod(publicB, privateA, p);
    secretB = powerMod(publicA, privateB, p);

    printf("\nAlice's Public Key: %lld", publicA);
    printf("\nBob's Public Key: %lld", publicB);

    printf("\n\nAlice's Shared Secret Key: %lld", secretA);
    printf("\nBob's Shared Secret Key: %lld\n", secretB);

    if(secretA == secretB)
        printf("\nKey Exchange Successful!\n");
    else
        printf("\nKey Exchange Failed!\n");

    return 0;
}
```

## Output:

<img width="355" height="396" alt="Screenshot 2026-09-03 at 10 21 50 PM" src="https://github.com/user-attachments/assets/d0d8d0eb-a964-4b64-bf85-476e6a68bd42" />


## Result:
  The program is executed successfully

