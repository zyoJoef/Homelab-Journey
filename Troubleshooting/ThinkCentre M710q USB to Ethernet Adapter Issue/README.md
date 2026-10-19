<h1>Lenovo ThinkCentre M710q USB to Ethernet Adapter Issue</h1>
  <p>
    Following the issue with the internal NIC or Ethernet of my recently bought <b>Lenovo ThinkCentre M710q Mini PC</b> on debian which forced me to temporarily run it on Wi-Fi, 
  but then made me firm with using it with a USB to Ethernet Adapter, which I know seems to be of an unreliable solution, but it left me no choice.
  </p>

<h2>What model?</h2>
<p>Just a generic Jasoz brand USB 3.0 to Ethernet Gigabit Adapter</p>

<h2>The fix</h2>
  <p>
    Though it works right out of the bat when tried with other devices. However, when I hooked it up to my M710q Mini PC it has issues, the status shows up as down. But I just need 
    to do the following:
  </p>
<ol>
  <li>
    <h3>Find the Interface Name</h3>
    <p>Plug in the USB-to-Ethernet adapter and list the network interfaces to find its name (often starting with enx followed by its MAC address, or eth0, end0, etc.):</p>
    <pre><code>ip link</code></pre>
    <p>(Alternatively, use lsusb or dmesg | grep -i usb to confirm the kernel recognizes the adapter).</p>
  </li> 
  <li>
    <h3>Bring the Interface Up</h3>
    <p>Use the modern ip command to turn the interface up:</p>
    <pre><code>sudo ip link set dev &lt;interface_name&gt; up</code></pre>
    <p>(Replace &lt;interface_name&gt; with your actual adapter name, such as enx00e04c07002e).</p>
  </li>
  <li>
    <h3>Assign an IP Address (for me this was optional, since it was automatically assigned in my case)</h3>
    <ul>
      <li>
        <strong>Option A: Request an IP via DHCP (Dynamic):</strong>
        <p>If your network has a DHCP server (like a home router), run a DHCP client such as dhclient:</p>
        <pre><code>sudo dhclient &lt;interface_name&gt;</code></pre>
      </li>
      <li>
        <strong>Option B: Assign a Static IP:</strong>
        <p>If you need a manual IP address:</p>
        <pre><code>sudo ip addr add 192.168.1.50/24 dev &lt;interface_name&gt;</code></pre>
      </li>
    </ul>
  </li>
  <li>
    <h3>Make the Configuration Permanent</h3>
    <p>To ensure the interface comes up automatically on reboot, add it to /etc/network/interfaces:</p>
    <ol>
      <li>
        <p>Open the file with a text editor:</p>
        <pre><code>sudo nano /etc/network/interfaces</code></pre>
      </li>
      <li>
        <p>Add the configuration for your adapter (replace &lt;interface_name&gt;):</p>
        <pre><code>allow-hotplug &lt;interface_name&gt;
iface &lt;interface_name&gt; inet dhcp</code></pre>
        <p>(Or use inet static with address, netmask, and gateway lines if required).</p>
      </li>
      <li>
        <p>Save and close the file, then restart the networking service:</p>
        <pre><code>sudo systemctl restart networking</code></pre>
      </li>
    </ol>
  </li>
</ol>


<h2>References</h2>
<ul>
  <li>https://serverspace.us/support/help/configuring-network-adapter-in-ubuntu-or-debian/</li>
  <li>https://mirrors.bieringer.de/Linux+IPv6-HOWTO/x1018.html</li>
  <li>https://forums.debian.net/app.php/anubis/api/make_challenge?redir=https%3A%2F%2Fforums.debian.net%2Fviewtopic.php%3Ft%3D157146</li>
  <li>https://wiki.debian.org/NetworkConfiguration?pow_referer=https%3A%2F%2Fwww.google.com%2F</li>
</ul>
