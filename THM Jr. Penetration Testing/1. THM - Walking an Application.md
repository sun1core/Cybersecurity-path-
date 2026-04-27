*Note: Manually review a web application for security issues using only your developers tools. Hacking with Just Browser, no tools or scripts.*

- View source - see the website's raw code ( HTML )
- Inspector - Examine & edit page elements ( HTML/CSS )
- Debugger - Analyze and control JavaScript execution 
- Network - Monitor all requests between browser & server.


---

##### Viewing the page source 

- Look for HTML comments
    
    <!-- something here -->
    
    In Try Hack Me, flags are often hidden here
    
- Comments can include:
    - Notes
    - Hidden links
    - Flags (THM{...})

### What to do:

- Right-click → View Page Source
- Search (`Ctrl + F`) for:
    - `<!--`
    - `http`
    - `href`


### Key things to look for in Page Source:

- Hidden links in comments
    - Example: link starting with `"secr"`
    - Open it → flag is there


- Directory listing vulnerability
    - If files (CSS/JS/images) are in a folder:  
        Open the folder URL directly
    - If listing is enabled → you’ll see all files
    - Look for:
        - `flag.txt`
        - backup files
        - hidden data


- Framework info (very important)
    - Check bottom comments for:
        - Framework name
        - Version
    - Then:
        - Visit its official site
        - Look for update/vulnerability info
        - That info leads to the flag


---
How did I solve problems? 
1. ---> first visit given page 
then, Right click after view page source
in the above HTML comment at above as i find it comment < !---..........@ /new-home-beta--- >
add in back link and find answer => THM{HTML_COMMENTS_ARE_DANGEROUS}

2. 2nd answer was in welcome page found it over here. => THM{NOT_A_SECRET_ANYMORE}     ```<p class="welcome-msg">Our dedicated staff are ready <a href="[/secret-page](https://10-48-172-4.reverse-proxy.cell-prod-ap-south-1a.vm.tryhackme.com/secret-page)">to</a> assist you with your IT problems.</p>

3.  The given link of VM link as i was adding over in link /assets in the home page. => THM{INVALID_DIRECTORY_PERMISSIONS}
4. visit the webpage framework and added it /tmp.zip after it downloaded file with their flag.txt  => THM{KEEP_YOUR_SOFTWARE_UPDATED}

---
---
#### Developer tools - inspector 
In this section as i have solve it by 
-contact us 
-then [Inspect] 
-after inspect in display: block change into ----> display: none

This is the remove [paywall] by changing.
=> THM{NOT_SO_HIDDEN}

---
---
#### Developer Tools - Debugger
- Analyze and pause JavaScript.
- Helps find hidden or date in web page.

[ Process: ]
1. open developer tools
right-click ---> Inspect 
2. chrome ---> sources
  Firefox/safari ---> debugger
  3. find the JavaScript file 
  Left panel ---> open assets ---> click flash.mini.js
  4. make code readable 
 click pretty print {} to format code 
 5. Locate important code 
  scroll down --> find:
 ``` flash['remove']();```
 this removes the red popup.
 6. Sets a breakpoint 
 click the line number ---> it turns blue
 7. Refresh the page 
  page pauses execution at that line
  8. Observe Result 
  Red box stays visible ---> reveals hidden flag



> [!NOTE]
>stop JavaScript before it hides something, so you can see hidden content.


---
---
#### Developers Tools Network 

- shows all requests a webpage sends/receives
- Helps you see hidden data, APIs, and form submissions

---

Step-by-Step Process

1. Open Developer Tools
    - Press `F12` ---> go to Network tab
2. Refresh the page
    - You’ll see all requests (HTML, JS, CSS, APIs)
3. Clear clutter (optional)
    - Click (trash icon)
4. Perform an action
    - Fill the contact form ---> click Send Message
5. Find the new request
    - Look for a new entry (usually XHR / Fetch)
6. Click the request
    - Inspect details:
        - Headers (URL, method)
        - Payload (data sent)
        - Response (server reply)
7. Open the request URL
    - Visit it directly (if possible)
8. Check response
    - Hidden info (like flag) appears there


> [!NOTE]
> Even if the page doesn’t show something, the server still sends it—you just catch it in Network tab.

