
# Some Linux/Unix-terminal Commands

1. **cd**: Change directory - `cd <directory-name>`
2. **pwd**: Present working directory - `pwd`
3. **ls**: 'List' contents of current working directory - `ls`
4. **rm**: Remove/delete a file - `rm`
5. **clear**: Clear all text in terminal window - `clear`
6. **touch**: Create a new file - `touch <filename.extension>`

###  Uninstall Installed Packages
- Run the following command to view the log and find installed packages:
  - `less /var/log/apt/history.log`
- To uninstall a package, use the following command:
  - `sudo apt remove <package_name>`
- To completely remove the package, including its configuration files, use:
  - `sudo apt purge <package_name>`
- Automatic Removal of Unused Dependencies:
  - `sudo apt autoremove` 

### Write into a file:
- **echo**: Write a single line.
  1. `echo "your content" > filename.txt`
  2. `echo "additional content" >> filename.txt`  // Appends content instead of overwriting.
  
- **cat**: Write multiple lines (type content and press 'ctrl+D' to save).
  1. `cat > filename.txt`
  2. `cat >> filename.txt`  // To append new items.
  
- **nano/vim**: Open a file in a text editor like 'nano' or 'vim'.
  - `nano <filename.txt>`
  
- **Display file content**: 
  - `cat <filename.txt>`

7. **mv**: Rename a file. 
  - `mv [source] [destination]`
  - Example: `mv 'old_name' 'new name'`

---

# Access Your GitHub Account Remotely

### 1. Personal Access Token (PAT)
Use correct username and password. To generate a PAT:
   1. Go to 'Github Settings';
   2. Click 'Generate new token';
   3. Select the necessary scopes and generate the token;
   4. Copy the token (Caution: You will not be able to see it again).

### 2. Update the Remote URL Using HTTPs:
Open terminal in your repo and set the remote URL with the token:
   - `git remote set-url origin https://<TOKEN>@github.com/username/repo.git`

### 3. Use Git Credential Manager (GCM)
   1. Install GCM, if not installed already.
   2. Configure Git to use GCM:
      - `git config --global credential.helper manager`
   3. Cache your credentials.

### 4. Clear Cached Credentials:
   - `git credential-cache exit`

---

### 5. SSH Authentication (Alternative to HTTPs):
   1. Generate an SSH key (if not done already):
      - `ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`
      
   2. Add the SSH key to the ssh-agent:
      - `eval "$(ssh-agent -s)"`
      - `ssh-add ~/.ssh/id_rsa`
   
   3. Add the SSH key to your GitHub account:
      - Copy the SSH key to your clipboard:
        - `cat ~/.ssh/id_rsa.pub`
      - Go to GitHub SSH and GPG keys settings and add a new SSH key.
      
   4. Update the remote URL to use SSH:
      - `git remote set-url origin git@github.com:username/repo.git`
