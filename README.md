# ubuntu_22_installers
#This repository storages the code to installers

#First, update your existing list of packages:
sudo apt update

#Next, install a few prerequisite packages which let apt use packages over HTTPS:
sudo apt install apt-transport-https ca-certificates curl software-properties-common

#Then add the GPG key for the official Docker repository to your system:
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

#Add the Docker repository to APT sources:
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"

#This will also update our package database with the Docker packages from the newly added repo.
#Make sure you are about to install from the Docker repo instead of the default Ubuntu repo:
apt-cache policy docker-ce

#You’ll see output like this, although the version number for Docker may be different.

#Notice that docker-ce is not installed, but the candidate for installation is from the
# Docker repository for Ubuntu 20.04 (focal). Finally, install Docker:
sudo apt install docker-ce

#Docker should now be installed, the daemon started, and the process enabled to start on boot. Check that it’s running:
sudo systemctl status docker

#Now the systemctl command shows the service is active.

#If you want to avoid typing sudo whenever you run the docker command, add your username to the docker group:
sudo usermod -aG docker ${USER}

#To apply the new group membership, log out of the server and back in, or type the following:
su - ${USER}

#If you need to add a user to the docker group that you’re not logged in as, declare that username explicitly using:
sudo usermod -aG docker username
