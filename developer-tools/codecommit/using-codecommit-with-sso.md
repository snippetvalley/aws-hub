##  AWS CodeCommit using AWS SSO 


We need to setup git-remote-codecommit to connect CodeCommit Using a root account, federated access, or temporary credentials .Follwing  Steps are helping you to setup  git-remote-codecommit.   
      
### Step 1: Install Prerequisites for git-remote-codecommit

Note!
 we need must install **Python Version 3** or Later and its package manager pip , git-remote-codecommit requires **pip version 9.0.3** or later.
 
Install Python 

   |                                                           For Windows                                                           |
   | ------------------------------------------------------------------------------------------------------------------------------- |
   |1. Download and Install latest python. [Download Python for windows ](https://www.python.org/downloads/) .Ensure that the Install launcher for all users (recommended). And the Add Python 3.7 tonPATH checkboxes at the bottom are checked |
   
   |                                                          For MAC                                                                |
   | ------------------------------------------------------------------------------------------------------------------------------- |
   |1. Download and Install latest python.[Download Python for mac](https://www.python.org/ftp/python/3.7.7/python-3.7.7-macosx10.9.pkg)|
    
    
 To Verify python Installition Type the Below Command (it will work both windows and mac )
 ```python
  python --version 
  ```
 Once you’ve confirmed that Python is correctly installed, you can proceed with installing Pip.      
 
Installing Pip

   |                                              For Windows                                                                       |
   |  ----------------------------------------------------------------------------------------------------------------------------- |
   | 1. Download and install Pip [Download](https://pip.pypa.io/en/stable/installing/#do-i-need-to-install-pip) Download *get-pip.py* to a folder on your computer. Open a command prompt and navigate to the folder containing *get-pip.py*.                                |
   
   Run the following command on CMD in Windows System:
   
   ```python
   python get-pip.py
   ```
    
    
  |                                             For MAC                                                                            |
  |  ----------------------------------------------------------------------------------------------------------------------------  |
  | 1.  for Download  `curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py`for install  `python get-pip.py`                    |
          
Pip is now installed!

To check your version of pip, open a terminal or command line and run the following command:

 ```python
 pip --version
 ```
 
 2. Download and install git. [Download Git for windows](https://github.com/git-for-windows/git/releases/download/v2.25.1.windows.1/Git-2.25.1-64-bit.exe) For Mac [Download git for Mac ](https://central.github.com/deployments/desktop/desktop/latest/darwin)
 
 Note! -  CodeCommit supports **Git versions 1.7.9** and later. make sure in  instaltion time **Disable Git Credential Manager option**
 
###  Step 2: Install git-remote-codecommit
Follow these steps to install git-remote-codecommit.
To install git-remote-codecommit At the terminal or command line, run the following command:

Note! - Below Commands are suppoting in both platform (windows/Mac) 

```python
 pip install git-remote-codecommit
 ```
 For Upgrade and install to latest version 
 
```python
pip install --upgrade git-remote-codecommit
```
Below is the message of sucess installtion :

```
Successfully built git-remote-codecommit
```

### Step 3: Set Up the Credential Helper
Open a command prompt and use Followig Command  that  enables the Git credential helper to send the path to repositories:

```
 git config --global credential.helper "!aws codecommit credential-helper $@"

 git config --global credential.UseHttpPath true
```

above  Commannd writes the following to the .gitconfig file:
```
[credential]    
    helper = !aws codecommit credential-helper $@ 
    UseHttpPath = true
```
 
### Step 4 :- To install and configure the AWS CLI

Download  and install the AWS CLI [Download AWS Cli for windows  ](https://s3.amazonaws.com/aws-cli/AWSCLI64PY3.msi).  CodeCommit works only with **AWS CLI versions 1.7.38** and later. 

Download and install the AWS Cli On Mac Follow the below steps 
  
  ```
     curl "https://s3.amazonaws.com/aws-cli/awscli-bundle.zip" -o "awscli-bundle.zip"
     unzip awscli-bundle.zip
     sudo ./awscli-bundle/install -i /usr/local/aws -b /usr/local/bin/aws

```

To determine which version of the AWS CLI you have installed, run the follwing Command 
```
aws --version 
```

### Step 5 :- Configure AWS CLI with your SSO Credential 

We need to bookmark our sso signup link . Example is  following  below .
       
 **https://my-sso-portal.awsapps.com/start**

Copy and  paste the link in your browser and select your account , it will give you two options as like management Console and programmatic  access . Here we need to click on programmatic access , again it will give you two options as like MAC/Linux and windows . Here you need to select  credential key according to your operating system Support , copy environment credential and paste it in CMD/Terminal. this process will add credetial for aws on your system .

Note! if you get error like "select the region" , you need to run `aws configure` and set the region for the first time only . 

### Step 6: Connect to the CodeCommit Console and Clone the Repository

Open the CodeCommit console at **https://console.aws.amazon.com/codesuite/codecommit/home.**
```
 git clone  codecommit::us-west-1://MyDemoRepo
```

For more Refrences [git-remote-codecommit clone step for Windows ](https://docs.aws.amazon.com/codecommit/latest/userguide/setting-up-git-remote-codecommit.html)
