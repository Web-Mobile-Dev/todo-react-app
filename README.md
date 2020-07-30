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
- Complete Amazon Web Services Tutorial

## Amazon account registration

1. If you are not registered at amazon AWS, please, register at [https://console.aws.amazon.com/s3/home](https://console.aws.amazon.com/s3/home) as a root user
    1. Select Account type as Personal
    2. Enter your real data in the form
    3. It is important to enter the payment Information to get access to a free server. 

        Note: When you submit your payment information, Amazon will charge $1 USD/EUR to your credit card as a verification charge to ensure your card is valid. The amount may show as pending in your credit card statement for 3-5 days until the verification is completed, at which time the charge will be removed. You may be redirected to your bank website to authorize the verification charge.

    4. Select a Basic Support Plan which is free
    5. Sign in to the Console by clicking "**Sign In to the Console**" button in the top right corner

# Getting source files

1. Fork the project from the repository into your personal GitLab ([https://gitlab.com/laskau/todo-app-create-react-app](https://gitlab.com/laskau/todo-app-create-react-app))

# Configure GitLab repository

## Rules

1. In the left-bar of GitLab, navigate to Settings → Repository <br/>
![1.png](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fd3e91611-b117-453a-bf83-4237c33e1e01%2FUntitled.png)

2. Expand **Default Branch** tab, and make sure that Default Branch is **development** <br/>
![2.png](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F8172f830-f722-4d34-a38a-1a92c7922b3f%2FUntitled.png)

3. Expand Protected Branches section and protect the **development** branch (click "Protect" to confirm): <br/>
![3.png](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F314077d2-846a-4a11-9c7c-d7c9a8da8fc6%2FUntitled.png)

4. Protect the **staging** and **master** branches with the following settings: <br/>
![4.png](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F82326c53-9993-4c76-a057-ef986897a25c%2FUntitled.png)

5. The completed pushing policy should look like this: <br/>
![5.png](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fccdccaf0-8422-4948-a92b-3a0181249a0c%2FUntitled.png?table=block&id=75c2d1c7-a833-4238-a36c-8967d39520de&width=1700&cache=v2)

6. In the left-bar of GitLab, navigate to **Settings** → **General**

7. Open **Merge requests** tab and check **Pipelines must succeed** option <br/>
![6.png](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fd60b6986-ac6a-4f53-8d9f-741e0a879b1b%2FUntitled.png?table=block&id=8908a7d4-e668-4f6c-882a-c53d41143305&width=1210&cache=v2)

### Set local development environment

1. Clone this repo
2. Build the project using npm. From the terminal you must:
3. Go to the directory

    ```
    cd ~/<git_root_folder>/todo-app-create-react-app/ToDoProject
    ```

4. Run the comands consequently.
    1. Install dependencies:

        ```
        npm i
        ```

    2. Build the project:

        ```
        npm run build
        ```

    3. Running this command should shown (almost at the end of the output):

        ```
        The build folder is ready to be deployed.
        You may serve it with a static server:

          serve -s build
        ```

### Configuring Amazon Web Service account

1. Configure a bucket as a static website using the AWS Management Console:
    1. Enable website hosting
        1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console.aws.amazon.com/s3/](https://console.aws.amazon.com/s3/)
        2. In the **Bucket name** list, click the "**Create bucket**" button.
        3. Enter the name that you would like. It will be used as a part of the domain name.
        4. (Optional) For better connection, choose the closest region for you. 
        5.  Click **Next** and then again **Next**. You should be on the step 3 "**Set permissions**".
        6. Clear **Block *all* public access**, check the warning "I acknowledge that the current settings may result in this bucket and the objects within becoming public", and click **Next**.
        7. Click "**Create bucket**" button and wait until the bucket will be created.
        8. Click on your bucket name in the buckets list. 
        9. Choose **Properties**.
        10. Choose **Static website hosting**.
        11. Choose **Use this bucket to host a website**.
        12. Enter the name of your index document. The index document name is typically index.html.
        13. Under **Static website hosting**, note the Endpoint. This link will become available over the Internet after the deploy.
        14. Choose **Save**.
    2. Get your access key id and secret access key for AWS:
        1. Go to your [AWS account overview](https://console.aws.amazon.com/)
        2. Click on account menu in the upper-right (has **your name** on it)
        3. Select **My Security Credentials**
        4. On the page **Your security credentials** select tab **Access keys**
        5. Click **Create New Access Key**
        6. Click **Show Access Key**
        7. Write down somewhere both keys, you'll need them later

### Configuring deployment to staging and production environments

*Note:* this instruction is also a scenario that shows the rules for commits and merging in action. 

1. Go to the settings of CI/CD of the forked GitLab repository (*GitLab Setting → CI/CD*)
2. Find the ***Variables*** section and click the button ***Expand*** 
3. Click ***Add Variable*** and provide:
    1. the key AWS_ACCESS_KEY_ID  with the value from Amazon Web Services Tutorial;
    2. the key AWS_SECRET_ACCESS_KEY with the value from Amazon Web Services tutorial. 
4. Create a branch with the name "update-aws" from *development* branch and perform the following actions to update AWS configuration:
    1. click *.gitlab-ci.yml* 
    2. press *Edit*
    3. update the line *47* by replacing the string "todo-app-create-react-app" with **bucket name**  provided by the AWS;
    4. provide commit message if possible 
    5. press Commit changes 
    6. create Merge request from "update-aws" to "development" and submit it
    7. Wait until the pipeline completes and admit the request when the pipeline is finished 
5. Before merging your changes into master create a merge request from *development* to *stages.* 
6. Wait until the pipeline completes and admit the request when the pipeline is finished: 
    1. This step performs a deployment to staging environment that can be accessed by the link when the pipeline is completed successfully"https://***<your-gitlab-account-name>***.gitlab.io/todo-app-create-react-app"
    2. Confirm that the web-app is up and running
7. Finally, we can proceed with the production deployment to the bucket created in Amazon Web Services Tutorial:
    1. Create a merge request from *staging* to *master*
    2. Wait until the pipeline completes and admit the request when the pipeline is finished http://<**aws-bucket-name**>.s3*-website.eu-central-1.amazonaws.com/*
8. Confirm that the web-app is up and running - this would mean that the instruction was completed successfully

### Exit criteria

The instruction is considered successful when the following conditions hold: 

- The staging environment is up and running on the link - *https://**<your-gitlab-account-name>**.gitlab.io/todo-app-create-react-app*
- The production environment is up and running on the link - *http://<**aws-bucket-name**>.s3-website.eu-central-1.amazonaws.com/*