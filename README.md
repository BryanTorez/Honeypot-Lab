<h1>Honeypot Project</h1>


<h2>Description</h2>
This project consists of creating a trap for hackers attempting to steal valuable data, services, or systems. The trap's objective is to detect unauthorized activity or to learn more about an attacker or simply distract them. Today, I'll be walking you through on how you can spin up a collection of honeypots using T-Pot, an all-in-one, multi-arch honeypot platform. Features include 20+ honeypots and countess visualization options using the Elastic Stack, animated live attack maps, and lots of security tools to further improve the deception exprience. If you want to follow along I will be using a cloud provider called Vultr. Without further a do, let's begin...


<h2>Applications Used </h2>
Vultr Cloud Provider Website (https://www.vultr.com/)
T-Pot Honeypot Platform Github (https://github.com/telekom-security/tpotce)

<h2>Project walk-through:</h2>

<p align="center">
Create your free account with Vultr: <br/>
<br />
<img src="https://snipboard.io/dF07Vi.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Once you've created your account, you should see your dashboard. Next, put your cursor on 'Deploy+' and then click on 'Deploy New Instance'.:  <br/>
<br />
<img src="https://snipboard.io/gYdj5x.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
From here you have a couple of options that you can select. I'm just going to select 'Cloud Compute-Shared CPU' as that will cost the least amount of money. For the location you want to select the one that is closest to you: <br/>
<br />
<img src="https://snipboard.io/HVvRUG.jpg" height="100%" width="100%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
For the 'Choose Image' you want to select upload ISO and then you can drag and drop your already downloaded T-Pot ISO or you can paste it into a remote URL.  <br/>
<br />
<img src="https://snipboard.io/hDjUsi.jpg" height="100%" width="100%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/fQedYP.jpg" height="100%" width="100%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
I'll select the 160 gigs SSD because this will have four virtual CPUs and 8 gigs of memory and it will cost us $40 a month with the free $100 credit that you get from signing up with the link thats in my description that should be more than enough:  <br/>
<br />
<img src="https://snipboard.io/3j2wSV.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
<br />
For additional features, I'll go ahead and disable auto backups and IPv6 as well:  <br/>
<br />
<img src="https://snipboard.io/hxHPYr.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/miM0a1.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
Scrolling down, we have a firewall group that I'll create later on. For the server hostname, I am going to name this as 'MyDFIR-Honeypot and click on 'deploy now':  <br/>
<br />
<img src="https://snipboard.io/I3o7ml.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Now I already have a box that is running and I'll look at that later, but for the one that is being created you can see that it says 'installing'. After a couple of minutes you should see the status as 'running now' we can go ahead and click on our Honeypot:  <br/>
<br />
<img src="https://snipboard.io/yHoGPT.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/7kY1w4.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
If you take a look at the top right corner you will see a 'View Console'. That is what we're going to be using to interact with our Honeypot. Go ahead and click on 'View Console' and we get this screen:  <br/>
<br />
<img src="https://snipboard.io/YPcEjU.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/OsjZLo.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/bfcRXU.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
We'll go ahead and hit 'enter' on the first option and this will begin its setup. While this is setting up, let's create a new 'firewall group' for our Honeypot. The reason why we want to do this is because, in the beginning, we want to limit our IP to access the Honeypot. We don't want the entire internet to have access to our Honeypot until it is fully configured.:  <br/>
<br />
<img src="https://snipboard.io/bfcRXU.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/OPXwiH.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
To create a new firewall group we can click on 'Settings' and then at the left-hand side you should see 'Firewall' so we'll go and click on that and then click on 'Manage'.:  <br/>
<br />
<img src="https://snipboard.io/OPXwiH.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/6BKoUb.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/g2cLsH.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/dBPoHz.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
I already have a firewall group that I've created for my other box but we can click on '+Add Firewall Group' at the top right corner and then I'll name this as Honeypot and click on 'Add Firewall Group':  <br/>
<br />
<img src="https://snipboard.io/uY3t9j.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/FAnqYC.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
Again we want to only allow our IP to access our Honeypot. As for the protocol, it is currently set to 'SSH'. We can scroll up and select 'TCP'. For the port range, it is one colon to specify a range and then I'll type in '65535'. As for the source, you want to select my IP and what this rule will do is it will allow your IP to access your honeypot on any port. Then you want to click on the '+' button. Second to last, you want to add another one but this time you want to select 'UDP'. Put in the same ports and make sure you select my IP. Finally you hit the '+' button and now you should have two rules. One with the protocol 'TCP and 'UDP'. There is an automatic rule that was created that would do an explicit deny-all, and that is what we want.:  <br/>
<br />
<img src="https://snipboard.io/E8ioSG.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/MaEPxO.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/obgaZO.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/MaEPxO.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
Now that we have the firewall group. Let's go back into our Honeypot. We can do this by clicking on 'Compute' at the top left corner and then select your Honeypot. Under 'Settings', click on 'Firewall'. Finally for the drop-down, you want to select the one that you created. Mine was called 'Honeypot' so I'll go and select that and click on 'Update Firewall Group'. Now our firewall has been created and implemented onto our Honeypot and again this firewall group makes it so we are the only ones that can access our Honeypot for the time being.:  <br/>
<br />
<img src="https://snipboard.io/AS6M7v.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/1A3bDL.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/fbjexN.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/ulJZHi.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/cXB6qG.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/19OEmK.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/TWe5Dm.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
Now once we are done configuring the Honeypot we'll remove those rules and allow the internet to access it. Let's go ahead and click on 'View Console' again so you can select your location. I'll go ahead and just hit 'enter' on my location. Then select 'enter' on your keyboard so we can sit and wait for the auto-configuration.:  <br/>
<br />
<img src="https://snipboard.io/rtz5vo.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/Qhni9s.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/VfBn4w.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/iGy0Q2.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
Next, we need to select the country for the Debian archive. I'll select the 'United States'. Click on 'deb. debian.org'. Finally, if you need an HTTP proxy to access the outside world this is where we'll enter it. Now we don't have a proxy so I'll click 'enter'. When you get presented with the screen what you want to do is remove the iso image from your virtual machine and to do that under 'Settings' we can select 'Custom ISO' and click on 'Remove ISO'.:  <br/>
<br />
<img src="https://snipboard.io/gYfqMv.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/3ycZxk.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/GVSJF4.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/mY2gPk.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/PO3dom.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/C8G40i.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
It'll just say, "Hey are you sure you want to remove the attached image?". If you do, your server will be rebooted. To complete this process, I'll click on 'Remove ISO' and we get the message of the iso being removed from the machine. Let's go ahead and click on 'View Console' again and eventually, you get presented with this screen where it asks you to choose your T-Pot Edition. There are multiple editions that you can select but in this demo I'm going to select standard. Standard will include everything you need. We'll go ahead and hit 'enter' and now it's asking us for a password:  <br/>
<img src="https://snipboard.io/XKxzns.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/ACfStI.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/hInCqD.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/p40uXw.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
I know it's kind of hard to see but the username is 'tsec' all lowercase and then you want to enter in your password this can be anything you want. Now we'll need to repeat the password hit 'enter'. Enter your web username and we cannot use 'tsec'. So for my username, I'll just type in 'Steven'. Finally enter your password again. Perfect. T-Pot is going to install all its dependencies and eventually, it'll instruct us on how we can access T-Pot.:  <br/>
<br />
<img src="https://snipboard.io/ZwdNDB.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/dEGDVm.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/UTrWBm.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/SqIcGs.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
While we wait for T-Pot to be installed, I wanted to show you their GitHub page. This includes a lot of documentation that you can take a look at if you ever encounter any issues or if you want to learn more about T-Pot. Scrolling down, we see that T-Pot is an all-in-one Honeypot platform supporting over 20+ honeypots. It has a lot of visualization options which is quite nice along with animated live attack maps. Scrolling down we have the table of contents. This includes your requirements, how you can download it, install it, what to do when you first start, and how you can access it.: https://github.com/telekom-security/tpotce <br/>
<br />
<img src="https://snipboard.io/oxTfNi.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/kxCFjl.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/MrcA0U.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
The most important important thing is the required ports. We need to make sure that we have the following ports enabled for our Honeypot to work.:  <br/>
<br />
<img src="https://snipboard.io/6485Pz.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Going back over to our console, we now see that T-Pot is successfully installed. Now I know it is hard to see but right above the log-on prompt, we have information about our honeypot. So first, we have the SSH, IP, and Port number of our Honeypot. Next, is the web, so we can use this IP and port to connect over to the 'Web Server'. Lastly, we have the 'Admin'. We can use the IP and port to access the 'Admin Portal' for this Honeypot:  <br/>
<br />
<img src="https://snipboard.io/NUfzyA.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
Now let's access the web portal which is the one above admin. Your IP is going to be different than mine so make sure that you type in your correct IP and port. In my case, it is going to be '216.128.185.215', on port, '64297'. Now you will get the 400 bad requests page if you do not specify 'https', so let's do that.:  <br/>
<br />
<img src="https://snipboard.io/fQqLGZ.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/IqWsz9.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/vzGadE.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/gcn1x9.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/0MtdTj.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Now we get, 'Your connection isn't private'. Go ahead and select 'Advance' and we'll continue to this IP. You want to use the username and password that you created during the setup. My username was Steven and then I'll enter in my password and now we're on the homepage of T-Pot:  <br/>
<br />
<img src="https://snipboard.io/u2rlWS.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/3uXiyc.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/1pLjte.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/igqsob.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
There is a lot of information here and very quickly on the left we have the 'Attack Map". Next is the Cockpit which is your admin panel to manage T-Pot. Then you have 'Cyberchef' which is a Swiss Army tool that can be used for various purposes. Next to last, you have 'Elasticvue', which is a web goey for elastic search. 'Kibana' is where you can query data and create visualizations. Lastly, 'Spiderfoot', this is a huge collection of ENT tools that you can use to find out more information:  <br/>
<br />
<img src="https://snipboard.io/hT8k6F.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
The main options that we'll be using are Kibana and the attack map. So first let's go ahead and click on 'Attack Map'. This is what we see in real time. Now we don't see any information here. That is because our firewall is blocking all of the inbound access and only I can access our honeypot. So we're going to modify our firewall rule and remove that. Make sure you're under your Honeypot and then go under 'Settings'. Go to firewall. Click on 'Manage'. You want to select your correct firewall in my case it is called 'Honeypot'.:  <br/>
<br />
<img src="https://snipboard.io/hHjicB.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/1yMpWx.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/aUP7fg.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/hOBkIT.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
We want to create a new rule. So we want to enable 'TCP' as the protocol and the port range is going to be '64294: 64297'. We want to have the source as my IP and then hit '+'. We want to remove the two rules that we created from the beginning which allowed only our IP to access the Honeypot. So I'll go ahead and remove that. It'll ask you, "Are you sure you want to delete this firewall rule?" Click 'Delete Firewall' and do the same for the other one.:  <br/>
<br />
<img src="https://snipboard.io/UjZP1J.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/PSR3o8.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/0vQ4xc.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/Wd04VD.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Once those two rules have been deleted, we need to read add those two rules but this time instead of selecting your IP you want to select, 'Any'. So we'll go ahead and select 'TCP' and put in the port range of '1:65535'. Select Source as 'Anywhere'. Click on the '+'. I'll just do the same for 'UDP' with the port '1:65535'. The source is set to 'Anywhere'. We should have a total of three inbound ipv4 rules that we've created. The first two are to allow any IP addresses coming inbound to our Honeypot using both protocols TCP and UDP. The third rule will allow our IP to access our Honeypot using 'TCP; with the port range of '64294-64297'. :  <br/>
<br />
<img src="https://snipboard.io/QZutpi.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/OXjpgy.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/fiBsIo.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/B3Rt69.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Now that we've updated these rules. We can go back over to our attack map. We automatically see additional information. At the bottom right, we can see the time that this event occurred, what IP it generated from, the country, and what Honeypot captured that information along with its service. Finally, on the left, we can see the top hits:  <br/>
<br />
<img src="https://snipboard.io/ldRI2i.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
So currently, we only see information sourcing from the United States. Now if it came from a different country such as China, we would see that here as well. From that, you see a nice count of the IPS. On the very left. we can see the color associated with the service. We can simply highlight any of these dots on the map. Click on it and it will show us the IP address. Notice it has a classification of known attackers. I think that's pretty cool I'll leave this on for a couple of minutes.:  <br/>
<br />
<img src="https://snipboard.io/ldRI2i.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/IJ59le.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Let's head over to Kibana. In Kibana, we have a lot of dashboards that we can select. If we go back over to the attack map, notice that the Honeypot that was used is called 'Honeytrap'. Going back over to Kibana, we can look for 'Honeytrap' and select its dashboard since we know for a fact that there should be data there.:  <br/>
<br />
<img src="https://snipboard.io/N6mj5R.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/ots4Bj.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
While we wait for this dashboard to be populated with data, we can query for data if you want. By selecting the hamburger icon at the top left, you want to select "Discover' under this tab you can practice your query skills and learn how to use Kibana:  <br/>
<br />
<img src="https://snipboard.io/Oed60P.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/d2YtDk.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/kxGz8P.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
Overall this is a fantastic way to gain hands-on experience. For example, I can go ahead and expand the first event. On the right-hand side, we can get a list of all of the fields and their field value. Now let's just say I am interested in the destination IP. I can highlight these icons to see what they mean. We can 'Filter for the value', 'Filter out the value', 'Filter for field present', 'Toggle column and table' and finally 'Pin the field'. I'll click on the 'Toggle column in table' icon. By doing so, our table automatically added the destination IP field. Now this is a much cleaner view for us to take a look at. You can add more columns to your table and this will help you with your analysis.:  <br/>
<br />
<img src="https://snipboard.io/kxGz8P.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/M9qr8G.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/JDfzVs.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/x1maGO.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/zC8OkS.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/creTZq.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/LwBIEh.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/5SGrXo.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/5sk691.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Heading back over to our 'Honeytrap' dashboard. We finally get some events. So we see that there are seven total attacks with seven unique Source IPS. If we scroll down, we see the attacks by ports. We also see the attacks by country. So far, it is all coming from the United States. We have the IP reputation, which is for known attackers. At the bottom, we have the 'ASN'S' and on the right, we get the source IP. The cool thing about T-Pot is that you can click on the source IP and it'll check its IP reputation. We can see that the sender IP reputation is currently set to 'Poor'.:  <br/>
<br />
<img src="https://snipboard.io/HLQzjo.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/FInAzV.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/Qci4bP.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/0L5UxA.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/k2J9ay.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/iYTgD3.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/Ut2IfP.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
Let's head back over to our attack map. Look at that; we see a lot more countries. It looks pretty fancy. We see that there are Portugal, Turkey, Bulgaria, and Brazil. :  <br/>
<br />
<img src="https://snipboard.io/H8eaXI.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/bpoDVs.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Now I left this for a couple of days and this is what we see here. Looking at the same 'honeytrap' we have 6,583 attacks with 1,485 unique Source IPS's. We can see that the attacks were coming from all over the world. Scrolling down, we can see a nice little heat map which is pretty cool. Looking at the IP reputation, the majority of it was from a known attacker. The second is a mass scanner. The third is a bot/crawler. Lastly you have your 'Attacks by Country'. Looking at the countries, the top one is the United States followed by the United Kingdom and then Italy:  <br/>
<br />
<img src="https://snipboard.io/b0ucad.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/2VQTzc.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/vqib5t.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/ba0L45.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/EkV0Zc.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/bkdcje.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
So a Honeypot is pretty cool to spin up and it can collect a lot of interesting information. I do recommend that you practice with Kibana queries because this will not only help you build confidence but familiarity with the query language. Again overall, a fantastic way to gain hands-on experience. Honeypots are pretty cool. It can provide you a quick glimpse of what the internet is currently doing but at the end of the day you'll quickly find out that everybody is just scanning everybody.:  <br/>
<br />
<img src="https://snipboard.io/QEOyZV.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
