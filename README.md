# bash-commands

SSH - Running the SSH command on its own returns a list of SSH command parameters and options. 

INPUT - ssh

OUTPUT -
![Alt text](/ssh/ssh.png)

SSH userid - In this case, used user id and password to connect to a remote host. The most basic way to inovoke the program to use ssh command along with the remote server ip address. Then it asks for username and password. Or to connect using the input example command below.

INPUT - eg: ssh UserName@IPAddress

OUTPUT - After connecting to remote server, testing to see the contents it.
![Alt text](/ssh/ssh_userID_password.png)

SSH USING THE KEY FILE - used ssh key pair file to connect to the remote host from local host

INPUT

Initially checking for the key files in the local machine.

command: ls -ltr *.pem (Because the key pair here is a pem file)

And then making the key publicly not viewable for the SSH to work.

Command: chmod 400 key_pair_file

To connect with key_pair. 

Command: ssh -i "key_pair_file" remote_host_userID@server.example.org (Specify the key with the -i option)

OUTPUT
![Alt text](/ssh/ssh_key.png)

SSH password less - Firstly, creating a key using ssh-keygen. Secondly, using ssh-copy-id to get copy public key of the key file for the first time and then connect password less after that.

ssh-keygen is a program to create a new authentication key pair for SSH, which can be used to automate logins, to implement SSO and to authenticate hosts. 

Command: ssh-keygen -t ed25519 -C "your_email@example.com" 

ssh-copy-id is a program used to copy, install and configure an SSH key on a server to automate passwordless logins and SSO.

Command: ssh-copy-id -i ~/.ssh/example_key.pub example_user@IPaddress (Specify the public key to be transferred with the -i option. Replace the example with your username and the server's IP address.)

 ![Alt text](/ssh/ssh_password_less.png)