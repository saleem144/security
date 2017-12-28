





Information Gathering & Enumeration



Bypass Cloudflare

First thing you should do is to check if the website is using cloudflare or not, and if does then bypass it. Finding the real IP address is necessary and will help us in further exploitation.



Recommended Tools: CloudFail



Find Subdomains

Finding subdomains of the target website is crucial. What if there a sudomain dev.example.com which is being used by the developers of the website to test new features? Maybe you can find a command injection vulnerability there can and pawn the whole server.



Recommended Tools: Sublist3r



DNS, Whois & Reverse IP Lookup

The next step should be dumping the DNS related data like name servers and mail servers. You can also try zone transfer if you see port 53 on a server.



Whois info can also reveal a lot about the target, especially information that can help us in the social engineering phase.



You should also do reverse IP lookup which will give you the list of websites hosted on the same server so if you fail to hack the target website, then you can hack any other websites hosted on that server and then gain access to the server.



Recommended Tools: dnsdumpster.com, dnsenum, YouGetSignal, whois.net



Information Gathering about the Organization

Find as much as information you can about the organization who owns the website. Ranging from their partners in business to the email addresses of their employees. Linkedin is a great resource to find and learn about the employees. The more information you have about the organization, the better your social engineering approaches will be.



Recommended Tools: theHarvester, Maltego, Google



Port Scanning

Do a port scan to have an idea about what services are running on the server, save the results for reference in further exploitation.



Recommended Tools: NMap



Web Technology Detection

Modern websites are very complex and they use a lot of web technologies like various JavaScript libraries, plugins, content management systems, frameworks and what not. For a hacker, it is very important to know what kind of web technologies are in use for further exploitation.



Recommended Tools: builtwith.com, wpscan, whatcms.org



WAF/IPS Detection

Its advised to detect if a WAF/IPS is in place in the early stage because don’t want to wonder why your payloads aren’t working. The common method is to inject a noisy payload in some input box or parameter and watch the result, the access denied message often reveals the underlying WAF.



Recommended Tools: wafw00f



Robots.txt & Hidden Directories

Robots.txt is a file which contains the list of paths that the web developers don’t want the crawlers to find. In simple words, the contain that stuff which should not be found through search engines.

Brute forcing for common paths is also a good idea as you might get some hidden directories. Finding admin panels may also come handy for testing of login related issues or in case you get the credentials via social engineering.



Recommended Tools: dirsearch, Breacher



Using Exploits



What are the web technologies in use? What plugins are being used? What CMS is being used? Are they outdated? If yes, use vulnerability databases and google to find an exploit.



Recommended Tools: Google, exploit-db



Missing Pieces of the puzzle



Missing pieces of the puzzle? What does that means? Well these are the issues that can help you while exploiting other vulnerabilities. 





HTTP Headers

Do you know if x-frame–options header is missing we can do click jacking on the website? Similarly, there are other security vulnerabilities related on the HTTP headers and they can cause a lot of damage when chained with another severe vulnerabilities. Some headers misconfiguration can help you to bypass security restrictions.



Recommended Tools: None



Errors & Information Disclosure

Errors can give a lot of information about the configuration of the back end like what database management system is in use. It is also common for web apps to throw full path of the file in the error messages which can come in handy in further exploitation.



Recommended Tools: None



Exploiting Parameters & Forms



How do a website gets input from the users? Websites use mainly use GET & POST method to get input from user. Take a look at this  GET request:



https://example.com/gallery.php?this-is-a-parameter=and-this-is-its-value



As parameters are a way of submitting a data, there are a lot of attack vectors related to them. Website may also use forms run by JavaScript or JQuery and in that case you won’t be able to see the parameters but of course you are sending the data to the backend.



XSS & HTML Injection

XSS is one of the most common vulnerabilities. It doesn’t have a high risk factor but its impacts can be hazardous depending on the configuration of the webapp. XSS & HTML injection are very popular among bug hunters.



Recommended Tools: XSStrike \(Prefer manual injection\)



Database Injection

