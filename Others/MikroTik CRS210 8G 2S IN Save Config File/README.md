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
    <b>Alternative: One-Line Export via Windows 11 Terminal</b>
      <p>
        If SSH is enabled on your CRS210 and you already know its IP address, you can pull the configuration straight to your Windows 11 Desktop without opening WinBox:
      </p>
      <ul>
        <li>Run the SSH command. Open Terminal (PowerShell) in Windows 11, replace 192.168.88.1 with your switch's IP address, and run:
ssh admin@192.168.88.1 "/export" > "$HOME\Desktop\crs210-config.rsc"</li>
      </ul>
  </li>
</ol>
