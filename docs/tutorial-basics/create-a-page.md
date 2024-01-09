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

To convert the hashes into Hex format we'll also import the `hex` crate:

`hex = "0.4.3"`

## `Blake2` Hashing Functions

In Blake2, we implement `64bit`, `128bit` and `512bit` hashes as follows:

```rust
//This program is to show hashing in polkadot using blake2 and twox
//You can do either 64bit, 128bit, 512bit hashing

use hex::ToHex;
use sp_core::{*, hashing::{blake2_64, blake2_512}};

//Blake2 64bit hashing
pub fn hash_blake2_64(data: &[u8]) -> [u8; 8] {
    blake2_64(data)

}

//Blake2 128bit hashing
pub fn hash_blake2_128(data: &[u8]) -> [u8; 16] {
    blake2_128(data)
}

//Blake2 512bit hashing
pub fn hash_blake2_512(data: &[u8]) -> [u8; 64] {
    blake2_512(data)
}

#[cfg(test)]

mod tests {
    use super::*;
    #[test]
    fn hash_blake2_64_test() {
        let data = b"My name is Cyndie";
        let hash = hex::encode(hash_blake2_64(data));
        let expected = "c380973ddeea7bcb";
        assert_eq!(&hash, &expected);

    }

    #[test]
    fn hash_blake2_128_test() {
        let data = b"My name is Cyndie";
        let hash = hex::encode(hash_blake2_128(data));
        let expected = "ce383c85bf9d17f2366c63f430d77b40";
        assert_eq!(&hash, &expected);
    }

    #[test]
    fn hash_blake2_512_test() {
        let data = b"My name is Cyndie";
        let hash = hex::encode(hash_blake2_512(data));
        let expected = "c4d5f619e0eb5e91f1c3403c8b21c31d000e27fc4256f3f3fa9d28fee57263e3a49a44d731537f3522f96f73ee3ff7319fddcc749612aac7bb8ca77049ec1d30";
        assert_eq!(&hash, &expected);
    }
}
```

   




