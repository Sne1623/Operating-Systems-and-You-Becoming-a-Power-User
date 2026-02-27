Project: Windows System Administration & User Management
Course: Operating Systems and You – Becoming a Power User

Technician: Sinenhlanhla Khumalo

Deadline: February 27, 2026

 Introduction
This project demonstrates the core competencies of a Windows Power User, specifically focusing on Operating System Internals and Command-Line Interface (CLI) proficiency.

The objective was to perform advanced administrative tasks without a Graphical User Interface (GUI). By utilizing Windows PowerShell and the Chocolatey Package Manager, I successfully automated software installation, created a secure local user profile, and managed complex file system permissions (ACLs). This workflow simulates real-world system administration and server management environments.
Step 1: Package Management (Chocolatey)
To demonstrate command-line software installation, I utilized Chocolatey, a Windows package manager. This allows for automated, scriptable software deployment.

Software_Installation_Chocolatey	
<img width="858" height="279" alt="screenshot1" src="https://github.com/user-attachments/assets/d48d2032-c0e0-4152-b270-5b04985691c9" />

The PowerShell window showing the green text where Chocolatey and VLC finish installing.

 User & Group Management
In this phase, I created a new local user account named Student_Admin with a secure password to simulate onboarding a new administrative user.

# 1. Store the password as a secure string
$Password = ConvertTo-SecureString "P@ssword2026!" -AsPlainText -Force

# 2. Create the new user "Student_Admin"
New-LocalUser -Name "Student_Admin" -Password $Password -FullName "Project Admin User" -Description "User for OS Project"

# 3. Verify the user exists in the system
<img width="754" height="230" alt="screenshot2" src="https://github.com/user-attachments/assets/c340a0f1-3830-4b4c-a92a-171be71abe37" />

Show the output of the Get-LocalUser command showing the account "Student_Admin".

 File System Permissions (ACL)
This step involves creating a directory and managing Access Control Lists (ACL) to ensure only the designated user has "Full Control" over the project folder.

# 1. Create a project folder on the C: drive
New-Item -Path "C:\OS_Project" -ItemType Directory

# 2. Grant "Full Control" (F) to Student_Admin
icacls "C:\OS_Project" /grant Student_Admin:F

# 3. Verify the permissions are correctly applied
<img width="1014" height="699" alt="screenshot 3" src="https://github.com/user-attachments/assets/85ca813a-9e6a-4c63-a023-13994e754699" />

Show the result of the icacls command where "Student_Admin:(F)" is visible.

 Conclusion
The successful completion of this project highlights the efficiency of using PowerShell for system administration. By moving away from the GUI, I was able to perform precise user management and file security tasks that are easily repeatable and scalable.
