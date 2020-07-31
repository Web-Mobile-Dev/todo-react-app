# scenarios.txt

## Introduction

This document describes a scenario of making changes to the product and consists of the following parts:

1. Making local changes and running them on dev environment
2. Deploying changes to the staging environment
3. Deploying changes to the production environment

## Entry criteria

1. Successfully completed readme.txt 

## Running dev environment locally

### Making changes in local repository

1. Open terminal in the forked project folder on your local machine.
    1. cd ~/<git_root_folder>/todo-app-create-react-app/
2. Make sure that the repo is currently on *development* branch
    1. Note: you can use **git status** command for it.
3. Open file ToDoProject/src/App.js in IDE or any text editor
4. Add comma at the end of the line 16.

    ![1.png](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F83cc6184-f052-4a7e-b4d9-a4fc51c47e72%2FUntitled.png)

5. Create a new line after line 16.

    ![2.png](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F2de1dbd3-fecd-4cf9-b82a-2d232a69b6f0%2FUntitled.png)

     6. Add the following content to just created line :

    ```jsx
    { id: 4, name: 'Check DevOps Final Projects', isComplete: false }
    ```

    *Note:*  as a result, 'todos' array should look like this: 

    ![3.png](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F596e3c0e-b9f9-4fff-89af-c609f987d9e1%2FUntitled.png)

    7. Save changes.

### Running the app on dev environment

1. Open terminal in ToDoProject folder 

    Note: cd ~/<git_root_folder>/todo-app-create-react-app/ToDoProject

2. Build the project after changes

    ```bash
    npm run build
    ```

3. Go to the folder *env-dev* 

Note: 

cd ../env-dev/

1. Run the command to mount vagrant

    ```bash
    vagrant up
    ```

2. When the previous command is successfully finished run the following command to get the **id** of the virtual machine that has been just mounted in the folder **'env-dev'**:

    ```bash
    vagrant global-status
    ```

3. Copy the build folder into the vagrant development environment

    ```bash
    vagrant scp ../ToDoProject/build [env-dev-id]:/home/vagrant
    ```

    Note: **env-dev-id** is an id of the env-dev virtual machine

4. When the previous command is finished, run the following command to access **env-dev** virtual environment through ssh

    ```bash
    vagrant ssh
    ```

5. Run the application:

    ```bash
    serve -s build
    ```

    Note: you should see the next green box in your terminal

    ![4.png](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fa3b0f387-f49a-4294-a699-40bffa4d92f9%2FUntitled.png?table=block&id=52addf01-d7a0-475d-8e10-f7dcbe3ed1cb&width=1470&cache=v2)

6. Open a browser on your machine and locate to the address - http://192.168.33.10:5000

*Note:* The web-application should be up and running on the address. You should also see a task that was added in the previous steps.

![5.png](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F76c3ef81-a80e-4432-a5e6-6ea3d280c7ec%2FUntitled.png?table=block&id=24fb3d2e-9619-4855-8461-73f0c6dee4ef&width=860&cache=v2)

## Deploying to staging environment

**Warning:** you should complete the steps described in the previous section

*Note:* obtain your GitLab account name before executing the steps

1. Commit and Push your changes to the remote development branch
2. Create a merge request from *development* to *staging* in the forked repository using GitLab
3. When the pipeline is finished successfully click "Merge" button
4. After the merge is completed you can check staging environment by following the link http://***<your-gitlab-account-name>***.gitlab.io/todo-app-create-react-app/staging

## Deploying to production environment

**Warning:** you should complete the steps described in the previous section

*Note:* obtain AWS bucket name from readme.txt before executing the steps

1. Create a merge request from *staging* to *master* in the forked repository using GitLab 
2. When the pipeline is finished successfully click "Merge" button
3. http://***<your-gitlab-account-name>***.gitlab.io/todo-app-create-react-app/master