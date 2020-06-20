# Web based todo-app
A simple todo list application.
Features:
1. Add an item to todo list.
1. Check an item as completed in the todo list.
1. Remove item from the todo list.


## Pre-requisites

### Hardware
Laptop with at least 4 Gb memory

### Software
1. nodejs and npm of the latest version
* Instructions to install here: https://nodejs.org/en/download/
* Check installation with the command `node -v`
* Check installation with the command `npm -v`


2. VirtualBox(v 6.0, or higher)
* Instructions to install here: https://www.virtualbox.org/wiki/Downloads 


3. Vagrant (v 2.2.5, or higher) 
* Instructions to install here: https://www.vagrantup.com/downloads.html
* (only if using Windows 10 or Windows 8 Pro) Disable Hyper-V, see instructions to disable here: https://www.poweronplatforms.com/enable-disable-hyper-v-windows-10-8/
* Check installation with the command `vagrant -v`'





## Set local working environment

1- Clone this repo

2- Build the project using npm. From the terminal you must:

3.1-  Get to the directory

```
cd ~/<git_root_folder>/todo-app-create-react-app/ToDoProject
```

3.2- Run the comands consequently.

3.2.1- Install dependencies:
```
npm i

```

3.2.2- Build the project:
```
npm run build
```

Running this command should shown (almost at the end of the output):

```
The build folder is ready to be deployed.
You may serve it with a static server:

  serve -s build
```

## Development environment
1-  Get to the directory

```
cd ~/<git_root_folder>/todo-app-create-react-app/env-dev`
```

2- Install vagrant plugin to ease the copy of files into vagrant environments.

```
vagrant plugin install vagrant-scp
```
3-  Run the command

```
vagrant up
```

Running this command should shown at the end of the output:

```
 default: Done.
```

4- Run the command
```
vagrant global-status
```

5- Copy the build folder into the vagrant development environment

```
vagrant scp build/ [id_vagrant_environment]:/home/vagrant
```

6- Jump into the virtual environment (refered to also as *guest*) : 
```
 vagrant ssh
```

7- Run the application
```
 serve -s build
```

8- Open a browser, and try to access to this url

http://192.168.33.10:5000

You should see the application "React Todos" running.

## Integration environment
1-  Get to the directory

```
cd ~/<git_root_folder>/todo-app-create-react-app/env-integration`
```

2- Install vagrant plugin to ease the copy of files into vagrant environments.

```
vagrant plugin install vagrant-scp
```
3-  Run the command

```
vagrant up
```

Running this command should shown at the end of the output:

```
 default: Done.
```

4- Run the command
```
vagrant global-status
```

5- Copy the build folder into the vagrant integration environment

```
vagrant scp build/ [id_vagrant_environment]:/home/vagrant
```

6- Jump into the virtual environment (refered to also as *guest*) : 
```
 vagrant ssh
```

7- Run the application
```
 serve -s build
```

8- Open a browser, and try to access to this url

http://192.168.33.10:5000

You should see the application "React Todos" running.