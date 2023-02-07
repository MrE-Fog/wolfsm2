
# wolfSSL SM Algorithms

This repository contains the impementations of the Chinese Nation Standard's
cryptographic algorithms known as ShangMi (SM).

Support includes:
* SM3 - Hash Function
* SM4 - Cipher
* SM2 - ECDH key agreement and a signature scheme using the specified 256-bit elliptic curve.

The code must be installed into wolfSSL in order to be used.

Note that the test and build configuration code is already in wolfSSL.

## Get wolfSSL from GitHub

wolfSSL is needed to build and test the SM algorithm implemetnations.
Checkout the wolfSSL repository from GitHub beside wolfsm:

```
cd .. # To directory containing wolfsm
git clone https://github.com/wolfssl/wolfssl.git
```

## Install SM code into wolfSSL

To install the SM code into wolfSSL, use the install script:

```
cd wolfsm
./install.sh
```

## Build wolfSSL

Now you can build SM algorithms into wolfSSL.

Choose which algorithms you require on the configure line:
* --enable-sm3
* --enable-sm4-ecb
* --enable-sm4-cbc
* --enable-sm4-ctr
* --enable-sm4-gcm
* --enable-sm4-ccm
* --enable-sm2

For example, to include SM3, SM4-GCM and SM2:

```
cd ../wolfssl
./autogen.sh
./configure --enable-sm3 --enable-sm4-gcm --enable-sm2
make
sudo make install
```

# Development

## Regenerating assembly code

### Get scripts repository

The scripts to generate the assembly code have a dependency on the scripts
repository.
Checkout the scripts repository from GitHub beside wolfsm:

```
cd .. # To directory containing wolfsm
git clone https://github.com/wolfssl/scripts.git
```

### Regenerate

Now regenerate the assembly code using the gen-asm.sh script:

```
cd wolfsm
./gen-asm.sh
```

## Checking against install

You can check whether the code is different from what is already installed:

```
./check.sh
```

A list of files that would be copied and there difference will be shown.
There are no difference if the line is:

```
    SAME
```

## Reinstall

If the wolfsm files are more up to date then those in wolfSSL, install all the files with:

```
./install.sh
```

## Modifying SM implementations in wolfSSL

You may have modified installed wolfsm files in place in wolfSSL.

You will have to manually copy back each file you have modified.

See "Checking against install" as to which files need to be copied.

## Need Help?

Please reach out to support@wolfssl.com for technical support. If you're
interested in commercial licensing, FIPS operating environment additions,
consulting services, or other business engagements, please reach out to
facts@wolfssl.com.

