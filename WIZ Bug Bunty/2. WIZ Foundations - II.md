#### The Vulnerabilities That Matter


##### Insecure Direct Object Reference (IDOR)
- Accessing unauthorized data by changing IDs in URL/API due to missing permission checks.
     - Example:
         - Changing `order=123` to `order=124` shows another user's order details.





##### Server-Side Request Forgery (SSRF)
- forcing a server to make requests to internal/private resources due to poor URL validation.
    - Example step-wise:
        - Feature: Enter Image URL
        - Normal use: `https://example.com/pic.jpg 
        - Attack: `http://169.254.169.254/latest/meta-data`
        - Server fetches it internally ---> exposes cloud credentials ---> attacker gets sensitive data.
- Note:  not attacking directly; make the server attack itself for you.



##### Subdomain Takeovers
- Taking control of subdomain pointing to an unclaimed third-party service due to leftover DNA records.
     Example;
         `store.company,com` points to an unused AWS S3 bucket ---> attack registers that bucket ---> gains control of the subdomain.



##### Exposed Files & Leaked Secrets 
- Sensitive files or data accidentally left Public (e.g., backups, .env, API keys ).
    - Example;
        - Accessing /backup/ or finding API keys in a public GITHUB repo exposing private data.




##### Business Logic Flaws
- Exploiting weakness in how an app's workflow is designed ( not a code error ).
     - Example;
         - Apply s big discount to an expensive item, then reduce its quantity but keep the discount ---> get items almost free.




##### Exploiting 0-Days and Novel Misconfigurations
- Newly discovered vulnerabilities or misconfigurations exploited before systems are patched.
     - Example;
         - A new CVE ( Common Vulnerabilities and Exposures ) is released ---> attacker uses PoC to find unpatched servers and exploit them quickly.
- Note:  Speed matters --- whoever finds reports first wins.







---
---
### The Power of Community
*Start to learn and engaging from social media like X/Twitter list*
- [https://x.com/samwcyo](https://x.com/samwcyo) (Sam Curry) – Known for massive findings on companies like Apple and Uber

- [https://x.com/iangcarroll](https://x.com/iangcarroll) (Ian Carroll) – Known for high-impact findings in airlines, travel, and government systems

- [https://x.com/rhynorater](https://x.com/rhynorater) (Justin Gardner) – Host of Critical Thinking podcast, deep technical insights

- [https://x.com/NahamSec](https://x.com/NahamSec) (Ben Sadeghipour) – Educator, streamer, and founder of one of the largest bug bounty communities

- [https://x.com/Jhaddix](https://x.com/Jhaddix) (Jason Haddix) – Recon methodology legend, creator of essential wordlists

- [https://x.com/galnagli](https://x.com/galnagli) (Gal Nagli) - Myself! sometimes I post cool bug bounty stuff : )

- [https://x.com/pdiscoveryio](https://x.com/pdiscoveryio) – Project Discovery team, creators of Nuclei and other essential tools


*PODCASTS to listen to*
- [https://www.criticalthinkingpodcast.io/](https://www.criticalthinkingpodcast.io/) – Hosted by Justin Gardner and Joel Margolis. The most technical and methodology-focused podcast in the space.

- [https://www.youtube.com/@NahamSec](https://www.youtube.com/@NahamSec) – Available on YouTube, featuring interviews with top hunters and live hacking.

- [https://open.spotify.com/show/3yUhNMX8Y0Jrji1FPjlYkc](https://open.spotify.com/show/3yUhNMX8Y0Jrji1FPjlYkc) – Hosted by Fisher, featuring a wide range of hunter interviews.

- [https://darknetdiaries.com/](https://darknetdiaries.com/) – Hosted by Jack Rhysider. Not bug bounty specific, but incredible hacking stories that build context and motivation.


*Where to find Bug Bounty write-ups;*
 -  [https://hackerone.com/hacktivity](https://hackerone.com/hacktivity) – A live feed of publicly disclosed reports. Filter by severity and program to find gold.

- [https://medium.com/tag/bug-bounty](https://medium.com/tag/bug-bounty) – Many hunters post detailed write-ups. Following them on X is the best way to catch these when they drop.

- [https://portswigger.net/research](https://portswigger.net/research) – Deep technical research from the creators of Burp Suite.







---
---
### Building Your Hacking Machine

*Toolkit;*
1. Web Proxy 
   - Intercepts and modifies web traffic between browser and server.
     Example tools; Caido, Burp Suite
        - used to view requests, change parameters, test vulnerabilities.


2. Recon Tool
   - Discover target's assets ( subdomains, live servers ).
    Example tools; Subfinder, httpx
        - used to map full attack surface.


3. Fuzzing Tools
 - Burp-force hidden files, directories, and endpoints.
    - Example tool; ffuf
        - used for hidden paths like `/admin`, `/backup`.



#### Step-by Step Installation Guide
1. Install the Go programming language
   For Linux: `echo 'export PATH=$PATH:$HOME/go/bin' >> ~/.bashrc && source ~/.bashrc`
   For MacOs: `echo 'export PATH=$PATH:$HOME/go/bin' >> ~/.zshrc && source ~/.zshrc`
2. Configure Your terminal path
   For Linux: `echo 'export PATH=$PATH:$HOME/go/bin' >> ~/.bashrc && source ~/.bashrc`
   For MacOs: `echo 'export PATH=$PATH:$HOME/go/bin' >> ~/.zshrc && source ~/.zshrc`
3. Install Your core Command-Line Tools
   - Subdomain Discovery: SubFunder
    `go install -v github.com/projectdiscovery/subfinder/v2/cmd/subfinder@latest`
- HTTP Probing: HTTPX
    `go install -v github.com/projectdiscovery/httpx/cmd/httpx@latest`
- Vulnerability Scanning: nuclei
    `go install -v github.com/projectdiscovery/httpx/cmd/httpx@latest`
- Web Fuzzing: ffuf
    `go install github.com/ffuf/ffuf/v2@latest`
- Historical URL Discovery: gau     
    `go install -v github.com/lc/gau/v2/cmd/gau@latest`
4. Verify Installation
    `subfinder -version`
    `httpx -version`
    `nuclei -version`
    `ffuf -h`
    `gau --version`
5. Download First Wordlist
   `mkdir -p ~/wordlists && curl -o ~/wordlists/directory-medium.txt https://raw.githubusercontent.com/danielmiessler/SecLists/refs/heads/master/Discovery/Web-Content/DirBuster-2007_directory-list-lowercase-2.3-medium.txt`
   GitHub explore more wordlists `**https://github.com/danielmiessler/SecLists**` 
6. Install Web Proxy
     Download it from:https://caido.io`
7. Install Useful Browser Extension
    - Wappalyzer---> identify technologies used on websites.
    - FoxyProxy ---> easily troggle traffic through cadio or burp



   








