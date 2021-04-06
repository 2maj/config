#Config your server


##All the following handling make as root
	- ###Create new user
		- connect to your server as root
		- Create new user with cmd useradd. add :
		        - option (s) for the shell console
		        - option (d) (m) to create home directory for the new user
		        - option (G) join new user to specific group like sudo or other
		        > sudo useradd -s /bin/bash -d /home/your-user/ -m -G sudo your-group
		- Create password for the new user. Run the next code and tape password:
		> sudo passwd your-user
		- Add your to root group :
		> sudo usermod -a -G root your-user

	- ###Access extern by ssh
		- To connect to your server with the new user by password less your can make the following handling.
		        - Create ssh folder :
		        > sudo mkdir /home/your-user/.ssh/
		        - Give right access :
		        > sudo chmod 0700 /home/your-user/.ssh/
		        - Add your public ssh key on your server :
		        > sudo -- sh -c "echo 'your public ssh key' > /home/your-user/.ssh/authorized_keys"
		        - Change the owner of .ssh folder by your-user and his group:
		        > sudo chown -R your-user:your-group /home/your-user/.ssh/

##Connect to the server thanks to your new user
- Change the ower of /var/www/html by your user
- Add your ssh key in your github account
> ssh-keygen -t rsa -b 4096 -C "your mail@mail.com"
	- Start your ssh agent in background:
		> eval "$(ssh-agent -s)"
	- Add priavte ssh key to the agent:
		> ssh-add ~/.ssh/id_rsa
##Switch php version
> sudo update-alternatives --config php
> sudo service apache2 restart