Database injection vulnerabilities are like a treasure for a hacker. You should have knowledge of how different databases and DBMS work in order to exploit them.



Recommended Tools: Prefer manual injection, SQLmap, NoSQLmap



Command Injection

Why check for other vulnerabilities if you can run system commands on the web server? Common sense and knowledge of command line is all you need to exploit command injection vulnerabilities.



Recommended Tools: Commix



Open Redirection & Server Side Request Forgery \(SSRF\)

If a parameter or input form takes a URL as input, you must check for SSRF and open redirect vulnerability.



Recommended Tools: None



Application Specific Attakcs



There are some attacks which are application/technology specific like LDAP injection, SSI injection, XML injection, XPath injection etc. Perform tests for them whenever possible.



Recommend Tools: None



Logic Based Attacks



What do I mean by logic based attacks? Well these are those attacks or techniques which can’t be automated and need to be done by a human. There are no tools for that.



Cross Site Request Forgery \(CSRF\)

C is something which is found in many variations. Missing security policies and XSS can be used to bypass CSRF protection.



Insecure Direct Object Reference \(IDOR\) vulnerabilities

How these complex web apps distinguish between users, products etc.? They assign a value to it and if the HTTP request contains that value then its possible for an attacker to modify it.



Other Stuff

Let me tell you a real story. When I was a kid, I was fond of a local sweet. 2 sweet pieces came in a packet and there used to be a  chit in the packet having an item name written on it. After eating the sweet, we would show the chit to the shopkeeper and he would give the mentioned item. A lot of items were in scope but I wanted the superhero mask. So I asked the shopkeeper one day, What my chit should be in order to get that mask? He said, “Mukhauta” \(Hindi word for Mask\). Why I did that? Because that chit used to be hand written and I could have written it myself if I can find the exact same paper \(that paper was more like a cardboard\). I found the same material, the inside part of a matchbox. I careful cut it and wrote Mukhauta on it. I went to the shop and purchased the sweet, ate it and then submitted my chit to the shopkeeper and got a superhero mask.



Thats it. There are no names for logic based attacks. You can exploit anything, just anything. It depends on your understanding of web apps and creativity.



Files? Gotcha.



LFI & RFI attacks

If the HTTP request includes a file path/name either from remote address or the web server itself then you must test for RFI and RFI. You can get a web shell with RFI easily. On the other hand, LFI can be used to view files on the web server and you can run system conditions if proper security measures are not in place.



Recommended Tools: LFISuite



Unrestricted File Upload

Does the website have a file upload form? Great. You can check if the website checks the extension of the file properly or not. For example, if a website lets the users upload a profile picture for their account, the attacker will try to upload a web shell spoofed as an image and if proper checking mechanism is not in place, the website will get compromised through that web shell.



Recommended Tools: Iron Man Suit



Other Stuff

There are many attacks and vulnerabilities related with file uploads like persistence of metadata, XXE attack, XSS through file upload etc. Its up to you to check for them. Good luck.



Recommended Tools: None



Authorization Issues



Can you bypass the login panel with malicious strings?



Are you able to access web pages you should be allowed to view without authorization?



Do the session id has a weak value? Like a user name or small number which can be bruteforced?



Is there any rate limiting on the login page to stop bruteforcing?

Ref : teamultimate

Do the cookie expire when the user logs out?



Other Web App Attacks



There are a lot of other attacks like HTTP response splitting, header injection, subdomain takeover, page takeover, path transversal, SMTP Injection etc.



Social Engineering Based Attacks



If you did proper information gathering, you can target employees of the organization and pivot your way or can hack the administrator of the website himself. Phishing, vishing, water hole attack, malicious email attachments…..possibilities are endless.



Rest of The Attack Surface



So you failed to hack the website? Don’t worry. Pick one website hosted on the same server and try to gain access to it so you can further exploit your way till you get root access on the server. As the whole server is under your control, you can play with the target website too.



Open your port scan results and see if you can exploit the services running on the service.



Apart from these you can do a lot of things like this one. And don’t forget to test all the subdomains, you never know when you hit the G-spot \*coughs\* I mean the right spot

