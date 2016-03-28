Easy way to deploy Rails app to DigitalOcean instance.

Four simple steps:

- Install ansible 'brew install ansible'
- Clone this repo to your Rails project directory
- Add target hosts and modify deploy variables in 'hosts.ini' file
- Run 'ansible-playbook playbook.yml' inside ansible directory

Note:

Be advised that the root play contains tasks for setting up rails environment and creates a user for deploying an application, in order to use it you need a user with root privileges on target machine.
User play sets up rvm, rubies and deploys actual application. It doesn't require root privileges.

If you have already configured your ssh connection without password, you can skip root play and simply run:
'ansible-playbook plays/user.yml'

Important!

Do not forget to add target machine ssh key to repo you will be pull from.

Configure Environment

If you don't want to install rvm and deploy any app, you can create new user, install and configure Postgresql, MySQL, Nginx, NodeJs, Redis and common libraries such as libpq-dev, openssl etc by simply run:

- 'ansible-playbook plays/root.yml'

Deploy/Redeploy

- 'ansible-playbook plays/deploy.yml'

Restart

- 'ansible-playbook plays/restart.yml'


How it works:

Here will be process description