# Diffie-Hellman-Project

Diffie-Hellman shared-secret derivation in Python, computing the agreed key from public values with hand-written modular exponentiation.

## What this demonstrates

Diffie-Hellman lets two parties agree on a shared secret over a public channel without ever sending the secret itself. This works the derivation end to end: given the prime `p`, generator `g`, one party's private exponent `a`, and the other party's public value `g^b mod p`, it computes the shared key `(g^b)^a mod p`. The prime is a 512-bit value, so the exponentiation runs on Python big integers.

## Concepts demonstrated

- The Diffie-Hellman key exchange: public `p` and `g`, private exponents, shared secret `g^(ab) mod p`
- Modular exponentiation by square-and-multiply (`modPower`) as the operation that keeps the private exponent hidden
- Deriving the shared secret from one side's private exponent and the other side's public value
- Miller-Rabin primality testing and prime generation (`getRandomPrime.py`) for producing the group prime

## What's implemented

- `main.py` computes the shared key `(g^b)^a mod p` from the project's constants. The prime-generation loop is kept inline as commented reference.
- `getRandomPrime.py` generates probable primes: a trial-division sieve against small primes followed by a Miller-Rabin test (`MRTest`) with 20 witnesses.

## Stack

- Python 3 (standard library, arbitrary-precision integers)

## Usage

```
python main.py
```

Prints the derived shared secret. The public parameters and private exponent are the values assigned for the project; edit the constants in `main.py` to run different inputs.
