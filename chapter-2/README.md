# Chapter 2: Hash functions


## generate hash by openssl on terminal

1. first way
```bash

 > openssl dgst -sha256 Cargo.toml

SHA256(Cargo.toml)= e3e2bd35c7048d83966aa641f7cdc9307f149f7d917ac70cc885b2f30d4eeee0

```

2. second way
```bash

 > echo -n "Cargo.toml" | openssl dgst -sha256
 
 e3e2bd35c7048d83966aa641f7cdc9307f149f7d917ac70cc885b2f30d4eeee0

```

## Three specific security properties

- pre-image resistance
  - no one should be able to reserve the hash function in order to recover the input given an output.
- second pre-image resistance
  - given an input x, no one should be able to find a second input x' such that x != x' and H(x) = H(x')
  - Example:
    - Suppose you have a document and its hash value. You don't want someone to be able to create a new document with the same hash value but different content.
- collision resistance
  - no one should be able to produce two different inputs that hash to the same output.
  - Example:
    - When creating digital certificates, you don't want two different people to be able to generate certificates with the same hash value.
- main difference between second pre-image resistance and collision resistance
  - Given Input vs Any Input: Second Pre-image Resistance is against a given input x1, whereas Collision Resistance is in the absence of any given input.
  - Security Strength: Collision Resistance is generally considered to be a stronger security property because it must hold for all possible pairs of inputs, not just a given one.

## exercise

- Can you tell if a hash function provides hiding and binding if used as a commitment scheme?
  - Hiding
    - In a commitment scheme, hiding means that once you commit to a value, others cannot deduce what this value is from your commitment. This is usually achieved through a hash function due to its one-way nature.
  - Binding
    - Binding means that once you make a commitment, you cannot change it. This is also achieved through a hash function because it is deterministic: the same input always produces the same output.
  - How to judge?
    - If the hash function is cryptographically secure and has good pre-image resistance and second pre-image resistance, then it usually can provide good hiding.
    - If the hash function has collision resistance, then it usually can provide good binding.

## curve

- 4 * a ^3 + 27 * b ^2 != 0
  - This is called the discriminant of the curve.
  - It is used to ensure that the curve is non-singular, which means that it does not have any self-intersections.
  - If the discriminant is zero, then the curve is singular and is not suitable for cryptographic use.