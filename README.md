<h1>File Permissions in Linux</h1>


<h2>Scenario</h2>
You are a security professional at a large organization. You mainly work with their research team. Part of your job is to ensure users on this team are authorized with the appropriate permissions. This helps keep the system secure.
<br />
<br/>
Your task is to examine existing permissions on the file system. You'll need to determine if the permissions match the authorization that should be given. If they do not match, you'll need to modify the permissions to authorize the appropriate users and remove any unauthorized access. 
<br />


<h2>Program walk-through:</h2>

<p align="center">
<b>Check file and directory details:</b> <br/>
<br />
The following code demonstrates how I used Linux commands to determine the existing permissions set for a specific directory in the file system
<br />
<br/>
<img src="https://imgur.com/VFjkwjI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
The first line of the screenshot displays the command I entered, and the other lines display the output. The code lists all contents of the <b><i>projects</b></i> directory. I used the <b><i>ls</b></i> command with the <b><i>-la</b></i> option to display a detailed listing of the file contents that also returned hidden files. The output of my command indicates that there is one directory named <b><i>drafts</b></i>, one hidden file named <b><i>.project_x.txt</b></i>, and five other project files. The 10-character string in the first column represents the permissions set on each file or directory. 
<br />
<br />
The 10-character string can be deconstructed to determine who is authorized to access the file and their specific permissions. The characters and what they represent are as follows:
<br />
  -<b>1st character:</b> This character is either a <b><i>d</b></i> or a hyphen <b><i>(-)</b></i> and indicates the file type. If it's a <b><i>d</b></i>, it is a directory. If it is a hyphen <b><i>(-)</b></i>, it is a regular file.
<br />
  -<b>2nd-4th characters:</b> These characters indicate the read <b><i>(r)</b></i>, write <b><i>(w)</b></i>, and execute <b><i>(x)</b></i> permissions for the user. When one of these characters is a hyphen <b><i>(-)</b></i> instead, it indicates that this permission is not granted to the user.
<br />
  -<b>5th-7th characters:</b> These characters indicate the read <b><i>(r)</b></i>, write <b><i>(w)</b></i>, and execute <b><i>(x)</b></i> permissions for the group. When one of these characters is a hyphen <b><i>(-)</b></i> instead, it indicates that this permission is not granted to the group.
<br />
  -<b>8th-10th characters:</b> These characters indicate the read <b><i>(r)</b></i>, write <b><i>(w)</b></i>, and execute <b><i>(x)</b></i> permissions for other. This owner type consists of all other users on the system apart from the user and the group. When one of these characters is a hyphen <b><i>(-)</b></i> instead, it indicates that this permission is not granted for other.
<br />
<br />
<b>Change File Permissions</b>  <br/>
The organization determined that other shouldn't have write access to any of their files. To comply with this, I referred to the file permissions that I previously returned. I determined that <b><i>project_k.txt</b></i> must have the write access removed for other.
<br />
<br />
The following code demonstrates how I used Linux commands to do this:
<img src="https://imgur.com/2kvDx4M.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
The first two lines of the screenshot display the command I entered, and the other lines display the output of the second command. The <b><i>chmod</b></i> command changes the permissions on files and directories. The first argument indicates what permissions should be changed, and the second argument specifies the file or directory. In this example, I removed write permissions from other for the <b><i>project_k.txt</b></i> file. After this, I used <b><i>ls -la</b></i> to review the updates I made. 
<br />
<br />
<b>Change File Permissions on a Hidden File:</b> <br/>
The research team at my organization recently archived <b><i>project_x.txt</b></i>. They do not want anyone to have write access to this project, but the user and group should have read access.
<br />
<br />
The following code demonstrates how I used Linux commands to change the permissions.
<img src="https://imgur.com/WBUJOY0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
The first two lines of the screenshot display the commands I entered, and the other lines display the output of the second command. I know <b><i>.project_x.txt</b></i> is a hidden file because it starts with a period. In this example, I removed write permissions from the user and group, and added read permissions to the group. I removed write permissions from the user with <b><i>u-w</b></i>. Then, I removed write permissions from the group with <b><i>g-w</b></i>, and added read permissions to the group with <b><i>g+r</b></i>.
<br />
<br />
<b>Change Directory Permissions:</b>  <br/>
My organization only wants the <b><i>researcher2</b></i> user to have access to the <b><i>drafts</b></i> directory and its contents. This means no one other than <b><i>researcher2</b></i> should have execute permissions.
<br />
<br />
The following code demonstrates how I used Linux commands to change the permissions.
<img src="https://imgur.com/PxtsGU4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br/>
The output here displays the permission listing for several files and directories. Line 1 indicates that the current directory (projects), and line 2 indicates the parent directory (home). Line 3 indicates a regular file titled <b><i>.prokect_x.txt</b></i>. Line 4 is the directory (drafts) with restricted permissions. Here you can  see that only researcher2 has execute permissions. It was previously determined that the group had execute permissions, so I used the <b><i>chmod</b></i> command to remove them. The <b><i>researcher2</b></i> user already had execute permissions, so they did not need to be added. 
<br />
<br />


<h2>Summary</h2>
I changed multiple permissions to match the level of authorization my organization wanted for files and directories in teh <b><i>projects</i></b> directory. The first step in this was using <b><i>ls -la</i></b> to check the permissions in the directory. This informed my decisions in the following steps. I then usedd the <b><i>chmod</i></b> command multiple times to change the permissions on files and directories. 
<br />

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
