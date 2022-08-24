# bash-commands

## SSH 
Running the SSH command on its own returns a list of SSH command parameters and options. 

#### INPUT 
> Command : ssh
#### OUTPUT
![Alt text](/ssh/ssh.png)

### SSH userid 
In this case, user id and password provides a connection to a remote host using the input example command below. <br> The most basic way to invoke the program is to use ssh command along with the remote server host name or IP address. Then it asks for username and password.

#### INPUT
> Command: ssh UserName@IPAddress

#### OUTPUT
After connecting to remote server, testing to see the contents it. 

![Alt text](/ssh/ssh_userID_password.png)

### SSH USING THE KEY FILE 
Using ssh key pair file to connect to the remote host from local host

#### INPUT
1. Initially checking for the key files in the local machine. <br>
> command: ls -ltr *.pem (Because the key pair here is a pem file) <br> 
2. And then making the key publicly not viewable for the SSH to work. <br> 
> Command: chmod 400 key_pair_file <br>
3. To connect with key_pair. <br> 
> Command: ssh -i "key_pair_file" remote_host_userID@server.example.org (Specify the key with the -i option)

#### OUTPUT
![Alt text](/ssh/ssh_key.png)

### SSH password-less 
Initially, creating a key using ssh-keygen. Secondly, using ssh-copy-id to get copy public key of the key file for the first time and then connect password less after that. <br> 

ssh-keygen is a program to create a new authentication key pair for SSH, which can be used to automate logins, to implement SSO and to authenticate hosts. <br> 
> Command: ssh-keygen -t ed25519 -C "your_email@example.com" <br> 

ssh-copy-id is a program used to copy, install and configure an SSH key on a server to automate passwordless logins and SSO. <br> 
> Command: ssh-copy-id -i ~/.ssh/example_key.pub example_user@IPaddress (Specify the public key to be transferred with the -i option. Replace the example with your username and the server's IP address.)

 ![Alt text](/ssh/ssh_password_less.png)

## SCP
SCP (secure copy) is a command-line utility that allows you to securely copy files and directories between two locations. <br>
> Command: scp [OPTION] [user@]SRC_HOST:]file1 [user@]DEST_HOST:]file2 <br>
1. OPTION - scp options such as cipher, ssh configuration, ssh port, limit, recursive copy …etc. <br>
2. [user@]SRC_HOST:]file1 - Source file. <br>
3. [user@]DEST_HOST:]file2 - Destination file. <br>

### Copying a File from a Local Computer to a Remote Server

#### INPUT
Copying a file from local host to a remote server and naming what the file should be called. Here, in this case, it is called scp_eg.txt on local computer and scp_example.txt on the remote server.  <br> 
> Command: scp /Users/vaishaliyasala/Desktop/scp_eg.txt root@207.246.104.234:/root/scp_example.txt 

#### OUTPUT
#### Image 1:
The first image is to show ssh passwordless login from the local computer to the remote server. And also, to show the file existence on the remote server with the ls command before and after the transfer.

![Alt text](scp/scp_login.png)

#### Image 2:
 Second one is to show the result of input command given above.

![Alt text](scp/scp_local_to_remote.png)

### Copying a File from a Remote Server to a Local Computer
Connecting to the remote server and then creating a file "a-file.txt" with text "Hello World" in it. Then, copying this file from remote server to the local computer. 

#### INPUT 
> Command: scp root@207.246.104.234:/root/a-file.txt ~/Desktop/a-file.txt  

#### OUTPUT
#### Image 1:
This image shows the login to the remote machine, creating a file on there and checking if it worked.

![Alt text](/scp/scp_login_and_file.png)

#### Image 2:
This image shows the command to copy the file created earlier on the remote server to the local computer.

![Alt text](/scp/sch_remote_to_local.png)

## CP
cp stands for copy. This command is used to copy files or group of files or directory. It creates an exact image of a file on a disk with different file name. cp command require at least two filenames in its arguments.<br>
> Options: <br>
1. -i - i stands for interactive copying.
2. -b - creates the **backup** of the destination file in the same folder with the different name and different format.
3. -f - f stands for force and it can be used when the user doesn't have writing permission for this file. Then by using -f option with cp command, destination file is deleted first and then copying of content is done from source to destination file.
4. -r - to copy an entire directory **recursively**. Example of this option is shown in image 3 below.
5. -p - To **preserve** the time of the last data modification and the time of the last access, the ownership (only if it has permissions to do this), and the file permission-bits of each source file in the corresponding destination file.
Note: Preservation of characteristics is only possible if you are the root user of the system, otherwise characteristics changes.

#### INPUT
> Command: <br>
cp [OPTION] Source Destination <br>
cp [OPTION] Source Directory <br>
cp [OPTION] Source-1 Source-2 Source-3 Source-n Directory <br>

First and second syntax is used to copy Source file to Destination file or Directory. Third syntax is used to copy multiple Sources(files) to Directory.

#### OUTPUT
#### Image 1:
The image below shows copying a file in the same folder with a slightly different name.

![Alt text](/cp/cp_file.png)

#### Image 2:
The image below shows copying a file to a directory with the same name.

![Alt Text](/cp/cp_file_to_directory.png)

#### Image 3: 
The image below shows copying a directory from one to another. 

![Alt text](/cp/cp_directory.png)

## MV
mv stands for move. It can be used to move one or more files from one place to another in a file system like UNIX. <br>
> Options: -i, -f, -b options are same as for cp command. 
1. -n - with **no-clobber** option, mv prevents existing files to be overwritten.
2. -v - this shows the **version** of mv running on the system.

#### INPUT

> Command: mv [OPTION] source destination

#### OUTPUT
The image below shows moving "a-file-copy.txt" file Desktop directory to Commands_files directory.

![Alt Text](/cp/mv_file_to_directory.png)




