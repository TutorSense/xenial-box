# xenial-box

## Setting Up
* Create a directory on your local system called `Vagrant`
* Clone this box into that directory using
```
$ git clone git clone https://github.com/TutorSense/xenial-box.git
```
* Create another new directory on your local system called `Sites/xenial-sites`
* On a windows system you should now have a directory structure looking like this:
```
- C:/
--- Vagrant
------ xenial-box
--- Sites
------ xenial-sites
```
* On a unix system you should have something like this:
```
- ~
--- Vagrant
------ xenial-box
--- Sites
------ xenial-sites
```

* In the xenial box directory you should have a file called `Vagrantfile`
* Open that and look for the line that reads:
```
config.vm.synced_folder "~/Sites/xenial", "/var/www/vhosts"
```
* Replace `~/Sites/xenial/` to match whatever you have set up for your sites folder.
* Following the above instructions for windows, the entire line would be:
```
config.vm.synced_folder "C:/Sites/xenial-sites", "/var/www/vhosts"
```
* And for a unix system:
```
config.vm.synced_folder "~/Sites/xenial-sites", "/var/www/vhosts"
```

This directroy set up will mean anything you do in the `/var/www/vhosts/` directory on the Vagrant box, will be accessible from the `~/Sites/xenial-sites` directroy on your local machine, allowing you to edit things on the box directly using your editor of choice. 

### Running
* After the above setting up, navigate to the xenial-box directory and run
```
$ vagrant up
```
* to start the box, and
```
$ vagrant ssh
```
* to ssh into it. 

## New Box Versions

As boxes are updated (with additional software or whatever), Vagrant will notify
that your local box is out-of-date (when you run `vagrant up`).

You'll need to destroy your VM first before it can be updated (unfortunately). To
run the update process:

```
# Download the latest box (but don't do anything with it yet)

$ vagrant box update

# Destroy your VM

$ vagrant destroy

# Rebuild with the new box you downloaded

$ vagrant up
```
