- h2, h3, number list, color titles,
- command line
	- summary
	  collapsed:: true
		- a program that could running instructions,
		- basic syntax likes other code, `command -argument1 argument2...`, arguments need to *separated by space*,
	- general
	  collapsed:: true
		- use `Ctrl + C`to stop the command,
		- use `Ctrl + D`to kill the terminal,
		- help
		  collapsed:: true
			- use `help` command to see all commands' help document,
			- use `tldr command` or `whatis command` to see a brief introduction to the command,
			- `man command`will show complex manual of the command,
		- `history`will show history commands,
		- `clear` will clear the STDOUT,
	- path(directory)
	  collapsed:: true
		- environment variables
		  collapsed:: true
			- `which command` will show the *default* installing path of the command,
			- `whereis command` will show *all* installing path of the command,
		- absolute path
		  collapsed:: true
			- path started with `/`(root directory),
		- relative path
		- `pwd`(print work directory)
		- `cd`(change directory)
		  collapsed:: true
			- `.`means present directory,
			- `..`means up directory,
			- use *absolute path* to change to the directory, like `cd /home/abc/Code`,
			- use `cd -` to change between nearly used directories,
		- `ls`(list)
		  collapsed:: true
			- print all files in the directory,
			- use `-l` to display in long mode(detailed mode with read, write, execute permissions),
			- use `-lrt` to sort by time,
			- use `-a` to show hidden files(start with`.`),
			- append absolute directory argument to print corresponding files,
		- `fasd`(sort directory by frequency)
		- `mkdir`(make directory/folder)
	- file
	  collapsed:: true
		- `<`, `>`(file redirect)
		  collapsed:: true
			- the file don't need to be created before,
			- use `> file` to add words to `file`, instead of printing on the screen,
			- use `< file` to read words from `file`, instead of the basic input(like keyboard),
			- `>>` could append words to the file,
		- mv(move), cp(copy), rm(remove),
		  collapsed:: true
			- `rm -rf` is able to delete folders,
		- `echo`is used to display content on STDOUT, while using `>` could add the content to file,
		- `cat` could read the file's content and display it on STDOUT,
		  collapsed:: true
			- `cat -n file` will add numbers before each line,
			- `head -10 file` will show first 10 lines,
			- `tail -10 file` will show last 10 lines,
		- `tar` compression command,
	- bat
	  collapsed:: true
		-
	- find
	  collapsed:: true
		- `find`and `fd` are used to find selected *files*,
			- basic syntax is `find directory -name 'file.c'`,
			- `find directory -name 'file.c' -exec command` could run the command for every file find,
		- `grep` is used to find the selected *content* in files,
			- basic syntax is `grep "content" /home/Code/file.c`,
	- pipeline
	  collapsed:: true
		- `|` will use first command's output as second command's input,
		- `||` run second command if first command report error,
		- `&&`run second command if first command success,
	- others
	  collapsed:: true
		- `df`print the storage information, `du -sh`print present directory's amount,
- command line advanced
	- process
	- terminal multiplexer(tmux)
	- alias
	  collapsed:: true
		- `alias ll="ls -lh"` use `ll` as `ls- lh`'s alias, `unalias ll`will disable this alias,
		- shell won't store alias by default, need to save it to bash file `.bashrc` manually to reuse the alias,
	- dotfiles(settings)
	- ssh(remote devices)
- git
-
- make
-
- [[C]]
- [[C++]]
- [[Science]]