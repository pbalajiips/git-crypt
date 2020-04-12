# git-crypt

This Tool used to encrypt/decrypt your sensitive data in git repo. 

Using gpg keypair you can encrypt or decrypt your files.


### What is GPG(GNU privacy Guard):  
Implementation of OpenPGP (Open Pretty Good Privacy). It is an encryption technique  and gpg can used to create set of KeyPair(Private/Public)

## Install

==> Download gpg from ["https://gpgtools.org/"](https://gpgtools.org/) and install on your mac.

==> Install git-crypt on mac 

```
brew install git-crypt
```

#### Create new gpg keypair

```
gpg --gen-key
```

#### To list Keys
 ```
gpg --list-keys 
```
Note the Hexacode.

#### To Trust the key
```
gpg --edit-key <keyID>

> fpr

> trust

>save

```
#### Initialise  git repo

```
git-crypt init

EX:
➜  git-crypt git:(master) git-crypt init
Generating key...
➜  git-crypt git:(master)
```

#### Create .gitattributes file with filters list 
```
➜  git-crypt git:(master) cat .gitattributes
mykey filter=git-crypt diff=git-crypt
*.key filter=git-crypt diff=git-crypt
*.secret filter=git-crypt diff=git-crypt
secret/* filter=git-crypt diff=git-crypt
➜  git-crypt git:(master)

```
Note: update this file before creating secret files

#### Add user keys to the repo
```
git-crypt add-gpg-user 41C6BC30BA8D8FD7161A1251A51BC853D4C99D53

```

#### Create files that needs to be encrypted
```
echo test >  my.key
```

#### Verify status 
```
git-crypt status
```

#### Commit and push the code then 

#### Lock & Unlock

To decrypt the file use
```
git-crypt unlock 
```  
to encrypt all
```
git-crypt lock
```

NOTE: it is overall idea. to get more info please refer gpg and git-crypt repo.

To add another user you can add his pub key to the ring and trust it later run git-crypt  add-gpg-user to allow the user to decrypt using his private key.


