### ryandeussing + makeryco accounts

Create two SSH keys, saving each to a separate file:

    $ cd ~/.ssh 
    $ ssh-keygen -t rsa -C "ryandeussing@gmail.com"
    # save it as id_rsa_personal when prompted
    $ ssh-keygen -t rsa -C "ryan@makery.co"
    # save it as id_rsa_makeryco when prompted

Copy keys to clipboard one at a time and paste into Github accounts:

    $ pbcopy < ~/.ssh/id_rsa_personal.pub

Create a config file in ~/.ssh/

    # githubRyandeussing
    Host personal
       HostName github.com
       User git
       IdentityFile ~/.ssh/id_rsa_personal

    # githubMakeryco
    Host makeryco
       HostName github.com
       User git
       IdentityFile ~/.ssh/id_rsa_makeryco
       
Clear stores identities:

    $ ssh-add -D

Add new keys:

    $ ssh-add id_rsa_personal
    $ ssh-add id_rsa_makeryco
    
Test to make sure they are stored:

    $ ssh-add -l

Test Github:

    $ ssh -T personal
    Hi githubPersonal! You've successfully authenticated, but GitHub does not provide shell access.
    $ ssh -T makeryco
    Hi githubWork! You've successfully authenticated, but GitHub does not provide shell access.

### Override global email setting for makeryco repos!

Otherwise commits will be blamed to your git global user (ryandeussing@gmail.com)

    git config user.email ryan@makery.co