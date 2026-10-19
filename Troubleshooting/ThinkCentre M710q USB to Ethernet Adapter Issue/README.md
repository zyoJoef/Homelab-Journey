# Lenovo ThinkCentre M710q USB to Ethernet Adapter Issue
<p>Following the issue with the internal NIC or Ethernet of my recently bought <b>Lenovo ThinkCentre M710q Mini PC</b> on debian which forced me to temporarily run it on Wi-Fi, 
  but then made me firm with using it with a USB to Ethernet Adapter, which I know seems to be of an unreliable solution, but it left me no choice.
</p>

<h2>what model?</h2>
  <p>Just a generic Jasoz brand USB 3.0 to Ethernet Gigabit Adapter</p>

<h2>The fix</h2>
  <p>
    Though it works right out of the bat when tried with other devices. However, when I hooked it up to my M710q Mini PC it has issues, the status shows up as down. But I just need 
  to do the following:
  </p>
  <ol>
      <li>Find the Interface Name
          <br>
            Plug in the USB-to-Ethernet adapter and list the network interfaces to find its name (often starting with enx followed by its MAC address, or eth0, end0, etc.):
              <pre><code>ip link</code></pre>
            (Alternatively, use lsusb or dmesg | grep -i usb to confirm the kernel recognizes the adapter).
      </li> 
      <li>Bring the Interface Up
          <br>
            Use the modern ip command to turn the interface up:
              <pre><code>sudo ip link set dev <interface_name> up</code></pre>
            (Replace <interface_name> with your actual adapter name, such as enx00e04c07002e).
      </li>
      <li>Assign an IP Address (for me this was optional, since it was automatically assigned in my case)
          <br>
            <ul>
              <li>Option A: Request an IP via DHCP (Dynamic):</li>
              If your network has a DHCP server (like a home router), run a DHCP client such as dhclient:
              <pre><code>sudo ip link set dev <interface_name> up</code></pre>
            (Replace <interface_name> with your actual adapter name, such as enx00e04c07002e).
            </ul>
      </li>
  </ol>

<h2>2. List available docker-ce versions:</h2>
  <pre><code>apt-cache policy docker-ce</code></pre>

You will see a list of versions. Copy the exact version string (e.g., 5:25.0.5-1debian.12bookworm) of the version you want to downgrade to.
Example snippet string:
5:28.3.2<s>debian.12</s>bookworm /last known running


<h2>3. Stop Docker Service</h2>
  <pre><code>sudo systemctl stop docker</code></pre>


<h2>4.Remove Current Docker Packages</h2>
Remove the existing Docker packages using apt remove. This step removes the binaries, but critically, it leaves your configuration files, images, and containers (stored in /var/lib/docker) intact.
  <pre><code>sudo apt remove -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin</code></pre>

<b>Warning:</b> Do NOT use sudo apt purge or manually run sudo rm -rf /var/lib/docker, as this will delete all your containers and images.


<h2>5. Install the Specific Older Version</h2>
  <pre><code>sudo apt install -y docker-ce=[VERSION_STRING] docker-ce-cli=[VERSION_STRING] containerd.io</code></pre>

Where I used to make it run again :
  <pre><code>sudo apt install -y docker-ce=5:28.3.2~debian.12~bookworm docker-ce-cli=5:28.3.2~debian.12~bookworm containerd.io</code></pre>


<h2>6. Start the Docker service</h2>
  <pre><code>sudo systemctl start docker</code></pre>


<h2>7. Verify the new version and check your containers</h2>
  <pre><code>docker version</code></pre>
  <pre><code>docker ps -a</code></pre>


<h2>8.Prevent Future Upgrades (Optional)</h2>
To HOLD the upgrade of Docker until CasaOS is updated:
  <pre><code>sudo apt-mark hold docker-ce docker-ce-cli containerd.io</code></pre>

To UNHOLD the upgrade of Docker until CasaOS is updated:
  <pre><code>sudo apt-mark unhold docker-ce docker-ce-cli containerd.io</code></pre>

Hope this helps!


<h2>References</h2>
<ul>
  <li>https://www.youtube.com/watch?v=R8miC0--RzY</li>
  <li>https://github.com/IceWhaleTech/CasaOS/issues/2387</ul>
</ul>
