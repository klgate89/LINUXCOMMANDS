<h1> File permissions in Linux </h1>

 
<h2>Project Description</h2>
<i>This scenario is based on a fictional company:</i>
<br><br>
The research team at my organization needs to update the file permissions for certain files and directories within the <b>projects</b> directory. The permissions do not currently reflect the level of authorization that should be given. Checking and updating these permissions will help keep their system secure. To complete this task, I performed the following tasks:

<h2> Check file and directory details </h2>

The following code demonstrates how I used Linux commands to determine the existing permissions set for a specific directory in the file system.

<img src="https://i.ibb.co/02fDvy8/Image-1-in-order.png" alt="Image-1-in-order" border="0">
<br>
The first line of the screenshot displays the command I entered, and the other lines display the output. The code lists all contents of the <b>projects</b> directory. I used the ls command with the -la option to display a detailed listing of the file contents that also returned hidden files. The output of my command indicates that there is one directory named <b>drafts</b>, one hidden file named <b>.project_x.txt</b>, and five other project files. The 10-character string in the first column represents the permissions set on each file or directory.

<h2> Describe the permissions string</h2>

The 10-character string can be deconstructed to determine who is authorized to access the file and their specific permissions. The characters and what they represent are as follows:

- <B>1st character:</B> This character is either a d or hyphen (-) and indicates the file type. If it’s a d, it’s a directory. If it’s a hyphen (-), it’s a regular file.

- <b>2nd-4th characters:</b> These characters indicate the read (r), write (w), and execute (x) permissions for the user. When one of these characters is a hyphen (-) instead, it indicates that this permission is not granted to the user.

- <b>5th-7th characters:</b> These characters indicate the read (r), write (w), and execute (x) permissions for the group. When one of these characters is a hyphen (-) instead, it indicates that this permission is not granted for the group.

- <b>8th-10th characters:</b> These characters indicate the read (r), write (w), and execute (x) permissions for other. This owner type consists of all other users on the system apart from the user and the group. When one of these characters is a hyphen (-) instead, that indicates that this permission is not granted for other.

For example, the file permissions for <b>project_t.txt</b> are <b>-rw-rw-r--</b>. Since the first character is a hyphen (-), this indicates that <b>project_t.txt</b> is a file, not a directory. The second, fifth, and eighth characters are all r, which indicates that user, group, and other all have read permissions. The third and sixth characters are w, which indicates that only the user and group have write permissions. No one has execute permissions for <b>project_t.txt</b>.

<h2> Change file permissions </h2>

The organization determined that other shouldn't have write access to any of their files. To comply with this, I referred to the file permissions that I previously returned. I determined <b>project_k.txt</b> must have the write access removed for other.

The following code demonstrates how I used Linux commands to do this:

<img src="https://i.ibb.co/fYgpR4y/Image-2-in-order.png" alt="Image-2-in-order" border="0">
The first two lines of the screenshot display the commands I entered, and the other lines display the output of the second command. The <b>chmod</b> command changes the permissions on files and directories. The first argument indicates what permissions should be changed, and the second argument specifies the file or directory. In this example, I removed write permissions from other for the <b></b>project_k.txt</b> file. After this, I used ls -la to review the updates I made.

<H2>Change file permissions on a hidden file</H2>

The research team at my organization recently archived <b>project_x.txt</b>. They do not want anyone to have write access to this project, but the user and group should have read access. 

The following code demonstrates how I used Linux commands to change the permissions:

<img src="https://i.ibb.co/m9DjpzY/Image-3-in-order.png" alt="Image-3-in-order" border="0">
The first two lines of the screenshot display the commands I entered, and the other lines display the output of the second command. I know <b>.project_x.txt</b> is a hidden file because it starts with a period (.). In this example, I removed write permissions from the user and group, and added read permissions to the group. I removed write permissions from the user with u-w. Then, I removed write permissions from the group with g-w, and added read permissions to the group with g+r. 

<H2>Change directory permissions</H2>

My organization only wants the <b>researcher2</b> user to have access to the drafts directory and its contents. This means that no one other than <b>researcher2</b> should have execute permissions.

The following code demonstrates how I used Linux commands to change the permissions:

<img src="https://i.ibb.co/wsCww5D/Image-4-in-order.png" alt="Image-4-in-order" border="0">

The first two lines of the screenshot display the commands I entered, and the other lines display the output of the second command. I previously determined that the group had execute permissions, so I used the chmod command to remove them. The <b>researcher2</b> user already had execute permissions, so they did not need to be added.

<H2>Summary</H2>

I changed multiple permissions to match the level of authorization my organization wanted for files and directories in the <b>projects</b> directory. The first step in this was using <b>ls -la</b> to check the permissions for the directory. This informed my decisions in the following steps. I then used the <b>chmod</b> command multiple times to change the permissions on files and directories.
