Install Gitlab-ce
-----------------

Prerequisites

Ubuntu 22.04.2 LTS
Postfix - :doc:`install-postfix`


#Update packages that are already installed

.. code-block:: bash 

    sudo apt update
    sudo apt upgrade -y

#Reboot

.. code-block:: bash

    sudo reboot

#Install Dependencies

.. code-block:: bash

    sudo apt install tzdata curl ca-certificates openssh-server

#Import GPG key (Import the GPG key so we can use third-party software)

.. code-block:: bash 

    gpg_key_url="https://packages.gitlab.com/gitlab/gitlab-ce/gpgkey"
    curl -fsSL $gpg_key_url| sudo gpg --dearmor -o /etc/apt/trusted.gpg.d/gitlab.gpg

#Add the repository

.. code-block:: bash

    sudo tee /etc/apt/sources.list.d/gitlab_gitlab-ce.list<<EOF
    deb https://packages.gitlab.com/gitlab/gitlab-ce/ubuntu/ focal main
    deb-src https://packages.gitlab.com/gitlab/gitlab-ce/ubuntu/ focal main
    EOF

#Update again

.. code-block:: bash

    sudo apt update

#Install gitlab-ce

.. code-block:: bash

    sudo apt install gitlab-ce

#Configure firewall

.. code-block:: bash

    sudo systemctl enable ufw
    systemctl start ufw
    sudo ufw allow https
    sudo ufw allow http
    sudo ufw allow ssh
    sudo ufw reload

