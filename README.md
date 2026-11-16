# Crypto Outlooks - proofs

Every trade call published on [Crypto Outlooks](https://cryptooutlooks.com) is hashed the moment it opens. Once a day the
hashes of that day form one Merkle root, and the day file is anchored in the Bitcoin blockchain with
[OpenTimestamps](https://opentimestamps.org). This repository is a public copy, so a call can be checked without our site.

- `proofs/<day>.txt` - one line per call: `<sha256 of the call> <call id>`, in opening order, then `root <merkle root>`.
- `proofs/<day>.txt.ots` - the OpenTimestamps proof of that file.

Check a day:

```
pip install opentimestamps-client
ots verify proofs/2026-11-13.txt.ots
```

The call id is printed on every trade page together with its hash; the hash must appear in the day file.
