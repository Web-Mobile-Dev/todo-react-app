# readme.txt

# Entry criteria

- GitLab account (create here [https://gitlab.com](https://gitlab.com/))
- PC with at least 4 Gb memory
- nodejs and npm of the latest version
    - Instructions to install here: [https://nodejs.org/en/download/](https://nodejs.org/en/download/)
    - Check nodejs installation with the command `node -v`
    - Check npm installation with the command `npm -v`
- VirtualBox(v 6.0, or higher)
    - Instructions to install here: [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)
- Vagrant (v 2.2.5, or higher)
    - Instructions to install here: [https://www.vagrantup.com/downloads.html](https://www.vagrantup.com/downloads.html)
    - (only if using Windows 10 or Windows 8 Pro) Disable Hyper-V, see instructions to disable here: [https://www.poweronplatforms.com/enable-disable-hyper-v-windows-10-8/](https://www.poweronplatforms.com/enable-disable-hyper-v-windows-10-8/)
    - Check installation with the command `vagrant -v`
- Vagrant plugin vagrant-scp to ease the copy of files into vagrant environments.
    - Install vagrant plugin with the command `vagrant plugin install vagrant-scp`


# Getting source files

1. Fork the project from the repository into your personal GitLab ([https://gitlab.com/laskau/todo-app-create-react-app](https://gitlab.com/laskau/todo-app-create-react-app))

# Configure GitLab repository

## Rules

1. In the left-bar of GitLab, navigate to Settings → Repository <br/>
![1.png](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fd3e91611-b117-453a-bf83-4237c33e1e01%2FUntitled.png)

2. Expand **Default Branch** tab, and make sure that Default Branch is **development** <br/>
![2.png](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F8172f830-f722-4d34-a38a-1a92c7922b3f%2FUntitled.png)

3. Expand Protected Branches section and protect the **development** branch (click "Protect" to confirm): <br/>
![3.png](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F314077d2-846a-4a11-9c7c-d7c9a8da8fc6%2FUntitled.png?table=block&id=01fd1de1-b8cc-4cf9-9e83-f89dfe95ee51&width=1700&cache=v2)
Note: the development branch can be protected by default:
![3_1.png](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F1817c78b-a5b5-49c0-bfea-6356b22cf6b0%2FUntitled.png?table=block&id=382d1de3-50bc-4f47-bf04-9a7773b94431&width=3020&cache=v2)

4. Protect the **staging** and **master** branches with the following settings: <br/>
![4.png](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F82326c53-9993-4c76-a057-ef986897a25c%2FUntitled.png)

5. The completed pushing policy should look like this: <br/>
![5.png](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fccdccaf0-8422-4948-a92b-3a0181249a0c%2FUntitled.png?table=block&id=75c2d1c7-a833-4238-a36c-8967d39520de&width=1700&cache=v2)

6. In the left-bar of GitLab, navigate to **Settings** → **General**: <br/>
![6_1.png](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fcbb09868-0cdc-4830-bd73-860e96e88d46%2FUntitled.png?table=block&id=72a70f7b-ecec-454b-a1a8-c7c8f974b7b5&width=480&cache=v2)

7. Open **Merge requests** tab and uncheck **Enable 'Delete source branch' option by default** option in **Merge options** section: <br/>
![7_1.png](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Ff66dc687-6247-4135-add3-e665dda84026%2FUntitled.png?table=block&id=82ce7843-c284-4d49-a0ce-088d06e62eb8&width=1250&cache=v2)

8. Scroll to **Merge checks** section and check **Pipelines must succeed** option <br/>
![6.png](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fd60b6986-ac6a-4f53-8d9f-741e0a879b1b%2FUntitled.png?table=block&id=8908a7d4-e668-4f6c-882a-c53d41143305&width=1210&cache=v2)

9. Press **Save changes** button at the end of the section: <br/>
![9_1.png](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fdc2f2723-145f-47b8-84a5-09b004bdbaef%2FUntitled.png?table=block&id=a67cd52e-3acd-4c0f-956c-0461def96726&width=2690&cache=v2)


### Set local development environment

1. Clone this repo to your PC.
2. Build the project using npm. From the terminal you must:
    1. Go to the directory

    ```
    cd ~/<git_root_folder>/todo-app-create-react-app/ToDoProject
    ```

    2. Run the comands consequently.
        - Install dependencies:

            ```
            npm i
            ```

        - Build the project:

            ```
            npm run build
            ```

        - Running this command should shown (almost at the end of the output):

            ```
            The build folder is ready to be deployed.
            ```