# Lesson 1: The Command Line

## Objectives

1. Be familiar with the Command Line Interface
2. Compare the Windows and Linux  CLI
3. Perform basic Command Line operations using PowerShell in Windows and Terminal in Ubuntu

## What is the Command Line?

The command line is a powerful, text-based interface to your computer. As developers we will use it extensively throughout this course to install and configure the tools that we will need to build Web application including Python, Django, Git, etc. We'll also be using the command line to manage our Web application projects.

On Windows machines there are actually two built-in command shells: the **Command** shell and **PowerShell** with the latter being the more powerful of the two. In Ubuntu, you have the Gnome Terminal or simply **Terminal** which runs the Bourne Again Shell or **BASH** by default.

## How does the Command Line Works?

A command shell works like a language translator,  it accepts human readable commands and translates them into something the Operating System can read and process.

**Command Syntax**
**`command [ARGUMENT]...`**  

For example,

```bash
echo Hello
echo -n Hello
```

```powershell
Write-Host Hello
Write-Host Hello -Separator ";"
```

*Note!* In Linux, commands are case-sensitive, but in Windows, it is not. 

**Getting Help**

**`man COMMAND`**

For example, to know how the `pwd` command is used, type:

```bash
man pwd
```

## What Basic Commands Should You Know?

- **`ls`** (list files in your current directory)
	```bash
ls
ls ~
ls Desktop
ls -l Desktop
ls -l -h Desktop
ls -lh Desktop
ls D*
	```
*Note!* Both Windows and Linux, uses aliases for special directories such as root directory ( **`/`**),  user\'s home directory (**`~`**),  parent directory (**`..`** ) and  current directory (**`.`**). The asterisk (**\***) is a wildcard character which matches all strings
	
- **`cd`** (change directory)
	
	```bash
cd
cd Desktop
cd ~/Documents
cd ..
cd /
cd /var/www
	```
	*Note!* In Linux, forward slash (`/`) is used as a directory separator. Windows uses backslash (`\`) instead. 

	```powershell
	cd C:
	cd \
	cd \Users\
	```
	
- **`mkdir`** (make directory)
	```mkdir
mkdir CSDC105
mkdir CSDC105/Labs
mkdir 'Trends in Application Development'
mkdir -p ADNU/Classes/'First Sem'
	```

- **`rmdir`** (remove directory)
 	```bash
rmdir CSDC105/Labs
	```

- **`touch`** (create a file)
	```bash
touch README.md
	```
*Note!* Powershell does not have a `touch` command, but you can create an alias for the `New-Item` command.
	```powershell
Set-Alias touch New-Item
	touch README.md
	```
	
- **`cp`** (copy files and directories)
	```bash
cp README.md instructions.txt 
cp instructions.txt CSDC105/
cp instructions.txt CSDC105/ideas.html
cp -r CSDC105/ Desktop/ 
	```
	
- **`mv`** (rename files and directories)
	```bash
mv README.md INFO.txt 
mv INFO.txt CSDC105/
mv CSDC105/Labs CSDC105/Work 
	```

- **`rm`** (remove files and directories)
	
	```bash
rm instructions.txt
rm -f instructions.txt
rm -r -f CSDC105/Work
	```
	```powershell
rm instructions.txt
rm -Force instructions.txt
rm -Recursive -Force CSDC105/Work
	```

## Additional Commands

- **`>`** (output redirection)
	
	```bash
echo "Hello" > hello.txt
	```
	
- **`>>`** (output redirection, append)

	```bash
echo "Hi!" >> hello.txt
	```

- - **`|`** (pipe)
	```bash
cat hello.txt | grep "ello"
	```
	

*Note!* The `grep` command for pattern maching is only available in Linux

## Some Tips!

- You can change theme/look and feel of the Command Line

- In Linux, you can change your shell application (popular options include `csh`, `zsh`, `fsh`)

- You can also define aliases to the commands you use the most in BASH:
	
	```bash
alias ls="ls -lh"
ls
	```

- You may want to install a tiling Terminal application such as `tilix`

  	```bash
sudo apt install tilix
tilix
	```
