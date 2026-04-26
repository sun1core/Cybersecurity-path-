- to find and report security vulnerabilities in their system.

###### The report submission process
- chose a program & read the rules 
- hunt for vulnerabilities
- write a high-quality report 
- triage and validation
- remediation & reward


### Terminal
- Navigating your file system 
```
mkdir {folder-name}
mkdir bug-bounty-learnpath
```
make a new directory with the mkdir command.

- Change Directory 
```
cd {folder-name}
cd bug-bounty-learnpath
```

- PWD (print the current directory) to know exactly where am i 
```
pwd
```

- ls list all files and directories in detail.  (current location)
```
ls -la
```

- to backup one level in directory 
```
cd {target directory}
cd .. {move one directory up}
```

- creating and editing files 
first, 
```
nano notes.txt
```
then, 
open a new screen create a new note nano.txt file with in the directory. press ctrl+ O and enter to save, and ctrl+ X to exit.  

- Viewing and organizing files
```
cat {file-name}
cat notes.txt
```

- make a copy of file (CP) 
```
cp notes.txt notes2.txt
```

- move or rename a file (MV)
```
mv notes2.txt final-notes.txt
```

- Searching & chaining commands 
```
ls > file_contents.txt
cat notes.txt | tee notes-backup.txt
```

- grep - to search for text 
```
cat notes.txt | grep "sun1core"
```

- head command 
files will be huge a lot of content for that reason we used head command where we can specify the number of rows we want to check from a given a file
```
cat {file-name} | head -n {number-of-lines}
cat notes.txt | head -n 1 (Show me only the first line from my notes.txt file)
```

- |  (PIPE) /  && (AND OPERATOR)  ---- used it for command flow 
runs the next command after the first one finishes successfully.
```
mkdir new-folder && cd new-folder 
(create "new-folder" and then navigate to it by changing directory)
```


### KEEPING SESSIONS ALIVE WITH TMUX
=> running long recon scans or working on a remote server, loosing your terminal session can mean losing hours of work. 
That's why it keeps your session running even if you close your terminal or lose connection.

```
tmux new -s hunting 
```
it creates a new session hunting. Even it can run tools if i disconnect every things keep running in the background 


- To detach from a session  ( leave it running )  Ctrl+ B, then D, 
- to reattach later 
```
tmux attach -t hunting
```

-  to see all running sessions 
```
tmux ls
```

> [!NOTE]
> Pro Tip: running a long subdomain enumeration or port scans, always run them inside tmux. 



### WEB APPLICATION BASICS 
