# Disable Lid Suspend

In terms of using a laptop as a Debian Server

<h2>Steps to Disable Lid Suspend</h2>
<ol>
  <li>Open a terminal and edit the configuration file with root privileges using a text editor like nano: 
    <pre><code>sudo nano /etc/systemd/logind.conf</code></pre></li>
  <li>Locate the following lines (they might be commented out with a # symbol at the beginning):
    • HandleLidSwitch=suspend
      <br>
	  • HandleLidSwitchDocked=suspend (or ignore)
      <br></li>
  <li>Remove the # character at the beginning of these lines and change suspend to ignore so they look like this:
    <pre><code>HandleLidSwitch=ignore</code></pre></li>
    <pre><code>HandleLidSwitchDocked=ignore</code></pre></li></li>
  <li>Save the file. In nano, press Ctrl + X, then Y, and hit Enter.</li>
  <li>Restart the systemd-logind service to apply the changes immediately:
    <pre><code>sudo systemctl restart systemd-logind</code></pre></li>
</ol>
