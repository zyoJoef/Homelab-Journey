# HP 2530 8G J9774A Managed Switch Save Config

<h2>Steps</h2>
<ul>
  <li>
    Method 1: Use the Modern Web UI
      <ol>
        <li>Return to the Modern Web UI: Refresh the page or navigate back to the switch's IP address.</li>
        <li>Expand Configurations: Look at the bottom of the dark gray sidebar on the left and click Configurations (right below Security).</li>
        <li>Click Configuration Management / Backup: Open the submenu item that appears underneath Configurations.</li>
        <img width="1615" height="672" alt="Screenshot 2026-11-19 174328" src="https://github.com/user-attachments/assets/e4dadd3c-022d-4adb-8075-55a747b09a9a"/>
      </ol>
  </li>
  <li>
    Method 2: Export via CLI 
    <p>If the web interface refuses to download the file, connect to the switch via SSH or a console cable (using PuTTY, Tera Term, or Terminal):</p>
      <ol>
        <li>Turn off page breaks: <pre><code>no page</code></pre></li>
        <li>Display the full configuration: <pre><code>show running-config</code></pre></li>
        <li>Save the text: Highlight everything from <pre><code>; J9774A Configuration Editor;</code></pre> down to the last line, copy it, and paste it into Notepad or any text editor. Save the file as <pre><code>switch-config.cfg</code></pre></li>
      </ol>
  </li>
</ul>

<h2>References</h2>
<ul>
  <li>https://community.networking.hpe.com/discussion/network-crash-with-aruba-2530-8g-switches</li>
  <li>https://arubanetworking.hpe.com/techdocs/AOS-Switch/16.10/Aruba%202530%20Management%20and%20Configuration%20Guide%20for%20ArubaOS-Switch%2016.10.pdf</li>
  <li>https://marktugbo.com/2018/02/20/hp-aruba-procurve-2530-2500-default-configurations/</li>
  <li>https://www.youtube.com/watch?v=7g7JyPaSaLg&t=701s</li>
  <li>https://support.hpe.com/hpesc/public/docDisplay?docId=c04432839&docLocale=en_US</li>
  <li></li>
</ul>
