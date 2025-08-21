# ansible-homework
# Ansible WordPress Deployment

This project automates the installation and configuration of **WordPress** on AWS EC2 instances using Ansible.  
It supports both **Debian/Ubuntu** and **Red Hat / Amazon Linux** families.

---
<details>
<summary>📂 Project Structure</summary>
.
├── README.md                   # Project documentation and usage instructions
├── ansible.cfg                 # Ansible configuration file
├── apache/                     # Role for installing and configuring Apache
│   ├── defaults/
│   │   └── main.yml            # Default variables for Apache role
│   └── tasks/
│       └── main.yml            # Tasks for Apache installation and setup
├── database/                   # Role for installing and configuring database (MySQL/MariaDB)
│   ├── defaults/
│   │   └── main.yml            # Default variables for Database role
│   └── tasks/
│       └── main.yml            # Tasks for Database installation and setup
├── group_vars/                 # Group variables for different operating systems
│   ├── redhat.yml              # Variables for RedHat/Amazon Linux hosts
│   └── ubuntu.yml              # Variables for Ubuntu/Debian hosts
├── main.yml                    # Main playbook that includes all roles
├── php/                        # Role for installing and configuring PHP
│   ├── defaults/
│   │   └── main.yml            # Default variables for PHP role
│   └── tasks/
│       └── main.yml            # Tasks for PHP installation and setup
├── web.aws_ec2.yml             # Dynamic AWS EC2 inventory configuration
└── wordpress/                  # Role for installing and configuring WordPress
    ├── tasks/
    │   └── main.yml            # Tasks for WordPress installation and setup
    └── templates/
        └── wp-config.php.j2    # WordPress configuration template (Jinja2)


Test connection:
ansible all -i web.aws_ec2.yml -m ping

To deploy WordPress:
ansible-playbook -i web.aws_ec2.yml main.yml

After playbook execution:
	1.	Visit http://<EC2-Public-IP> in your browser.
	2.	WordPress setup page should appear.
	3.	Complete installation via web interface.
