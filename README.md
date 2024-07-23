# Setting Up the Development Environment with a Shell Script

The script, `1-installation`, is designed to set up a development environment on a system that uses the RPM Package Manager (e.g., Fedora, CentOS)... for now! I will add other scripts for other operating systems in the future! It will download C/C++, Java, Python, and Git for you after executing the script. 

If you also want Visual Studio Code as your text editor, the script `2-vscode` will install Visual Studio Code on your Linux computer. 

I also included the essentials and some useful VsCode extensions in the script `3-extensions`. Running the script will install all of them at once. 

The `all-in-one` script is for my students who want to set up their development environment without worry. Most importantly, we can definitely finish the installation and explanation in one hour.

I hope they help. Happy coding!

<img width="1200" alt="Screenshot 2024-07-22 at 3 34 12 PM" src="https://github.com/user-attachments/assets/61f0e296-9b3d-4d6a-aa91-fc792680796a">

<br /> 

## Motivation

I am a community college tutor (in 2023-2024). Students come to me to ask for help downloading the vscode for each semester. I thought, "This is a computer thing... it should be able to be solved with computer language." Recently, I have learned Linux and realized that a shell script can solve the problem! And here comes the solution!

It also helps me set up my Linux virtual machine, saving me time. I hope this can save you time, too! 

<br /> 

## Get started

### Step 1: Create the Shell Script
1. Open a Terminal from the menu or press `Ctrl + Alt + T`.
2. Create a new script file with `vi` or `nano`. I will use `vi` here and name the file "vscode": `vi vscode.sh`
3. Copy and Paste the Script depending on the purpose or the operating system. I used the `vscode` as an example here.
     ```
      # Yi-Lu Wu 2024
      # Install the vscode on Linux (CentOS 9 Stream)
      
      #!/bin/bash
      
      # 1. download the repository
      sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
      echo -e "[code]\nname=Visual Studio Code\nbaseurl=https://packages.microsoft.com/yumrepos/vscode\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" | sudo tee /etc/yum.repos.d/vscode.repo > /dev/null
      
      # 2. update the package and install the vscode
      dnf check-update
      sudo dnf install code # or code-insiders
    ```
   P.S. You can delete or comment on any development tools if you don't need them.
   For example, if you copy the `1-installation` and don't want to download git, simply add `#` before `sudo dnf install git`.
   
5. Save and Exit.


### Step 2: Make the Script Executable
1. Change the Script Permissions with the command `chmod a+x [YOUR_SCRIPT_NAME]` or `sudo chmod a+x [YOUR_SCRIPT_NAME]` if you are not the root user.
   ```
   chmod a+x vscode
   ```

<img width="600" alt="Screenshot 2024-07-22 at 2 06 17 PM" src="https://github.com/user-attachments/assets/d5a08dd2-c9f1-4a8f-9c51-52c70c7dae57">

### Step 3: Run the Script
1. Run the script with the following command: `./[YOUR_SCRIPT_NAME].sh`
   ```
   ./vscode.sh
   ```
2. If you are running the `1-installation` or `2-vscode`, it will ask you, `Is this ok [y/N]:`. Answer `y` to agree on the installation.
<img width="600" alt="Screenshot 2024-07-22 at 2 06 37 PM" src="https://github.com/user-attachments/assets/d336b61c-b2e3-4799-86f4-eca9670475e2">

### Step 4: Verify the Installation

1. After running the `vscode.sh` script, you should be able to open Visual Studio Code by typing `code` in the terminal.
2. If you also run the `1-installation` script, verify that `gcc`, `g++`, `java`, `javac`, `python3`, and `git` are installed by checking their versions:
   ```
   gcc --version
   g++ --version
   java --version
   javac --version
   python3 --version
   git --version
   ```
   
   <img width="1200" alt="Screenshot 2024-07-22 at 4 04 32 PM" src="https://github.com/user-attachments/assets/5ecda411-d21d-4bbf-9561-7ecb2eae28b4">

   If any of them return `command not found...`, it means there is an issue with the installation. You can copy the command to the terminal again. If an error message pops up, search for the message on Google or ask chatGPT for help. Problem-solving is also an important ability for a software programmer.

3. For the `3-extensions` script, it's the same concept! Here is the outcome:
   
   <img width="600" alt="Screenshot 2024-07-22 at 2 08 38 PM" src="https://github.com/user-attachments/assets/121011ee-a418-479e-8c1f-7f3cb53d736b">

<br /> 

### Note: On the screenshot, why didn't I put `.sh` at the end of my script?
It's okay to create a script without a specific extension, such as `vi vscode` instead of `vi vscode.sh`.

<img width="600" alt="Screenshot 2024-07-22 at 3 30 27 PM" src="https://github.com/user-attachments/assets/03d55329-0ec9-402b-8fa6-752452ea323e">

The `.sh` extension explicitly indicates that this file is a shell script. This makes it easier for users and system tools to identify the file type, and editors and command-line tools that recognize the .sh extension might handle it differently. Also, many text editors provide syntax highlighting based on the file extension, making it easier to read and edit the script.

<br />

## Conclusion

Yeah! We've successfully set up our development environment using the provided shell script. We now have Visual Studio Code, compilers for C/C++, Java, Python, and Git installed on our system. Happy coding!

<br /> 

If you encounter any issues or have further questions, feel free to ask for help.
