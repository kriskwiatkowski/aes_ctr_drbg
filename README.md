# AES-CTR-DRBG

DRBG implementation based on AES-256.

Usage:

```
use aes_ctr_drbg::DrbgCtx;

fn main() {


	// personalization string must be min. 48 bytes long
	let p = vec![48, 0];

	// get entropy from somewhere, f.e. /dev/random
	let entropy: [u8; 48] = [0x04; 48]; // don't use that!

	let mut drbg = DrbgCtx::new();
	drbg.init(&entropy, p);

	// get 10 bytes
	let mut out = Vec::new();
	out.resize(10, 0);
	drbg.get_random(&mut out);

    println!("{:?}", out);
}
```

