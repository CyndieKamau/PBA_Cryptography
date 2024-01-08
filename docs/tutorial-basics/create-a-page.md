---
sidebar_position: 1
---

# Hash Functions


## What are Hash Functions?

- In computer Programming, a general hash function takes an input of any size and type (text, integers), and maps it to a number or code.
- It can be useful in say organizing data, example books by their title's first letters.
- **Collision** can happen, where we have different outputs with the same input. Say different books' titles having the same letters, so one code has two different sets of books.

- In cryptography, hash functions occur when text or binary data is mapped to a fixed-length **hash value**, which is **collision free** and **irreversible**, meaning one cannot access the original data using the hash value.


## Famous Hash Algorithms
- xxHash a.k.a TwoX (non-cryptographic)
- MD5
- SHA1
- RIPEMD-160
- SHA2-256 (aka SHA256) &c.
- SHA3
- Keccak
- Blake2

## Hash Functions in Polkadot
- Polkadot uses the **Blake2** and **xxHash** Hashing Algorithms:

- To import the Hashing Algorithms we will use polkadot's `sp_core` crate. 
- In your rust project, add `sp_core` as a dependency in your `Cargo.toml` file:

```toml
sp-core = { git = "https://github.com/paritytech/substrate", default-features = false, branch = "polkadot-v0.9.42", features = [
    "full_crypto",
    "std",
] }
sp-runtime = { git = "https://github.com/paritytech/substrate", default-features = false, branch = "polkadot-v0.9.42", features = [
    "std",
] }
```

   




