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
- every URL has a unique numerical address like ( IP Address) - ( 190.0.0.5)
- even for us to remember its domains name like ( xyz.com )
- server's actual IP Address called domains or domain name system

###### Anatomy of a URL 
Sample URL : ```
```
https://admin.example.com:8080/api/users?id=123#profile
```
- PROTOCOL => https://
make secure and encrypted connection.

- SUB-DOMAIN => admin.
functionality than the main site.

- DOMAIN => example.com
main site targeting.

- PORT => :8080
specifies a non-standard network port.

- PATH => /api/user
specific resource being requested

- PEARMETERS => ?id=123
data sent to the server , which is a area for manipulation.

- FRAGMENT => #profile 
marker your browser and is not sent to the server.


###### The Lifecycle of a Web Request
when using URL rapid sequence of events happen;
- DNS Lookup
- HTTP Request 
- HTTP Response 
- Rendering & Execution ---> HTML to build ---> CSS to style ---> JAVASCRIPT to add interactivity & build final.


###### HTTP: The language of the web
- GET - retrieve data ( loading, fetching info )
- POST - send data to the server ( login forms, creating something )
- PUT/PATCH - update existing data 
- DELETE - remove data 
- OPTIONS - check what methods are allowed ( useful for recon )


###### Key status codes to remember 

| code             | Meaning           | what to investigate                                               |
| ---------------- | ----------------- | ----------------------------------------------------------------- |
| 200              | success           | unauthorized action succeed when it shouldn't have?               |
| 401 unauthorized | login required    | can you bypass this authentication?                               |
| 403 forbidden    | access denied     | is the server properly blocking access, or can you get around it? |
| 404 not found    | doesn't exist     | maybe there are valid paths on other endpoints within the server? |
| 500 server error | problem on server | do the error expose stack traces or other internal details?       |




###### Authentication 

- Cookies - server stores your session.
- JWT ( JSON WEB TOKEN ) - Carry your identity in the token.

**In one line**
- Cookies say " I have an ID, check me in your database."
- JWT says, " Hers's proof of who I am, no need to check storage."

###### Frontend vs Backend
**Frontend** - What you see ( UI in browser using HTML, CSS, Java script.)
**Backend** - Hidden server logic ( Handles data, rules, authentication. )

In simple way,
- Frontend - display
- Backend - decision + Data

**Inspecting Requests
- Open Browser ---> Right click ---> Inspect ---> Network Tab
     Like ;
     - Requests browser sends
     - Responses from server 
     - Headers, Cookies, Tokens

Entry- level of hacking view of how apps communicate.


###### APIs & other services;
- API - bridge between frontend and backend
- Instead of full webpages, it returns data ( usually JSON)

**EXAMPLE;**
Frontend asks ---> "Give user info "
API responds ---> { name: "xyz" , age: 22 }

**Others Ports & Services;**
80 ---> HTTP
443 ---> HTTPS
8080 ---> Alternate Web server 
27017 ---> MongoDB Database


> [!NOTE]
> Hacker Check these because hidden services = Potential Vulnerabilities

