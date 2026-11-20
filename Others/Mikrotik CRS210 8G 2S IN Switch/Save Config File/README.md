# MikroTik CRS210 8G 2S IN Save Config File
The MikroTik CRS210-8G-2S+IN runs RouterOS exclusively (unlike CRS3xx models, it does not dual-boot into SwOS). 
You can export its complete switch and routing configuration directly to your Windows 11 PC using WinBox or Windows Terminal.

<h2>Steps</h2>
<ol>
  <li>
    <b>Connect from Windows 11</b>
      <ul>
        <li>Plug in your Ethernet cable. Connect your Windows 11 PC to any of the eight Gigabit Ethernet ports (ether1 through ether8) on the CRS210.</li>
        <li>Launch WinBox. Download and open WinBox on Windows 11.</li>
        <li>Discover the switch. Click the Neighbors tab in WinBox to locate your CRS210 by its MAC address or IP address (default is 192.168.88.1 with username admin and a blank password). Click on the device and hit Connect.</li>
      </ul>
    <br><br>
  <li>
    <b>Step 2: Export the Configuration</b>
      <ul>
        <li>Open the terminal. Click New Terminal on the left-hand sidebar.</li>
        <li>Run the export command. Type <pre><code>/export file=crs210-config</code></pre> and press Enter. If you are running RouterOS v7 and want passwords or secrets included in the script, use this instead <pre><code>/export show-sensitive file=crs210-config</code></pre></li>
        <li>Download to Windows 11. Click Files on the left-hand sidebar, find <pre><code>crs210-config.rsc</code></pre> and drag it directly onto your destination directory.</li>
      </ul>
    <br><br>
  <li>
    <b>Alternative: One-Line Export via Windows 11 Terminal</b>
      <p>
        If SSH is enabled on your CRS210 and you already know its IP address, you can pull the configuration straight to your Windows 11 Desktop without opening WinBox:
      </p>
      <ul>
        <li>Run the SSH command. Open Terminal (PowerShell) in Windows 11, replace <pre><code>192.168.88.1</code></pre> with your switch's IP address, and run:
<pre><code>ssh admin@192.168.88.1 "/export" > "$HOME\Desktop\crs210-config.rsc"</code></pre></li>
      </ul>
  </li>
</ol>

<h2>CRS210 Hardware Notes</h2>
<ul>
  <li>Switch chip settings. Because the CRS210 uses a QCA-8519 switch chip, all of your VLANs, port isolation, and hardware switch rules under <pre><code>/interface ethernet switch</code></pre> are automatically included in the .rsc export.</li>
  <li>Migrating to a newer switch. If you are exporting this configuration to move to a newer CRS3xx series switch, avoid importing the .rsc file directly without editing it first. CRS1xx/2xx switches handle VLANs in the Switch menu, whereas CRS3xx switches use Bridge VLAN Filtering, meaning the switch-chip commands will fail on newer hardware.</li>
</ul>

<h2>References</h2>
<ul>
  <li>https://www.discomp.cz/mikrotik-cloud-router-switch-crs210-8g-2s-in_d62815.html</li>
  <li>https://manual.mikrotik.com/hardware/crs-series/</li>
  <li>https://help.mikrotik.com/docs/spaces/UM/pages/17498175/CRS-series</li>
  <li>https://www.youtube.com/watch?v=k5N0F8iTX3s&t=241s</li>
  <li>https://academy.socialwifi.com/en/hardware-and-installation/setup-faqs/how-to-export-configuration-from-a-mikrotik-device/</li>
  <li>https://cdn.mikrotik.com/web-assets/mum/presentations/EU17/presentation_4068_1491395690.pdf</li>
</ul>
