## Quantum Resistant Digital Signature Program


This program generates a unique [quantum resistant](https://en.wikipedia.org/wiki/Post-quantum_cryptography) signature for given file.

It's implemented on [Lamport Scheme](https://en.wikipedia.org/wiki/Lamport_signature) which was invented by [Leslie Lamport](https://en.wikipedia.org/wiki/Leslie_Lamport).
Also it uses [OpenSSL](https://openssl-library.org/)

Lamport Scheme might seem useless since it throws the private key, but it is useful since it throws the private key.
You are trying to solve the reputation problem via [ledger](https://en.wikipedia.org/wiki/Distributed_ledger).
Lamport Scheme naturally kills it. Imagine it in the blockchain.
Anyway.

[Click Here](https://youtu.be/YVVr91kPQzQ)


#### USAGE:

When you want to sign a file, you do `sign ~/example/dir/file.ext`.
It will generate 2 files.
`file.ext.sg.bin` and `file.ext.pk.bin`.

Then you send these 2 files with the message (the signed file).
Receiver verifies it with `verify file.ext file.ext.sg.bin file.ext.pk.bin`.

It uses all bytes of the message. So even metadata changes are being detected as corruption.

Example I/O:

`$ sign test.c`<br>
`> Signature and Public Key files have been created`

`$ verify test.c test.c.sg.bin test.c.pk.bin`<br>
`> The signature is verified`

`$ echo -n " " >> test.c`<br>
`$ verify test.c test.c.sg.bin test.c.pk.bin`<br>
`> WARNING. File has been corrupted at byte 4`
