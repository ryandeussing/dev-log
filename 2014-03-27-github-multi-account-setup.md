### ryandeussing + makeryco accounts

Create two SSH keys, saving each to a separate file:

    $ cd ~/.ssh 
    $ ssh-keygen -t rsa -C "ryandeussing@gmail.com"
    # save it as id_rsa_ryandeussing when prompted
    $ ssh-keygen -t rsa -C "ryan@makery.co"
    # save it as id_rsa_exceptionlab when prompted

Copy keys to clipboard one at a time and paste into Github accounts:

    $ pbcopy < ~/.ssh/id_rsa_personal.pub

Create a config file in ~/.ssh/

    # githubRyandeussing
    Host ryandeussing
       HostName github.com
       User git
       IdentityFile ~/.ssh/id_rsa_ryandeussing

    # githubExceptionLab
    Host exceptionlab
       HostName github.com
       User git
       IdentityFile ~/.ssh/id_rsa_exceptionlab
       
Clear stores identities:

    $ ssh-add -D

Add new keys:

    $ ssh-add id_rsa_ryandeussing
    $ ssh-add id_rsa_exceptionlab
    
Test to make sure they are stored:

    $ ssh-add -l

Test Github:

    $ ssh -T ryandeussing
    Hi githubRyandeussing! You've successfully authenticated, but GitHub does not provide shell access.
    $ ssh -T exceptionlab
    Hi githubExceptionLab! You've successfully authenticated, but GitHub does not provide shell access.

### Override global email setting for secondary repos!

Otherwise commits will be blamed to your git global user (ryandeussing@gmail.com)

    git config user.email ryan@exceptionlab.co