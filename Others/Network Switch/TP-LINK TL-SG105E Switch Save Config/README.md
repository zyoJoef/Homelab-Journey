# TP-LINK TL-SG105E Switch Save Config

<h2>Steps</h2>
<ul>
  <li>
    Save Changes to the Switch
      <ol>
        <li>Web UI: Make your changes and click Apply so they take effect immediately. Then click Save Config in the top menu or navigation bar to write them to non-volatile memory before rebooting or unplugging power.</li>
        <li>Easy Smart Configuration Utility: Enter your username and password (default is <b>admin</b> for both), apply your settings, and check/click the Save Config option. As noted in a TP-Link Business Community thread, a user reported that saving via the Easy Smart Configuration Utility helped retain VLAN settings across power cycles when the web GUI had trouble.</li>
      </ol>
  </li>
    <br>
  <li>
    Back Up or Restore a Configuration File 
      <ol>
        <li>Log in to the switch's web interface and go to System > Backup and Restore.</li>
        <li>To save a backup file: Click Backup Config, choose a folder and file name, and click Save. Wait without disconnecting power until the download completes.</li>
        <li>To restore a backup file: Click Choose File, select your .cfg file (using only letters, digits, hyphens, or underscores), click Restore Config, and confirm with Yes. Wait for the switch to finish rebooting.</li>
        <img width="1403" height="556" alt="Screenshot 2026-11-19 180534" src="https://github.com/user-attachments/assets/728bd108-a164-406b-9224-164d7118225a" />
      </ol>
  </li>
    <br>
  <li>
    Troubleshooting Tips 
    <p>If the web interface refuses to download the file, connect to the switch via SSH or a console cable (using PuTTY, Tera Term, or Terminal):</p>
      <ol>
        <li>Update firmware: A post on the TP-Link Business Community notes that updating to the latest firmware from the TP-Link Download Center can resolve bugs where Save Config does not stick on older firmware versions of the TL-SG105E.</li>
        <li>Verify your subnet: If you change the switch's IP address, make sure your computer is on the same subnet so you can log back in and save the configuration.</li>
      </ol>
  </li>
</ul>

<h2>References</h2>
<ul>
  <li>https://static.tp-link.com/res/down/doc/TL-SG108PE_V1_UG.pdf</li>
  <li>https://community.tp-link.com/en/business/forum/topic/103526</li>
  <li>https://community.tp-link.com/en/business/forum/topic/96183</li>
  <li>https://www.youtube.com/watch?v=7g7JyPaSaLg&t=701s</li>
  <li>https://www.youtube.com/watch?v=EIfBBTGfEZQ&t=201s</li>
  <li>https://www.tp-link.com/ph/support/download/tl-sg105e/</li>
</ul>

