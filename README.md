# Managing File Permissions using Linux Commands


-------

# Description <a name="description">

I used Linux Commands to manage file permissions for a fictional research team. This assessment was completed as a component of my cybersecurity portfolio and as part of the <a href='https://www.coursera.org/google-certificates/cybersecurity-certificate'>Google Cybersecurity Professional Certificate</a> on Coursera, specifically in the  <a href='https://www.coursera.org/learn/linux-and-sql'> "Tools of the Trade: Linux and SQL" </a> Course.

This scenario is connected to a lab on how to examine and manage file permissions. I will explain the commands I used in that lab.

# Scenario  <a name="scenario">
You are a security professional at a large organization. You mainly work with their research team. Part of your job is to ensure users on this team are authorized with the appropriate permissions. This helps keep the system secure. 

Your task is to examine existing permissions on the file system. The research team at my organization needs to update the file permissions for certain files and directories within the projects directory. You need to determine if the permissions match the authorization that should be given. If they do not match, you’ll need to modify the permissions to authorize the appropriate users and remove any unauthorized access.

------------------------
   
Checking File and Directory Details  <a name="control-assessment">
===================
The following code shows how I used Linux commands to identify the current permissions set for a particular directory in the file system.

<p align="center">
Code: <br/>
<img src="https://i.imgur.com/Lr4WveE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

The command I typed is shown on the first line of the screenshot, and the output is shown on the following lines. The code contains a list of every file in the projects directory. I displayed a thorough listing of the file contents that included hidden files using the ls command with the -la option. According to the results of my command, there is one directory called drafts, one hidden file with the name.project_x.txt, and five additional project files. The permissions assigned to each file or directory are represented by the 10-character string in the first column.

### Describing the Permission String
To find out who is allowed to access the file and what permissions they have, the 10-character string can be broken down. The following are the characters and what they stand for:
- 1st character: This character is either a d or hyphen (-) and indicates the file type. If it’s a d, it’s a directory. If it’s a hyphen (-), it’s a regular file.
- 2nd-4th characters: These characters indicate the read (r), write (w), and execute (x) permissions for the user. When one of these characters is a hyphen (-) instead, it indicates that this permission is not granted to the user.
- 5th-7th characters: These characters indicate the read (r), write (w), and execute (x) permissions for the group. When one of these characters is a hyphen (-) instead, it indicates that this permission is not granted for the group.
- 8th-10th characters: These characters indicate the read (r), write (w), and execute (x) permissions for other. This owner type consists of all other users on the system apart from the user and the group. When one of these characters is a hyphen (-) instead, that indicates that this permission is not granted for other.

For example, the file permissions for project_t.txt are -rw-rw-r--. The fact that project_t.txt's first character is a hyphen (-) indicates that it is a file, not a directory. Indicating that user, group, and other all have read permissions, the second, fifth, and eighth characters are all rs. Only the user and group have write permissions, as shown by the third and sixth characters, which are w. No one has the ability to execute project_t.txt.

Changing File Permissions  <a name="control-assessment">
===================

The company decided that no one else should be able to write to any of their files. I referred back to the file permissions that I had previously returned in order to comply with this. I came to the conclusion that project_k.txt needs the write access disabled for others.

The code below shows how I accomplished this using Linux commands:
<p align="center">
Code: <br/>
<img src="https://i.imgur.com/1Vr4w1w.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

The screenshot's first two lines show the commands I typed in, and the following lines show the second command's output. The chmod command modifies a file's or directory's permissions. The first argument describes which permissions should be modified, and the second argument names the file or directory. In this case, I disabled other's ability to write to the project_k.txt file. I then used ls -la to look over the updates I had made.

Changing File Permissions on a Hidden File  <a name="control-assessment">
===================

Project_x.txt was recently archived by my organization's research team. The user and group should only be able to read this project; they do not want anyone to have write access. 

The code below shows how I changed the permissions using Linux commands:

<p align="center">
Code: <br/>
<img src="https://i.imgur.com/02Ibvzv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

The screenshot's first two lines show the commands I typed in, and the following lines show the second command's results. I know .project_x.txt is a hidden file because it starts with a period (.). In the example above, I gave the group read permissions while removing write permissions from the user and group. I used u-w to take the user's write permissions away. I then added read permissions to the group with g+r and removed write permissions with g-w. 

Changing Directory Permissions  <a name="control-assessment">
===================
My company only wants the researcher2 user to be able to access the drafts directory and everything inside of it. This indicates that only researcher2 should be granted execute permissions.

The code below shows how I changed the permissions using Linux commands:

<p align="center">
Code: <br/>
<img src="https://i.imgur.com/lRROcIw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

The screenshot's first two lines show the commands I typed in, and the following lines show the second command's results. I used the chmod command to remove the execute permissions after previously identifying that the group had them. It was not necessary to add execute permissions because the researcher2 user already had them.

Summary  <a name="control-assessment">
===================
In order to give files and directories in the projects directory the level of authorization that my organization desired, I changed a number of permissions. Using ls -la to check the directory's permissions was the first step in this process. My choices in the next steps were influenced by this. Then, I repeatedly used the chmod command to alter the permissions of files and directories.
