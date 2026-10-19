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
                  <pre><code>sudo dhclient <interface_name></code></pre>
              <li>Option B: Assign a Static IP:
                If you need a manual IP address:
                  <pre><code>sudo ip addr add 192.168.1.50/24 dev <interface_name></code></pre>
            </ul>
      <li>Make the Configuration Permanent
          <br>
            Use the modern ip command to turn the interface up:
              <pre><code>sudo ip link set dev <interface_name> up</code></pre>
            (Replace <interface_name> with your actual adapter name, such as enx00e04c07002e).
      </li>
      </li>
  </ol>


<h2>References</h2>
<ul>
  <li>https://www.youtube.com/watch?v=R8miC0--RzY</li>
  <li>https://github.com/IceWhaleTech/CasaOS/issues/2387</ul>
</ul>
