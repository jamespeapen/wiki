# OTP generator

`oathtool` can generate time-based one-time passowords for 2-step
verification.

```bash
oathtool --totp -b -d 6 [key]
```

`-d` sets the output to a six digit number.
