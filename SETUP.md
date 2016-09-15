## Passwordless SSH and Creating Keys

We're going to create a key pair that allows you to ssh into your raspberry pi without having to
use the password every time. 

Create a new keypair:
	$> ssh-keygen
	Generating public/private rsa key pair.
	Enter file in which to save the key (/Users/robrant/.ssh/id_rsa): /Users/robrant/.ssh/pikey.pem
	Enter passphrase (empty for no passphrase): 
	Enter same passphrase again: 
	Your identification has been saved in /Users/robrant/.ssh/pikey.pem.
	Your public key has been saved in /Users/robrant/.ssh/pikey.pem.pub.
	The key fingerprint is:
	SHA256:<my sha was in here>
	The key's randomart image is:
 	
Change the name of the public key to `pikey.pub` and copy into the `pi-setup/public_keys` directory.
