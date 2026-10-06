# Sky Router DHCP Dial Up Failed

<h2>Problem</h2>
<p>
So it has occurred twice already when we encountered waking up with a "Connected but No Internet" from our devices, and upon checking our home ISP Router (Sky Cable) which is the model Huawei EG8041X6-10, it shows up on the One-Click Diagnosis as "DHCP Dial Up Failed". Even if our other neighbors who also had the same ISP as ours doesn't have any issues, it is frustrating and can be unproductive to have no internet access, but luckily I found some solutions. 
</p>

Note: There is no guarantee that this would work for everyone. Also router settings and credential may vary from one to the other. 

TRY AT YOUR OWN RISK!!

<h2>Credentials</h2>
Directly quoting Facebook User "Jane Marie" post and Reddit user "aninong"
<ul>
    <li>IP Address: 192.168.100.1</li>
    <li>User: telecomadmin <br> Password: Converge@huawe123</li>
    <li>User: telecomadmin <br> Password: admintelecom</li>
    <li>User: Epadmin <br> Password: adminEP</li>
    <li>User: Epadmin <br> Password: adminEP</li>
</ul>
<b>Do not use the credential</b> <li>User: root <br> Password: adminHW 
 <br>
  since it is not a superadmin user, and only has limited options to access.



<h2>Steps</h2>
<ol>
    <li><h3>Search the IP Address of the router (192.168.100.1) (The router model is there if you have the same one, same user and password)</h3></li>
        <img src="https://github.com/user-attachments/assets/bf0cc221-1c47-47e2-bf7a-9d5e8091e966" alt="image" style="width:50%">
    <hr>
    <li><h3>Login using the provided credentials above</h3></li>
        <img src="https://github.com/user-attachments/assets/3d67406e-7b7d-4a7f-ac38-b8a92399725d" alt="image" style="width:50%">
    <hr>
    <li><h3>Login using the default credential on your router then go to One-Click Diagnosis</h3></li>
        <img src="https://github.com/user-attachments/assets/6032f9e6-4f45-45f4-ad0c-2d9eb36245a5" alt="image" style="width:50%">
            <p>If it is DHCP Dial Up Failed then proceed to the next step</p>
    <hr>
    <li><h3>On System Information, if you see these two shows up as either Disconnected or Connecting, go to the following steps</h3></li>
        <img src="https://github.com/user-attachments/assets/11388d41-cdae-40bd-b025-b1527291d880" alt="image" style="width:50%">
    <hr>
    <li><h3>Click the Advanced then WAN. Click both of them and delete</h3></li>
        <img src="https://github.com/user-attachments/assets/3e85a688-ec93-4649-96f8-b6ddab7eb4ff" alt="image" style="width:50%">
            <p>But first take a picture of each one, since we will be deleting and restoring them later on. So that you would have a backup on what to put in the settings once we put them back later.</p>
    <hr>
    <li><h3>Click Maintenance Diagnose > Configuration File. Click Save and Restart</h3></li>
        <img src="https://github.com/user-attachments/assets/93aa806e-7103-4970-9c8d-5339fa47cdfe" alt="image" style="width:50%">
            <p>Your router will restart. Log back in using the credentials at 192.168.100.1 and access the admin panel</p>
    <hr>
    <li><h3>Go back to ADVANCED > WAN and Click New</h3></li>
        <img src="https://github.com/user-attachments/assets/a25a8e2c-1776-4bc5-8181-2dcea2f114d3" alt="image" style="width:50%">
            <p>You will see that it is now empty. In the picture, just pretend that it is empty</p>
    <hr>
    <li><h3>Here's the setting that you must add:</h3></li>
        <pre><code>
            Service Type: INTERNET
            VLAN ID: 10
            MTU: 1500
        </code></pre>
            <img src="https://github.com/user-attachments/assets/4a696d5d-ac5c-42ec-9d89-646d74a59662" alt="image" style="width:50%">
                <p>Click Apply. You will do it thrice. So you will have 3 INTERNET in the WAN. After that, go back to Maintenance Diagnosis > Configuration File then click Save and Restart.</p>
    <hr>
    <li><h3>Your router will restart and log back in to the admin. Check if the 3 INTERNET we did earlier shows up as Connected. How to check? Click SYSTEM INFORMATION > WAN.</h3></li>
            <p>
                If one of them shows up as Connected then congrats you have Internet Connection! But we are not finished yet, Go back to Advanced > WAN and delete the other two (2) INTERNET that we did earlier, since we                 only need one. Go to NEW and add this settings:
            </p>
        <pre><code>
            Service Type: TR069
            VLAN ID: 10
            MTU: 1500
        </code></pre>
            <p>Click APPLY. Go to Maintenance Diagnosis > Config then SAVE AND RESTART. And viola you have Internet again!</p>
</li>
</ol>



<h2>Other Alternative</h2>
<ul>
    <li><b>Power Cycle the Equipment:</b> Turn off and unplug your optical network terminal (ONT/modem) and your router. Wait for 30 to 60 seconds, plug in the modem first and let its lights stabilize, then plug in your         router.</li>
    <li><b>Release and Renew IP / Check WAN Settings:</b> Log in to your router’s administrative page (usually 192.168.1.1 or 192.168.0.1) using the credentials on the sticker under the device. Verify that the WAN              connection type is set to Dynamic IP (DHCP) rather than PPPoE or Static, unless your specific plan requires otherwise.</li>
    <li><b>Check for Outages:</b> A DHCP/WAN failure can sometimes be caused by a wider regional outage or server-side drop from your provider rather than a broken home device.</li>
    <li><b>Change DNS settings:</b> If you can reach the WAN/LAN setup, try manually updating your DNS servers to public options like Cloudflare (1.1.1.1 and 1.0.0.1).</li>
    <li><b>Avoid hard-resetting immediately:</b> Pushing the physical reset button for too long can wipe your ISP-specific VLAN and provisioning settings, which often makes the connection worse.</li>
    <li><b>Contact your ISP support hotline:</b> If the diagnostics still show a DHCP dialup failure, the issue is typically on the provider's side or requires a remote reconfig of your ONT (Optical Network Terminal)           profile.</li>

</ul>



<h2>References</h2>
  <a href="https://www.reddit.com/r/ConvergePH/comments/1j2n4vx/no_internet_connection_dhcp_dialup_fails/">No internet Connection | DHCP dialup fails</a>
    <br>
  <a href="https://www.facebook.com/groups/890297584784216/permalink/1050308962116410/?rdid=D61jHmbqkM8esGlL&share_url=https%3A%2F%2Fwww.facebook.com%2Fshare%2Fp%2F16256P1uXJ%2F#">DHCP DIAL UP FAILED FIXED!!!</a>
