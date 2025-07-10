# **Run Ansible from Jenkins Pipeline**

## **Project Overview**
This project demonstrates how to execute ansible playbook from a jenkins pipeline.

---
  
## **Feature**

### **EKS provisioning using Terraform**

- Install jenkins on digital ocean server
- Install ansible on digital ocean server
- Execute Ansible playbook from jenklins pipeline to configure 2 EC2 instances.

### **Diagrammatic Presentation**
- Install jenkins on digital ocean server
  ![image](https://github.com/user-attachments/assets/8cc2a474-d175-4907-97bb-5b6651e1d006)

  ![image](https://github.com/user-attachments/assets/4cf0542b-1117-444e-8342-0f00381a2efa)

  ![image](https://github.com/user-attachments/assets/ad6bb142-6759-4134-9f5c-065c121c9763)

  ![image](https://github.com/user-attachments/assets/269f656a-1ce2-402f-b5c4-18b907bf7f3a)

  ![image](https://github.com/user-attachments/assets/159cf267-4d2b-4fce-96ea-5ca052f09409)

  ![image](https://github.com/user-attachments/assets/3163c959-bbf6-46a7-b67f-7b5835224b0b)

  ![image](https://github.com/user-attachments/assets/42867281-8f2c-47a7-a71e-ee353f81cbba)

  ![image](https://github.com/user-attachments/assets/5f8da30e-73b7-45e5-ae79-52da781f1703)


- Install ansible on digital ocean server
  
- Created ansible server form previous lesson
  ![image](https://github.com/user-attachments/assets/e5fda6af-14e1-4290-a223-73ffb4da7ba4)
  
- Install python dependencies
- Dependencies already installed
- Use the commnad below to confirmed
  
    ```
    python3 -c "import boto3"
    python3 -c "import botocore"
    ```
  ![image](https://github.com/user-attachments/assets/81ff8b91-2411-47ca-825d-ffdb1980fce2)

- Configure AWS credentials on the Ansible server
      1. Create .aws folder in the root directory
      2. cd into the directory
      3. create files called "credentials" into the directory.
      4. Copy the aws credentials from your user directory and paste into the server

      ```
            Pwd
            mkdir .aws
            cd .aws
            vim credentials
            type .aws/credentials
      ```
  
  
  ![image](https://github.com/user-attachments/assets/c7ffeefa-a769-47ce-a2b7-c745d6a6f724)


- Create 2 AWS EC2 instances and create key pair
  
  ![image](https://github.com/user-attachments/assets/7fadc810-b3b5-4a38-8f37-5c0cfa40c3e1)
  ![image](https://github.com/user-attachments/assets/ba24be38-e52c-4055-b101-2accbf89c776)
  ![image](https://github.com/user-attachments/assets/05b04f4e-1507-42ee-8d5f-84528d35bd8f)
  ![image](https://github.com/user-attachments/assets/4fb18b01-d3af-4262-8bbd-810cd5121191)
  ![image](https://github.com/user-attachments/assets/4ea33af8-e584-4dfc-9d82-c068772a284e)
  ![image](https://github.com/user-attachments/assets/7d5fcfd0-1189-4c10-bd10-24f07a811bb3)
  ![image](https://github.com/user-attachments/assets/2de5422d-6567-4b33-bb9a-ffe21018c686)

- Ansible Configuration Files
     - This section will create an Ansible configuration file, a dynamic inventory file, and an Ansible playbook.
       -  Open the ansible-jenkins project in Microsoft Visual Studio Code. Click the icon to create a new folder. Name the folder “ansible.”
       -  Create 3 new files inside the ansible folder: (1) ansible.cfg, (2) inventory_aws_ec2.yaml, and (3) my-playbook.yaml.

    ![image](https://github.com/user-attachments/assets/d8cff644-767e-47cb-8497-b473d1df56e3)


- Install Plugins (Jenkins Prerequisites)
      - SSH Agent
      - Credentials Binding

    ![image](https://github.com/user-attachments/assets/cbb01cb5-2c0a-458a-b259-784c16b4b81c)
    ![image](https://github.com/user-attachments/assets/2e8a355a-923b-4bc7-9d00-7e80fe290731)
    ![image](https://github.com/user-attachments/assets/7ddbd537-c9cc-456a-98a8-5521f81f3986)
    ![image](https://github.com/user-attachments/assets/18d3a308-4553-495c-858f-9c8449b5e006)
    ![image](https://github.com/user-attachments/assets/9db5632a-7554-417b-a4e3-f9ac5152ba68)
  
- Ansible Server Key Credentials
- This section will store the Ansible server key credentials inside the Jenkins credentials store
  
    ![image](https://github.com/user-attachments/assets/3b0495dc-7d93-42d4-811a-ec600557bc24)
    ![image](https://github.com/user-attachments/assets/4c80851d-5b92-4fb1-9d2a-fd9c4211b648)
    ![image](https://github.com/user-attachments/assets/98664849-2a69-4e4e-816b-e2fc53cec520)

  
- Open PowerShell and type the following command to display the local workstation’s SSH private key.
- Notice the header and footer are in the new OpenSSH format.
  
            ```  ~/.ssh/id_rsa
            ```

    ![image](https://github.com/user-attachments/assets/853c4e4e-92b1-406a-b25c-280995060aa2)

- As Jenkins only understands the classic format (e.g. header and footer with RSA PRIVATE KEY), the private SSH key will need to be converted. Enter the following command in PowerShell to convert the private SSH to the classic format

            ```
                ssh-keygen -p -f .ssh/id_rsa -m pem -P ""-N ""
            ```
-  Where:
     - f = path to the private key
     - m = the file extension
     - P = old passphrase
     - N = new passphrase
          
- When prompted for the new passphrase, leave it empty by pressing Enter. When prompted to reenter the passphrase, press Enter again. The following output will display:    


    ![image](https://github.com/user-attachments/assets/a8215ced-397d-48b6-925a-d41624d66e6a)
    ![image](https://github.com/user-attachments/assets/70b9ccfc-c977-4e00-9220-d97e63a94d2d)
    ![image](https://github.com/user-attachments/assets/35d8fbd8-57a7-4057-b8d7-d08dea7f7b55)
    ![image](https://github.com/user-attachments/assets/15a66c9d-08b9-485f-bf2a-50f7a823fe02)

- Jenkins Pipeline Creation/Execution

    ![image](https://github.com/user-attachments/assets/eec93778-4298-4283-af81-c33fc85f9bf4)
    ![image](https://github.com/user-attachments/assets/ac97f481-a60d-4e34-8d1c-ab223743ce85)
    ![image](https://github.com/user-attachments/assets/3f1e3953-a1ed-450d-b4da-8b75d7e0c815)
    ![image](https://github.com/user-attachments/assets/8fc45d8d-8b75-4ace-97d5-713fa6dd0ea3)
    ![image](https://github.com/user-attachments/assets/22c022d9-e91d-430c-9b20-542a5bd951ad)

- Is the "Pipeline: Stage View" plugin installed?
    - This plugin is usually installed by default with recent Jenkins installations, but it's worth checking.
    - Go to Manage Jenkins -> Plugins.
    - On the Installed tab, search for "Pipeline: Stage View". Ensure it's listed and enabled. If not, go to the Available tab, search for it, and install it.


    ![image](https://github.com/user-attachments/assets/ca2dc751-d3e6-47ad-8ad1-ce00e020a943)


  
   
- Pipeline Validation & Security Optimization
   - This section will validate the “copy files to ansible server” stage copied the ansible folder and private EC2 SSH key to the server. This section will also provide an optimization to the Jenkinsfile. Open PowerShell and SSH into the Ansible server. Issue an ls         command to confirm the ansible folder contents and the private EC2 SSH key exist:
    - Files on ansible host
     <img width="975" height="156" alt="image" src="https://github.com/user-attachments/assets/f288477f-09c2-4128-aa50-341b08174224" />

   - Inside the Jenkins management UI, navigate to the Dashboard. Click inside the ansible-pipeline job
   - In the left pane, click on build #8.
   - Notice the security warning below:
     <img width="975" height="424" alt="image" src="https://github.com/user-attachments/assets/9b538646-4e7c-4f14-8fac-ec3809144856" />
     <img width="975" height="72" alt="image" src="https://github.com/user-attachments/assets/4e2dffcf-02cd-474f-933e-54135c7960d0" />
     <img width="975" height="298" alt="image" src="https://github.com/user-attachments/assets/8ecaaffa-eaf7-4b93-ac37-47be4ec575e8" />
   - In Jenkinsfile, the security issue from Step 5 pertains to the syntax used with the keyFileVariable (keyfile) in the withCredentials block. The use of double quotes and curvy brackets will mistakenly let the Groovy interpreter reveal the keyfile secret in the          command line history.
   - To fix this, open Microsoft Visual Studio Code and restore the Jenkinsfile in the ansible-jenkins project. Modify the scp command in the withCredentials block by using single quotes and removing the curvy brackets as shown below:

     ```
         sh 'scp $keyfile root@104.248.55.160:/root/ssh-key.pem'
     ```


   - Open a terminal inside Microsoft Visual Studio code. Use the git command to add the changes, add a commit message, and push to the GiHub repository


    ```
        git add .
        git commit -m "Fix security warning for .pem file"
        git push
    ```



    - Return to the Jenkins management UI. On the Pipeline ansible-pipeline screen, click Build Now to rerun the Jenkins pipeline. The second build is successful
      <img width="975" height="554" alt="image" src="https://github.com/user-attachments/assets/f65ec294-3daa-4a4d-b26b-9e4383f975f2" />
      - Click on Status in the left menu and confirm the security warning is resolved.
        <img width="975" height="427" alt="image" src="https://github.com/user-attachments/assets/372083a3-d93e-4422-9af7-b935e5f42ce1" />
        <img width="975" height="606" alt="image" src="https://github.com/user-attachments/assets/c95d1119-515e-4206-aa4f-621765290871" />

  -  CI/CD Stage: Execute Ansible Playbook
      - Prior to writing the final stage of the Jenkins pipeline, the SSH Pipeline Steps Plugin must be installed in Jenkins. Once installed, the Jenkinsfile will be updated to add the “execute ansible playbook” stage. The pipeline will then be executed, validated,            and optimized
        <img width="975" height="299" alt="image" src="https://github.com/user-attachments/assets/15218c41-67cb-4956-a72c-1c7c343f1cac" />

     - Jenkinsfile
         -  Restore the ansible-jenkins project in Microsoft Visual Studio Code and open the Jenkinsfile. At the same indentation level as the “copy files to ansible server” stage, create a new individual stage block named “execute ansible playbook.”
             ```
                  stage("execute ansible playbook") {

                     }
            ```

         -  In the “execute ansible playbook” stage block, create nested steps and script blocks as shown below:
             ```
                    stage("execute ansible playbook") {
                         steps {
                              script {
                              }
                           }
                         }
             ```

         -  In the script block, display output to the user that the Ansible Playbook is being called to configure the EC2 instances:
             ```
                  echo "calling ansible playbook to configure ec2 instances"
             ```

        - Open the following webpage in a web browser: https://plugins.jenkins.io/ssh-steps/. Scroll down to the withCredentials example in the Examples section. Copy the following code to the clipboard
       
          <img width="577" height="255" alt="image" src="https://github.com/user-attachments/assets/d1dd70c1-626a-4406-a0da-917b041149ab" />

       -  The changes are summarized as follows
            ```
                def remote = [:]
                remote.name = "ansible-server"
                remote.host = "x.x.x.x"
                remote.allowAnyHosts = true
            ```

        - Enter a couple carriage returns. Still in the script block, use the withCredentials plugin again. For efficiency and to ensure there are no syntactical errors, copy the following line from the “copy files to ansible server” stage.
            ```
                   withCredentials([sshUserPrivateKey(credentialsId: 'ec2-server-key', keyFileVariable: 'keyfile', usernameVariable: 'user')]) {
 
                   }
            ```

          Change the credentialsId value to ‘ansible-server-key.’
          
       - Refer back to the official Jenkins documentation on using the SSH Pipeline Steps plugin (https://plugins.jenkins.io/ssh-steps/). Notice the user and identityFile keys in the Remote section of Configuration
          

          <img width="522" height="635" alt="image" src="https://github.com/user-attachments/assets/c916341a-aedf-42d4-8f04-552884ffdc0a" />

       - Once again, scroll to the withCredentials example in the Examples section. Copy the circled keys and associated values to the clipboard.
           <img width="624" height="329" alt="image" src="https://github.com/user-attachments/assets/ac5aa5ba-6df1-4293-8791-40205e77f5eb" />

           
      - Inside the withCredentials block, paste the user and identityFile keys from the clipboard. Make the following adjustments:- Change the user key’s value to user to match the usernameVariable in the withCredentials statement- Change the identityFile key’s value          to keyfile to match the keyFileVariable in the withCredentials statement.
        These changes are summarized as follows:

          ```
                 remote.user = user
                 remote.identityFile = keyfile
          ````

      - Inside the withCredentials block and under the identityFile key, add the following line to run the ls -l command
          ```
                 sshCommand remote: remote, command: "ls -l"
          ```
        Note: The ls -l command is for testing purposes and will be changed later.
 
        <img width="975" height="269" alt="image" src="https://github.com/user-attachments/assets/14e5efd7-b599-4c3f-9c53-1b6bc20e2962" />

    
      - Open a terminal in Microsoft Visual Studio code. Use the git command to add the changes, specify a commit message, and push to the GitHub repository.


          ```
                   git add .
                   git commit -m "Add remote execution"
                   git push
          ```

  - Jenkins Pipeline Execution
      - This section reruns the Jenkins pipeline with the addition of the "execute ansible playbook" stage.
      - Return to the Jenkins management UI and rerun the ansible-pipeline job. Confirm the build is successful:

        <img width="975" height="507" alt="image" src="https://github.com/user-attachments/assets/a68290fb-3bd5-418f-875f-2a8e935dde83" />
      - Restore the Jenkinsfile in the ansible-jenkins project. In the withCredentials block, modify the sshCommand by replacing the ls -l command with the ansible-playbook command. This command will run the Ansible playbook.
        ```
               sshCommand remote: remote, command: "ansible-playbook my-playbook.yaml"
        ```
        <img width="975" height="264" alt="image" src="https://github.com/user-attachments/assets/13b28ad5-7df9-44ed-85e2-ecbc285b03e6" />
        
      - In the terminal pane of Microsoft Visual Studio Code, use the git command to add the changes, specify a commit message, and push to the Gitlab repository.
        ```
               git add .
               git commit -m "Execute ansible command remotely"
               git push
        ```

      - Restore the Jenkins management UI and rerun the ansible-pipeline job. Confirm the build is successful:
        <img width="975" height="518" alt="image" src="https://github.com/user-attachments/assets/81ffad72-7f6b-4653-94c6-0b194531ff1d" />
        <img width="975" height="658" alt="image" src="https://github.com/user-attachments/assets/d4a03845-1c47-4da7-9c87-3f54065a9c12" />
        <img width="975" height="432" alt="image" src="https://github.com/user-attachments/assets/0348ca54-86b8-439a-bde3-8335539c2a0f" />

  - Jenkins Pipeline Optimization
    - Two optimizations will be applied to the Jenkins pipeline. First, since the Ansible server IP appears three times in Jenkinsfile, the Ansible server IP will be converted to an environment variable. Converting to an environment variable will make it so the              Ansible server IP address only has to be changed in one place moving forward. Second, a bash script will be used to automate the installation of Ansible and the Python-related packages for new server builds in the future.
    
    -  Environment Variable: Ansible Server IP
          - In this section, the Ansible Server IP will be converted to an environment variable.
            In Microsoft Visual Studio Code, restore the Jenkinsfile in the ansible-jenkins project. Notice the Ansible server IP appears three times – twice in the “copy files to ansible server” stage and once in the “execute ansible playbook” stage.
            Create an environment block between the agent any and stages block as show below

            ```
                   pipeline {
                       agent any
                       environment {
                       }
                        stages {
                         }
                     }
            ```

          - Inside the environment block, create a variable called ANSIBLE_SERVER and assign the Ansible server IP address as the value

            ```
                   ANSIBLE_SERVER = "x.x.x.x"
            ```
          - In the “copy files to ansible server” stage, locate the sshagent block where the SSH Agent plugin is used. Replace the Ansible IP with ${ANSIBLE_SERVER} as shown here:       

            ```
                   sh "scp -o StrictHostKeyChecking=no ansible/* root@${ANSIBLE_SERVER}:/root"
            ```
            
          - In the “copy files to ansible server” stage, locate the withCredentials block where the Credentials Binding plugin is used. Replace the Ansible IP with $ANSIBLE_SERVER. Recall the curvy brackets and double quotes cannot be used here to prevent the Jenkins              pipeline from showing the secret in the command history.
            ```
                   sh 'scp $keyfile root@$ANSIBLE_SERVER:/root/ssh-key.pem'
            ```
          - In the “execute ansible playbook” stage, locate the script block. Replace the value of the remote.host key with the value of ANSIBLE_SERVER as shown here:
            ```
                   remote.host = ANSIBLE_SERVER
            ```
         - In the terminal pane of Microsoft Visual Studio Code, use the git command to add the changes, specify a commit message, and push to the GiHub repository.
           ```
                 git add .
                 git commit -m "Create ansible server env var"
                 git push
           ```

         - Return to the Jenkins management UI and rerun the ansible-pipeline job. Confirm the build is successful:
           <img width="975" height="576" alt="image" src="https://github.com/user-attachments/assets/04cf0479-26be-4b06-ba9f-1a730cb7cfea" />


      - Bash Script: Prepare-Ansible-Server.sh
        -  The purpose of this section is to automate sections so that Ansible and Python's boto3 and botocore packages can be installed non-interactively. This is useful if installing on a fresh Ansible server in a Jenkins pipeline
           Restore the ansible-jenkins project in Microsoft Visual Studio Code. At the root of the project folder, create a new bash script called prepare-ansible-server.sh.
        - Add a shebang at the top of the prepare-ansible-server.sh file to notify the code editor this is the start of a bash script.
        
              ```
                    #!/usr/bin/env bash
              ```
            - Add the following apt commands to install Ansible, pip3, and boto3 and botocore Python packages.  The -y flag confirms the desire to proceed with the installation without manual intervention.
        
              ```
                    #!/usr/bin/env bash
                    apt update
                    apt install ansible -y
                    apt install python3-pip -y
                    apt install python3-boto3
                    apt install python3-botocore
              ```
            - Open the Jenkinsfile. In the “execute ansible playbook” stage, locate the withCredentials block. Add the following line above sshCommand:
        
              ```
                    sshScript remote: remote, script: "prepare-ansible-server.sh"
              ```
            - In the terminal pane of Microsoft Visual Studio Code, use the git command to add the changes, specify a commit message, and push to the GitHub repository.
              ```
                  git add .
                  git commit -m "Add Ansible server script optional step"
                  git push
              ```
            - Return to the Jenkins management UI. Rerun the ansible-pipeline job and confirm the build is successful.
              <img width="975" height="581" alt="image" src="https://github.com/user-attachments/assets/08be7c03-ac34-4197-8c7d-14ab58a153ed" />

            - On the Console Output screen, review the console output. Notice the output shows that ansible, pip3, and the boto3 and botocore packages are already the latest versions
              <img width="975" height="384" alt="image" src="https://github.com/user-attachments/assets/1d37fd47-f26e-4b1d-a574-ba47f04e92ef" />
              <img width="975" height="441" alt="image" src="https://github.com/user-attachments/assets/c3d651ea-9812-4604-9ea1-f06f40040720" />


              


