# SSH Into Remote Server Without Password

Updated: 09/07/2022
MacOS

## Check SSH key

```
$ ls -al ~/.ssh
```

ls

* -a : show all file
* -l : show file details

## Generate SSH key

```
$ cd ~/.ssh
$ ssh-keygen
```

ssh-keygen
Defaults to rsa

* RSA (Rivest–Shamir–Adleman)is one of the first public-key cryptosystems and is widely used for secure data transmission. It's security relies on integer factorization, so a secure RNG (Random Number Generator) is never needed. Compared to DSA, RSA is faster for signature validation but slower for generation.

* DSA (Digital Signature Algorithm) is a Federal Information Processing Standard for digital signatures. It's security relies on a discrete logarithmic problem. Compared to RSA, DSA is faster for signature generation but slower for validation. Security can be broken if bad number generators are used.

* ECDSA (Elliptical curve Digital Signature Algorithm) is an Elliptic Curve implementation of DSA (Digital Signature Algorithm). Elliptic curve cryptography is able to provide the relatively the same level of security level as RSA with a smaller key. It also shares the disadvantage of DSA of being sensitive to bad RNGs.

* EdDSA (Edwards-curve Digital Signature Algorithm) is a digital signature scheme using a variant of Schnorr signature based on Twisted Edwards curves. Signature creation is deterministic in EdDSA and its security is based on the intractability of certain discrete logarithm problems, so it's safer than DSA & ECDSA which requires high quality randomness for each and every signature.

* Ed25519, is the EdDSA signature scheme, but using SHA-512/256 and Curve25519; it's a secure elliptical curve that offers better security than DSA, ECDSA, & EdDSA, plus has better performance (not humanly noticeable).

## Upload the public key to the remote server

```
ssh-copy-id -i ~/.ssh/id_rsa.pub remote-user@remote-host
```
