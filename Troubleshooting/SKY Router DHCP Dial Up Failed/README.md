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
Directly quoting Facebook User "Jane Marie" post
<ol>
    <li><h3>Log in using the IP Address (192.168.100.1) (The router model is there if you have the same one, same user and password)</h3></li>
        <img src="https://github.com/user-attachments/assets/bf0cc221-1c47-47e2-bf7a-9d5e8091e966" alt="image" style="width:50%">
    <hr>
    <li><h3>Login</h3></li>
        <img src="https://github.com/user-attachments/assets/3d67406e-7b7d-4a7f-ac38-b8a92399725d" alt="image" style="width:50%">
    <hr>
    <li><h3>Login using the default credential on your router then go to One-Click Diagnosis</h3></li>
        <img src="https://github.com/user-attachments/assets/6032f9e6-4f45-45f4-ad0c-2d9eb36245a5" alt="image" style="width:50%">
            <p>If it is DHCP Dial Up Failed then proceed to the next step</p>
    <hr>
    <li><h3>On System Information, if you see these two shows up as either Disconnected or Connecting, go to the following steps</h3></li>
        <img src="https://github.com/user-attachments/assets/11388d41-cdae-40bd-b025-b1527291d880" alt="image" style="width:50%">
    <hr>
    <li><h3>Click the Advanced then WAN. Click both of them dalawa and delete</h3></li>
        <img src="https://github.com/user-attachments/assets/3e85a688-ec93-4649-96f8-b6ddab7eb4ff" alt="image" style="width:50%">
            <p>But first take a picture of each one, since we will be deleting and restoring them later on. So that you would have a backup on what value to put in the settings once we put them back later.</p>
    <hr>
    <li><h3>click Maintenance Diagnose > Configuration File. Click Save and Restart</h3></li>
        <img src="https://github.com/user-attachments/assets/93aa806e-7103-4970-9c8d-5339fa47cdfe" alt="image" style="width:50%">
            <p>Your router will restart. Log back in using the credentials at 192.168.100.1 and access the admin panel</p>
    <hr>
    <li><h3>Go back to ADVANCED > WAN and Click New</h3></li>
        <img src="https://github.com/user-attachments/assets/93aa806e-7103-4970-9c8d-5339fa47cdfe" alt="image" style="width:50%">
            <p>You will see that it is now empty. In the picture, just pretend that it is empty</p>
    <hr>
    <li><h3>Here's the setting that you must add:</h3></li>
        <pre><code>
            Service type: INTERNET
            VLAN ID: 10
            MTU: 1500
        </code></pre>
            <img src="https://github.com/user-attachments/assets/4a696d5d-ac5c-42ec-9d89-646d74a59662" alt="image" style="width:50%">
                <p>Click Apply. You will do it thrice. So you will have 3 INTERNET in the WAN. After that, go back to Maintenance Diagnosis > Configuration File then click Save and Restart.</p>
</li>
</ol>



<h2>References</h2>
  <a href="https://www.reddit.com/r/ConvergePH/comments/1j2n4vx/no_internet_connection_dhcp_dialup_fails/">No internet Connection | DHCP dialup fails</a>
    <br>
  <a href="https://www.facebook.com/groups/890297584784216/permalink/1050308962116410/?rdid=D61jHmbqkM8esGlL&share_url=https%3A%2F%2Fwww.facebook.com%2Fshare%2Fp%2F16256P1uXJ%2F#">DHCP DIAL UP FAILED FIXED!!!</a>
