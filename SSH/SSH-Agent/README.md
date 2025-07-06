ssh-agent

ssh-agent is a program that runs in the background and holds your private SSH keys in memory (after you unlock them with their passphrases)
so you dont have to enter the passphrase each time.

The agent also isolates your private key your SSH client asks it to sign data without ever seeing the actual private key.
it stays in the agents private memory.



