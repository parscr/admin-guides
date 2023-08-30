Install Gitlab-ce
-----------------

Ubuntu 22.04.2 LTS


.. code-block:: bash 

   sudo apt update
   sudo apt upgrade -y

#Install Prereqs

.. code-block:: bash

sudo apt install tzdata curl ca-certificates openssh-server

#import GPG key

.. code-block:: bash 

gpg_key_url="https://packages.gitlab.com/gitlab/gitlab-ce/gpgkey"
curl -fsSL $gpg_key_url| sudo gpg --dearmor -o /etc/apt/trusted.gpg.d/gitlab.gpg

#add the repository

.. code-block:: bash

sudo tee /etc/apt/sources.list.d/gitlab_gitlab-ce.list<<EOF
deb https://packages.gitlab.com/gitlab/gitlab-ce/ubuntu/ focal main
deb-src https://packages.gitlab.com/gitlab/gitlab-ce/ubuntu/ focal main
EOF

# Update again

.. code-block:: bash

sudo apt update

#install gitlab-ce

.. code-block:: bash

sudo apt install gitlab-ce

#configure firewall

.. code-block:: bash

sudo systemctl enable ufw
systemctl start ufw
sudo ufw allow https
sudo ufw allow http
sudo ufw allow ssh
sudo ufw reload

