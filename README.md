## SSH
My knowledge of SSH condensed into bite sized notes.

### What is SSH?
SSH or Secure Shell is a protocol/language for machines to communicate with each other just like FTP/HTTP(S).

### What's the difference between HTTPS and SSH?
They are both a form of encypted communication. HTTPS is used by a web browser to talk with servers and display websites. SSH needs a certain protocol to enable data exchange between two devices instead of a browser and server.

### How do you use SSH?
The format used to access a server: ***ssh {user}@{host}***

***ssh*** tells your system that you want to open a secure shell connection. 

***user*** represents the account you want to access e.g. root.

***host*** is the computer you want to access which could be something like an IP address or a domain name.

Using ssh on Linux/Mac is simple by using the format above. On windows you will need a ssh client such as PuTTY.

### Symmetric Encryption
Here we use **one secret key** for both encryption and decryption.

The problem with this is that anyone who has the key can decrypt the message which could be something important like a password. The solution for this is to use a ***key exchange algorithm***, which is a secure way to exchange keys.

This is more secure because the key is never transmitted between the client and host. The two computers share public pieces of data and manipulate it to calculate the secret key.

Without having this ***key exchange algorithm***, an outsider would not be able to get access to the key used between both parties.

### Asymmetric Encryption
For this we use **two separate keys** for encryption and decryption. Meaning that both parties will have both a private key and a public key. Together this forms a public/private key pair.

A machine has a **one-way relationship** between its public and private key, where the private key is used to decrypt information stored in the public key. Therefore you can send your public key to a friend, they can encrypt a message using your public key, and then you can decrypt it using your private key.

Keep in mind, you can only decrypt messages from your own public key by using your private key. Nobody else can decrypt the messages without your private key, so it is essential that you ***NEVER SHARE YOUR PRIVATE KEY***.

SSH uses both symmetric and asymmetric encrpytion. Since asymmetric is more time consuming, generally we use asymmetric encrptyion to share a public key, and from there we use symmetric encryption to make things faster.

### Hashing
This topic is complex, I recommend reading the resources at the end to learn more if you are interested.

Hashing is another type of cryptography used in SSH. In the case where someone manages to convince the client or host that they have access to tamper with the messages, we use hashes to verify the authentication of the messages. This is done by using ***HMAC*** (hash-based message authentication codes).

### Useful Terminal Commands (Linux/Mac)

Generate private/public key pair: `ssh-keygen -t rsa -b 4096 -C "youremail@address.com"`

Add private key identity: `ssh-add ~/.ssh/yourroute/yourprivatekey`

Copy the contents of your public key file: `pbcopy < ~/.ssh/yourroute/yourpublickey.pub`

Show hidden files: `ls -a`

List identities: `ssh-add -l`

Remove identities: `ssh-add -D`

### Additional Learning Resources
What is HMAC? [:link:](https://www.jscape.com/blog/what-is-hmac-and-how-does-it-secure-file-transfers)

Diffie Hellman Key Exchange vs RSA [:link:](https://www.encryptionconsulting.com/diffie-hellman-key-exchange-vs-rsa/)

