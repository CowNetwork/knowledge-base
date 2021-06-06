Setup SOPS
===========

1. First install the following programs:
* https://github.com/mozilla/sops
* https://github.com/FiloSottile/age

2. Retrieve the age public and secret key from out Bitwarden.

3. paste the secret key in a file somewhere on your disk `~/sops/age-keys.txt`. **Note:** One line per key.

4. Add 
* `SOPS_AGE_KEY_FILE=~/sops/age-keys.txt`
* `SOPS_AGE_RECIPIENTS=<public-key>`

to your `.bashrc` file.

You should now be able to use SOPS do encrypt and decrypt files.

###### tags: `how-to` `ops`