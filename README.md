# sha3 C implementation

[FIPS 202 sha3](http://csrc.nist.gov/groups/ST/hash/sha-3/fips202_standard_2015.html) implementation

## Usage

```c
#include "sha3.h"

int main(void) {
  sha3_ctx ctx;

  /* call this first */
  SHA3_RESULT res = FIPS202_SHA3_Init(&ctx, 512)
  if (res != SHA3_OK) {
    /* handle err */
  }

  /* call this N times */
  /* inSz is # of bytes */
  const char *in = "cat";

  SHA3_RESULT res2 = FIPS202_SHA3_Update(&ctx, in, strlen(in))
  if (res2 != SHA3_OK) {
    /* handle err */
  }

  /* call this last */
  const size_t outSz = FIPS202_SHA3_HashSize(&ctx)
  void *out = malloc(outSz);
  if (!out) { /* handle err */ }
  SHA3_RESULT res3 = FIPS202_SHA3_Final(&ctx, out, outSz); 
  if (res3 != SHA3_OK) {
    /* handle err */
  }

  /* out contains the digest, in binary form */
  free(out);
}
```


## Copyright
Copyright (c) 2016 Barry Allard

## Issues
[Issue tracker](https://github.com/steakknife/sha3/issues)

## License
MIT 

## See also
- Go [sha3sum](https://github.com/steakknife/sha3sum)
- Node [node-sha3](https://github.com/steakknife/node-sha3)
- Ruby [digest-sha3-ruby](https://github.com/steakknife/digest-sha3-ruby)
