**Source**
- https://nis-summer-school.enisa.europa.eu/2018/cources/IOT/nis-summer-school-damien-cauquil-BLE-workshop.pdf
- https://www.doyler.net/security-not-included/cracking-256-bit-rsa-keys
40 channels of 1 MHz width
- 3 channels for advertising: 37, 38, 39
- 37 channels to transmit data: 0 -> 36

FHSS : Frequency-hopping spread spectrum (FHSS) is a method of transmitting radio signals by rapidly changing the carrier frequency among many distinct frequencies occupying a large spectral band. The changes are controlled by a code known to both transmitter and receiver. FHSS is used to avoid interference, to prevent eavesdropping, and to enable code-division multiple access (CDMA) communications.

Hopping (FHSS) is only used on data channels (0-36)
Algo #1 (v4.x & v5) -> channel = (channel + hopIncrement) mod 37
Algo #2 (v5 only) -> based on PRNG

BT LE device may have one or multiple roles:
- Broadcaster
- Observer
- Peripheral
- Central

**Protocols**
- Low Energy Link Layer (LE LL) : implemented on the controller and manages advertisement, scanning, connection and security from a low-level, close to the hardware point of view from Bluetooth perspective
- Logical link control and adaptation protocol (L2CAP) : L2CAP is used within the Bluetooth protocol stack. It passes packets to either the Host Controller Interface (HCI) or, on a hostless system, directly to the Link Manager/ACL link.
- Low Energy Attribute Protocol (ATT) : Similar in scope to SDP but specially adapted and simplified for Low Energy Bluetooth. It allows a client to read and/or write certain attributes exposed by the server in a non-complex, low-power friendly manner.
In the protocol stack, ATT is bound to L2CAP.

**PDU Types**
- n* ADV_IND : Contains some advertising data (limited to 31 bytes) => btle.advertising_header.pdu_type == 0x0
- 1* SCAN_REQ : Sends a scan request to a specific device identified by its advertising address => btle.advertising_header.pdu_type == 0x3
- 1* SCAN_RSP : Sends back additional advertising data (limited to 31 bytes) => btle.advertising_header.pdu_type == 0x4
- 1* CONNECT_IND => btle.advertising_header.pdu_type == 0x5
- n* Empty PDU

** Interception**
nordic_ble.channel ==  37 OR nordic_ble.channel ==  38 OR nordic_ble.channel ==  39

```
-----BEGIN PUBLIC KEY-----
MGowDQYJKoZIhvcNAQEBBQADWQAwVgJBAKKPHxnmkWVC4fje7KMbWZf07zR10D0m
B9fjj4tlGkPOW+f8JGzgYJRWboekcnZfiQrLRhA3REn1lUKkRAnUqAkCEQDL/3Li
4l+RI2g0FqJvf3ff
-----END PUBLIC KEY-----

Modulus=A28F1F19E6916542E1F8DEECA31B5997F4EF3475D03D2607D7E38F8B651A43CE5BE7FC246CE06094566E87A472765F890ACB4610374449F59542A44409D4A809

git clone https://github.com/radii/msieve
edit Makefile -> OPT_FLAGS = -O3 -fomit-frame-pointer -march=athlon64-sse3 -DNDEBUG
make x86_64

e = 271159649013582993327688821275872950239
n = 8513909239276702310463241660208946735793173678202359843895330781205141862524433952199829179032817317799281688615001183017023849565598840210953921231104009

-----BEGIN RSA PRIVATE KEY-----
MIIBRwIBAAJBAKKPHxnmkWVC4fje7KMbWZf07zR10D0mB9fjj4tlGkPOW+f8JGzgYJRWboekcnZf
iQrLRhA3REn1lUKkRAnUqAkCEQDL/3Li4l+RI2g0FqJvf3ffAkBYf1ugn3b6H1bdtLy+J6LCgPH+
K1E0clPrprjPjFO1pPUkxafxs8OysMDdT5VBx7dZRSLx7cCfTVWRTKSjwYKPAiEAy/9y4uJfkSNo
NBaib393y3GZu+QkufE43A3BMLPCED8CIQDL/3Li4l+RI2g0FqJvf3fLcZm75CS58TjcDcEws8I1
twIgJXpkF+inPgZETjVKdec6UGg75ZwW3WTPEoVANux3DscCIDjx+RSYECVaraeGG2O/v8iKe6dn
1GpMVGUuaKecISArAiA0QRYkZFB5D4BnOxGkMX3ihjn7NFPQ7+Jk/abWRRq6+w==
-----END RSA PRIVATE KEY-----

e = 271159649013582993327688821275872950239
n = 8513909239276702310463241660208946735793173678202359843895330781205141862524433952199829179032817317799281688615001183017023849565598840210953921231104009
p = 92270847179792937622745249326651258492889546364106258880217519938223418249279
q = 92270847179792937622745249326651258492889546364106258880217519938223418258871
Phi = 8513909239276702310463241660208946735793173678202359843895330781205141862524249410505469593157571827300628386098015403924295637047838405171077474394595860

python3 rsatool/rsatool.py -n 8513909239276702310463241660208946735793173678202359843895330781205141862524433952199829179032817317799281688615001183017023849565598840210953921231104009 -p 92270847179792937622745249326651258492889546364106258880217519938223418249279 -q 92270847179792937622745249326651258492889546364106258880217519938223418258871 -e 271159649013582993327688821275872950239 -f PEM -o privkey.pem
Using (p, q) to initialise RSA instance

n =
a28f1f19e6916542e1f8deeca31b5997f4ef3475d03d2607d7e38f8b651a43ce5be7fc246ce06094
566e87a472765f890acb4610374449f59542a44409d4a809

e = 271159649013582993327688821275872950239 (0xcbff72e2e25f9123683416a26f7f77df)

d =
587f5ba09f76fa1f56ddb4bcbe27a2c280f1fe2b51347253eba6b8cf8c53b5a4f524c5a7f1b3c3b2
b0c0dd4f9541c7b7594522f1edc09f4d55914ca4a3c1828f

p =
cbff72e2e25f9123683416a26f7f77cb7199bbe424b9f138dc0dc130b3c2103f

q =
cbff72e2e25f9123683416a26f7f77cb7199bbe424b9f138dc0dc130b3c235b7

Saving PEM as privkey.pem
```

Payloa to decrypt:
```
$ echo 392969b018ffa093b9ab5e45ba86b4aa070e78b839abf11377e783626d7f9c4091392aef8e13ae9a22844288e2d27f63d2ebd0fb90871016fde87077d50ae53800000000000000000000000000000000000000000000000000000000000000000000000000 | xxd -r -p > data.bin
$ openssl rsautl -decrypt -inkey privkey.pem -in data.bin -out plain.txt
RSA operation error
140555776677184:error:0406506C:rsa routines:rsa_ossl_private_decrypt:data greater than mod len:../crypto/rsa/rsa_ossl.c:400:

$ echo 392969b018ffa093b9ab5e45ba86b4aa070e78b839abf11377e783626d7f9c4091392aef8e13ae9a22844288e2d27f63d2ebd0fb90871016fde87077d50ae538 | xxd -r -p > data.bin
```

CHTB{5p34k_fr13nd_4nd_3n73r}

https://github.com/ius/rsatool