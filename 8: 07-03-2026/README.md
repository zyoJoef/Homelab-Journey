<h1><b>07/03/2026</b></h1>

<p>I've been really looking to acquiring one of these tiny thin client PC due to how small they are, how energy efficient they are, and the fact that some or most of them are fanless. Though the challenge was getting my hands on one, since these tiny Dell Wyse 3040 gets sold out really quick (I guess that's how popular they are) and here's the specification of the one that I received:</p>

<ul>
  <li>Model : 15N365</li>
  <li>CPU : Intel Atom x5-Z8350 (1.44 GHz base, up to 1.92 GHz burst, Quad Core)</li>
  <li>LCD : 15.6" (1920 x 1080 Full HD)</li>
  <li>Graphic Chipset : Intel HD Graphics 400</li>
  <li>OS : Windows 10 Pro (64-bit)</li>
  <li>Memory : 2GB DDR3 RAM (Soldered)</li>
  <li>Disk : 16GB eMMC Flash (Soldered)</li>
  <li>I/O Ports : DisplayPort, Headset port, 4 USB ports and LAN</li>
</ul>

Here's some Youtube Video Tutorial that I based/reference on:
<br>
  <a href="https://youtu.be/OB51DoA43CI">Easily Install Pi-Hole using Diet Pi ! - Quick & Easy ! | Matthews Tech Hub</a>
<br>
  <a href="https://youtu.be/Zbg1M-u_l3w">Blocking Ads With a 15 Year Old Computer | Hardware Haven</a>
<br>
  <a href="https://youtu.be/9C7UGogyTWo">Do These CHEAP PCs Live Up To The Hype? | Hardware Haven</a>
<br>
  <a href="https://youtu.be/LADsGBvB_ns">Little Guys: Episode 2 Wyse 3040 | Cathode Ray Dude - CRD</a>
<br>
  <a href="https://youtu.be/tmYsT5dhi_E">Are $20 Thin Clients from eBay Worth It? Dell Wyse 3040 & HP T520 Review | Technically Unsure</a>
<br>
  <a href="https://youtu.be/8QTdW0Q8U3E">Building The "Ultimate" Router - PFSense + Pi-hole + PIVPN | Hardware Haven</a>
<br>
  <a href="https://youtu.be/oh2FUzAa5s8">Unbound + Pi-hole Setup Tutorial | WunderTech - CRD</a>

<h2>Why install Pi-hole into it?</h2>
<p>
  Govern that they're not powerful enough to run Windows 10 that they came along with. So I decided to turn it into a DNS Adblocker Server which it is somewhat capable of, by having DietPi as it's main OS (which is really lightweight). Although I had to reinstall the DietPi OS since I had an curl issue with it after messing something up in the setting again, but after it everything seem to work fine.
</p>

<h2>What are the services that you are running into it?</h2>
<p>The following are the services that I'm running:</p>
<ul>
  <li>Pi-hole</li>
  <li>Unbound</li>
  <li>Dietpi-Dashboard</li>
  <li>OpenSSH</li>
</ul>

<h2>Note</h2>
<p>
    I actually had trouble using this as DNS server on the MikroTik router switch that I have, since my other devices won't read nor detect the Pi-hole DNS Server IP Address, which is why I went into our ISP router settings and let it point to it as primary DNS sever and Google (8.8.8.8) as the secondary upstream DNS (although some website does take a while to load upon first loading), though I had to login as a superadmin on our ISP modem just to adjust it since upon using the credential written on the modem itself, it only gave a few options to tweak (though this might vary). 
</p>
