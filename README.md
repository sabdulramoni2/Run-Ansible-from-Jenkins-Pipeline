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
        -f = path to the private key
        -m = the file extension
        P = old passphrase
        N = new passphrase
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










    








  










