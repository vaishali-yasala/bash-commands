# bash-commands

### SSH 
Running the SSH command on its own returns a list of SSH command parameters and options. 

#### INPUT 
Command : ssh
#### OUTPUT
![Alt text](/ssh/ssh.png)

### SSH userid 
In this case, user id and password provides a connection to a remote host using the input example command below. <br> The most basic way to invoke the program is to use ssh command along with the remote server host name or IP address. Then it asks for username and password.

#### INPUT
Command: ssh UserName@IPAddress

#### OUTPUT
After connecting to remote server, testing to see the contents it. 

![Alt text](/ssh/ssh_userID_password.png)

### SSH USING THE KEY FILE 
Using ssh key pair file to connect to the remote host from local host

#### INPUT
1. Initially checking for the key files in the local machine. 
<br> command: ls -ltr *.pem (Because the key pair here is a pem file) <br> 
2. And then making the key publicly not viewable for the SSH to work. <br> Command: chmod 400 key_pair_file <br>
3. To connect with key_pair. <br> Command: ssh -i "key_pair_file" remote_host_userID@server.example.org (Specify the key with the -i option)

#### OUTPUT
![Alt text](/ssh/ssh_key.png)

### SSH password-less 
Initially, creating a key using ssh-keygen. Secondly, using ssh-copy-id to get copy public key of the key file for the first time and then connect password less after that. <br> 

ssh-keygen is a program to create a new authentication key pair for SSH, which can be used to automate logins, to implement SSO and to authenticate hosts. <br> Command: ssh-keygen -t ed25519 -C "your_email@example.com" <br> 

ssh-copy-id is a program used to copy, install and configure an SSH key on a server to automate passwordless logins and SSO. <br> Command: ssh-copy-id -i ~/.ssh/example_key.pub example_user@IPaddress (Specify the public key to be transferred with the -i option. Replace the example with your username and the server's IP address.)

 ![Alt text](/ssh/ssh_password_less.png)

#### SCP
SCP (secure copy) is a command-line utility that allows you to securely copy files and directories between two locations. <br>
Command: scp [OPTION] [user@]SRC_HOST:]file1 [user@]DEST_HOST:]file2 <br>
1. OPTION - scp options such as cipher, ssh configuration, ssh port, limit, recursive copy …etc. <br>
2. [user@]SRC_HOST:]file1 - Source file. <br>
3. [user@]DEST_HOST:]file2 - Destination file. <br>

#### INPUT
Copying a file from local host to a remote server and naming what the file should be called. Here, in this case, it is called scp_eg.txt on local host and scp_example.txt on the remote server.  <br> Command: scp /Users/vaishaliyasala/Desktop/scp_eg.txt root@207.246.104.234:/root/scp_example.txt 

#### OUTPUT
The first image is to show ssh passwordless login to the remote server. And also, to show the file has been copied to the remote server with the ls command before and after the transfer. <br> Second one is to show the result of input command given above.

#### Image 1:
![Alt text](scp/scp_login.png)

#### Image 2:
![Alt text](scp/scp_local_to_remote.png)

