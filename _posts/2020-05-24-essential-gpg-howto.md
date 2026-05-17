---
title: 'Essential Gnu Privacy Guard (GnuPG) Howto'
date: 2020-11-20
permalink: /posts/2020/11/essential-gpg-howto/
tags:
  - tools
---

- Creating a key through a full featured key generation dialog:
<pre>
gpg --full-generate-key
</pre>

-  Exporting public key for user `[UID]` in ASCII format and save it into `publickey.asc`:
<pre>
gpg --export --armor [UID] > publickey.asc
</pre>
Then, you should obtain something like [this](https://raw.githubusercontent.com/lorenzogentile404/lorenzogentile404.github.io/master/files/lorenzogentile404.asc).

- Importing public key from file `[PUBLICKEY]`:
<pre>
gpg --import [PUBLICKEY]
</pre>

- List keys stored on you machine:
<pre>
gpg --list-keys
</pre>

- Delete a secret key for user `[UID]`:
<pre>
gpg --delete-secret-key [UID]
</pre>

- Delete a public key for user `[UID]`:
<pre>
gpg --delete-key [UID]
</pre>

- Encrypt a file `[FILE]` for user `[UIDRECIPIENT]`:
<pre>
gpg --recipient [UIDRECIPIENT] --encrypt [FILE]
</pre>

- Decrypt encrypted file `[ENCRYPTEDFILE]`:
<pre>
gpg --decrypt [ENCRYPTEDFILE]
</pre>

- Encrypt and sign with signature of user `[UIDSENDER]` a file `[FILE]` for user `[UIDRECIPIENT]` in ASCII format:
<pre>
gpg --local-user [UIDSENDER] --recipient [UIDRECIPIENT] --armor --sign --encrypt [FILE]
</pre>

The signature is then checked when the obtained encrypted file `[FILE].asc` is decrypted.

In order to learn more about GnuPG, check the [full manual](https://gnupg.org/documentation/manpage.html) and this [extended Howto](https://www.dewinter.com/gnupg_howto/english/GPGMiniHowto.html).

Moreover, if you are interested in cryptography, check my [YouTube channel](https://www.youtube.com/channel/UC9KtiRxQQKEnUYBp3YQX5Ww). 
