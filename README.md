
# VagrantChefExample

Application developed by [Agilion Apps](http://agilionapps.com/)

## Development Setup

Development of the application was done using [Vagrant](http://www.vagrantup.com/).
Follow these steps to get a Vagrant virtual machine up and running.

1. Install Vagrant and VirtualBox. See instructions at [vagrantup.com](http://docs.vagrantup.com/v1/docs/getting-started/index.html)
2. Install Berkshelf for managing chef cookbooks: `gem install berkshelf`
3. Install vagrant berkshelf plugin: `vagrant plugin install vagrant-berkshelf`
4. Setup the VM: `vagrant up`
5. SSH into VM: `vagrant ssh`

From your host you can now use:

* `vagrant suspend` and `vagrant resume` to quickly pause and re-open your VM.
* `vagrant halt` to shutdown your VM, `vagrant up` to re-boot it.
* `vagrant destroy` to shutdown and delete your VM and free up disk space, `vagrant up` to re-create.
* `vagrant reload` to restart and re-provision your VM.

## Development Commands

All development commands such as installing gems and running database
migrations must be done from within the Virtual Machine:

1. SSH into VM: `vagrant ssh`
2. Change into working directory: `cd /vagrant`
3. Startup Rails server: `rails s`
4. Startup Rails console: `rails c`

## Running Automated Tests

The application has a number of unit tests (RSpec)  that should be run after making changes to the application
and before deploying.

1. SSH into VM: `vagrant ssh`
2. Change into working directory: `cd /vagrant`
2. Setup test database: `rake db:test:prepare`
4. Run unit tests: `rspec`


