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

http://imgur.com/a/ndCGo
