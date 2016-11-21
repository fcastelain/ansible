You need to put on the server some configuration:

Install ssh:
    apt-get install openssh-server

Accepte the root login with ssh key:
    -> vi /etc/ssh/sshd_config
        the line should be:
            PermitRootLogin yes
    -> restart ssh:
        service ssh restart

Now put your ssh key on the server:
    Before:
        -> Create the .ssh directory:
            mkdir ~/.ssh
        -> generate your ssh key on your own computer
            ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
        -> add the ssh key on your own ssh agent
            ssh-agent bash
            ssh-add ~/.ssh/id_rsa

    ToDO:
        -> Copy your public ssh key on the server
            ~/.ssh/id_rsa.pub | ssh user@ip_machine "cat - >> ~/.ssh/authorized_keys"
