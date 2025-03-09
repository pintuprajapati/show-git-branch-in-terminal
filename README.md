# Show Git Branch Name in Terminal

This guide helps you modify your Ubuntu/Linux terminal prompt to display the current Git branch name when inside a Git repository.

## Steps to Enable Git Branch Display in Terminal

Follow these steps to modify your `~/.bashrc` file and enable Git branch display in your terminal prompt:

### 1. Open the Terminal

### 2. Edit the `.bashrc` File
Type the following command to open the `.bashrc` file in the nano editor:
```bash
nano ~/.bashrc
```

### 3. Scroll to the Bottom of the File
Use the arrow keys to navigate to the bottom of the `.bashrc` file.

### 4. Copy and Paste the Code Below
Copy the following code and paste it at the end of the `.bashrc` file:

```bash
########### Show git branch name ###########
force_color_prompt=yes
color_prompt=yes
parse_git_branch() {
 git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/(\1)/'
}
if [ "$color_prompt" = yes ]; then
 PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[01;31m\]$(parse_git_branch)\[\033[00m\]\$ '
else
 PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w$(parse_git_branch)\$ '
fi
unset color_prompt force_color_prompt
#############################################
```

To paste in nano:
- Use `Ctrl + Shift + V` or
- Right-click and select **Paste**

### 5. Save and Exit
To save the file in nano:
- Press `Ctrl + O` (write out)
- Press `Enter` (confirm save)
- Press `Ctrl + X` (exit nano)

### 6. Apply the Changes
Restart the terminal or run the following command to apply the changes immediately:
```bash
source ~/.bashrc
```

## Verification
Now, when you navigate into a Git repository, your terminal prompt will display the current Git branch name next to the directory path.

**Example:**
```
user@hostname:~/my-repo (main)$
```
This indicates that the user is inside the `my-repo` directory and currently on the `main` branch.

## License
This script is open-source and free to use. Feel free to modify and share it!

