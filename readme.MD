This will work for Ubuntu, Alma Linux and everything except running the container for Rocky Linux
-Not sure for the reason but even with console access and manually installing and running podman kept getting exited 127 on running a container or any container like hello-world in rocky linx
	-also attempted to increase specs to minimum requirements didn't change anything. May have something to do with root permissions.
-works fine in the other distributions including Alma linux

1. first generate ssh key with vm
2. get ssh key and save it somewhere the this assumes the private key is named "4640_Lab" where "ansible.cfg" located and is set under group_vars/ALL
	-To Change this go to "inventory/group_vars/all" modify line "ansible_ssh_private_key_file:" replace "4640_Lab" with your key name
3. get api key and add to .profile with "export DO_API_TOKEN= <INSERT API KEY>" or create a file and run source
4. install the ansible-galaxy collection install community.digitalocean to use dynamic inventory
5. the VM are grouped by tags in digitalocean with "podman" being one of the two and the other being "ssh" to add users and remove
7. "ansible-playbook ssh_new_user_remove_root.yml -u root" to run the command to remove users on the Rocky,Alma and the ubuntu
8. "ansible-playbook install_podman.yml -u regular" will allow you to install and run a podman nginx container
