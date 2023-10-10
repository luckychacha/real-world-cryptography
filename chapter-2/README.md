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