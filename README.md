# How to share a folder with MacOS in a Docker Container

* Would you like to edit your files (source code/projects) that are inside Docker Containers, but, using MacOS?
* Would you like to share your Dock Container files with your MacOS?
* Would you like to access your Docker Container files without SFTP?
* Would you like to access your files without concerning in how to speed up file access in Docker?
* Would you like to edit your files without worrying about the sync on every time that a file is changed?

If you fit in some of those questions, this doc may help you.


## Step 1 - Sharing folder using Samba
The first thing that you need to do is let the folder that contains the files (project, source codes, settings, etc) 
that you want to share, visible for MacOS.

To do that, you'll need to share the folder on Docker Container using Samba. I won't describe how to do this here because 
there are a lot of resources on Internet.


## Step 2 - Redirecting the Samba ports on Kitematic
Kitematic is a platform that helps you to configure the container and other settings on Docker. It can be downloaded here: https://www.docker.com/products/docker-toolbox.
You DON'T need Kitematic to create the rules to redirect the Samba ports, however, you won't spend 2 minutes for that (instead trying to discover how to do that in the CLI).

Having Kitematic installed on MacOSS:
* Start Kitematic;
* Select the container (panel on left with the title **Container**) that contains the folder that you shared using Samba;

![Image of Panel on Docker](http://i.imgur.com/UmJBqzb.png)

* Click on the Settings tab and then the select the tab below called Hostname/Ports

![Image of Settings panel on Docker](http://i.imgur.com/lWmWiUz.png)

* Now, we add the ports 137, 138, 139 and 445 and redirects it to the same port on **localhost**.


## Step 3 - Mounting the Samba shared folder on MacOS
The last thing that is needed to edit your files on MacOS,is just map on MacOS the folder that is shared on Samba (inside the Docker container). To map that, open the **terminal** and run the following command:

```$ mount_smbfs //guest@localhost:/SharedFolderOnSamba source/```

What we're doing is using the method ```mount_smbfs```, telling that we'll connect to the ```@localhost``` in the folder ```SharedFolderOnSamba``` using the user ```guest``` and then, we'll map (create a new Drive) in the ```source/``` folder on the currenct directory of you terminal session on MacOS.

So, pay attention: 
* You can use any other user to use instead guest;
* You must have a source/ folder or define another folder that will be used;
* The SharedFolderOnSamba must be change to the name of the folder that you've shared using Samba. To confirm the name of the folder, go to /etc/samba/ and open smb.conf and search by the folder that you've shared.

