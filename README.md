<h1>Honeypot Project</h1>


<h2>Description</h2>
This project consists of creating a trap for hackers attempting to steal valuable data, services, or systems. The traps objective is to detect unauthorized activity or to learn more about an attacker or simply distract them. Today, I'll be walking you through on how you can spin up a collection of honeypots using T-Pot, a all in one, multiarch honeypot platform. Features include 20+ honeypots and countess visualization options using the Elastic Stack, animated live attack maps and lots of security tools to further improve the deception exprience. If you want to follow along I will be using a cloud provider called vultr. Without a futher a do, lets begin...


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
For the 'Choose Image' you want to select upload ISO and then you can drag and drop your already downloaded T-Pot ISO or you can paste in a remote URL.  <br/>
<br />
<img src="https://snipboard.io/hDjUsi.jpg" height="100%" width="100%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/fQedYP.jpg" height="100%" width="100%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
I'll select the 160 gigs SSD because this will have four virtual CPUs and 8 gigs of memory and it will cost us $40 a month and with the free $100 credit that you get from signing up with the link thats in my description that should be more than enough:  <br/>
<br />
<img src="https://snipboard.io/3j2wSV.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
<br />
For additional features, I'll go ahead and just disable auto backups and IPv6 as well:  <br/>
<br />
<img src="https://snipboard.io/hxHPYr.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/miM0a1.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
Scrolling down, we have a firewall group that I'll create later on. For the server host name, I am going to name this as 'MyDFIR-Honeypot and click on 'deploy now':  <br/>
<br />
<img src="https://snipboard.io/I3o7ml.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Now I already have a box that is running and I'll take a look at that later, but for the one that is being created you can see that it says 'installing'. After a couple minutes you should see the status as 'running now' we can go ahead and click on our Honeypot:  <br/>
<br />
<img src="https://snipboard.io/yHoGPT.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/7kY1w4.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
Now we can go ahead and click on our Honeypot and if you take a look at the top right corner you will see a view console. That is what we're going to be using to interact with our Honeypot. Go ahead and click on view console and we get this screen:  <br/>
<br />
<img src="https://snipboard.io/YPcEjU.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/OsjZLo.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/bfcRXU.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
We'll go ahead and hit enter and this will begin its setup. While this is setting up, let's create a new firewall group for our Honeypot and the reason why we want to do this is because in the beginning we want to limit our IP to access the Honeypot. We don't want the entire internet to have access to our Honeypot until it is fully configured:  <br/>
<br />
<img src="https://snipboard.io/bfcRXU.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/OPXwiH.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
To create a new firewall group we can click on settings and then at the left hand side you should see firewall so we'll go and click on that and then click on manage:  <br/>
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
I already have a firewall group that I've created for my other box but we can click on ADD firewall group at the top right corner and then I'll name this as Honeypot and click on ADD firewall group:  <br/>
<br />
<img src="https://snipboard.io/uY3t9j.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/FAnqYC.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
Again we want to only allow our IP to access our Honeypot as for the protocol it is currently set to SSH we can scroll up and select TCP for the port range it is one colon to specify a range and then I'll type in 65535 and as for the source. You want to select my IP and what this rule will do is it will allow your IP to access your honey pod on any port and then you want to click on the plus button then you want to add another one but this time you want to select UDP put in the same ports and make sure you select my IP and then you hit the plus button and now you should have two rules one with the protocol TCP and UDP. There is an automatic rule that was created that would do an explicit deny all and that is what we want.:  <br/>
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
Now that we have the firewall group. Let's go back into our Honeypot. We can do this by clicking on compute at the top left corner and then select your Honeypot under settings click on firewall and finally for the drop down you want to select the one that you created now ours was called Honeypot so I'll go and select that and click on update firewall group. Now our firewall has been created and implemented onto our Honeypot and again this firewall group makes it so we are the only ones that can access our Honeypot for the time being:  <br/>
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
Now once we are done configuring the Honeypot we'll remove those rules and allow the internet to access it. Let's go ahead and click on view console again so we see the select your location. I'll go ahead and just hit enter and then select your keyboard yeah that's correct and then it'll just do its thing so we can just sit and wait:  <br/>
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
next we need to select the country for the Debian archive I'll just select United States and then the Debian archive mirror says usually deb.debian.org is a good choice and that is the default so I'll hit enter and finally if you need a HTTP proxy to access the outside world this is where we'll enter it now we don't have a proxy so I'll just click on enter when you get presented with the screen what you want to do is remove the iso image from your virtual machine and to do that under settings we can select custom ISO and click on remove ISO:  <br/>
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
It'll just say hey are you sure you want to remove the attached image if you do your server will be rebooted to complete this process I'll click on that and we get the message of iso removed from machine let's go ahead and click on view console again and eventually you get presented with this screen where it asks you to choose your teot Edition there are multiple editions that you can select but in this demo I'm going to select standard standard will include everything you need we'll go ahead and hit enter and now it's asking us for a password:  <br/>
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
I know it's kind of hard to see but the username is TC all lowercase and then you want to enter in your password this can be anything you want and now we'll need to repeat the password hit enter enter your web username and we cannot use Tac so my username I'll just type in Steven is this your username yes it is and finally your password enter it again and perfect toot is going to run install all its dependencies and eventually it'll instruct us on how we can access toot:  <br/>
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
While we wait for T-Pot to be installed I wanted to show you their GitHub page because this includes a lot of documentation that you can take a look at if you ever encounter any issues or if you wanted to learn more about teapot scrolling down we see that teapot is the all-in-one multi- Honeypot platform and it really is I mean it supports over 20 plus honeypots and it has a lot of visualization options which is quite nice along with an animated live attack Maps AKA your pew pew maps. Scrolling down we have the table of content so this can include your requirements how you can download it and install it what to do when you first start and how you can access it: https://github.com/telekom-security/tpotce <br/>
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
The most important important thing is the required ports. So we need to make sure that we have the following ports enabled for our Honeypot to work.:  <br/>
<br />
<img src="https://snipboard.io/6485Pz.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Going back over to our console we now see that teapot is successfully installed now I know it is hard to see but right above the log on prompt we have information about our honeypot. So first we have the IP of our Honeypot and then we have the SSH along with this IP and Port that we can use to connect. Next is the web so we can use this IP and port port to connect over to the web server and lastly we have the admin we can use the IP and port to access the admin portal for this Honeypot:  <br/>
<br />
<img src="https://snipboard.io/NUfzyA.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
Now let's access the web portal which is the one above admin. Your IP is going to be different than mine so make sure that you type in your correct IP and port. In my case it is going to be 216.128.185.215, on port, 64297. Now you will get 400 bad requests if you do not specify 'https', so let's do that.:  <br/>
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
Now we get your connection isn't private. Go ahead and select advance and we'll continue to this IP. You want to use the username and password that you created during the setup. My username was Steven and then I entered my password and now we're on the homepage of T-Pot:  <br/>
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
There is a lot of information here and very quickly on the left we have the Attack Map. Next is the Cockpit which is your admin panel to manage T-Pot. Then you have Cyberchef which is a Swiss Army tool that can be used for various purposes. Next to last, you have Elasticvue, which is a web goey for elastic search. Kibana is where you can query data and create visualizations. Lastly, Spiderfoot, this is a huge collection of ENT tools that you can use to find out more information:  <br/>
<br />
<img src="https://snipboard.io/hT8k6F.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
the
11:32
The main options that we'll be using is Kibana and the attack map. So first let's go ahead and click on Attack Map. This is what we see in real-time. Now we don't see any information here. That is because our firewall is blocking all of the inbound access and only I can access our honeypot. So we're going to modify our firewall rule and remove that. Make sure you're under your Honeypot and then go under settings. Go to firewall, click on manage, you want to select your correct firewall in my case it is called Honeypot.:  <br/>
<br />
<img src="https://snipboard.io/hHjicB.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/1yMpWx.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/aUP7fg.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/hOBkIT.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
:  <br/>
<br />
<img src="https://snipboard.io/1yMpWx.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
:  <br/>
<br />
<img src="https://snipboard.io/hxHPYr.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
:  <br/>
<br />
<img src="https://snipboard.io/hxHPYr.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
:  <br/>
<br />
<img src="https://snipboard.io/hxHPYr.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
:  <br/>
<br />
<img src="https://snipboard.io/hxHPYr.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
:  <br/>
<br />
<img src="https://snipboard.io/hxHPYr.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
:  <br/>
<br />
<img src="https://snipboard.io/hxHPYr.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
:  <br/>
<br />
<img src="https://snipboard.io/hxHPYr.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
:  <br/>
<br />
<img src="https://snipboard.io/hxHPYr.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
:  <br/>
<br />
<img src="https://snipboard.io/hxHPYr.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
:  <br/>
<br />
<img src="https://snipboard.io/hxHPYr.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
:  <br/>
<br />
<img src="https://snipboard.io/hxHPYr.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
:  <br/>
<br />
<img src="https://snipboard.io/hxHPYr.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
:  <br/>
<br />
<img src="https://snipboard.io/hxHPYr.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
:  <br/>
<br />
<img src="https://snipboard.io/hxHPYr.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
:  <br/>
<br />
<img src="https://snipboard.io/hxHPYr.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
:  <br/>
<br />
<img src="https://snipboard.io/hxHPYr.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
:  <br/>
<br />
<img src="https://snipboard.io/hxHPYr.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/miM0a1.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
