# Sky Router DHCP Dial Up Failed

<h2>Problem</h2>
<p>
So it has occurred twice already when we encountered waking up with a "Connected but No Internet" from our devices, and upon checking our ISP Router (Sky Cable) which is the model Huawei EG8041X6-10, it shows up on the One-Click Diagnosis as "DHCP Dial Up Failed", even if our other neighbors who also had the same ISP as ours doesn't have any issues. It is frustrating and can be unproductive to have no internet access, but luckily I found some solutions. 
</p>

Note: There is no guarantee that this would work for everyone. Also router settings and credential may vary from one to the other. 

<h2>Credentials</h2>
Directly quoting Facebook User "Jane Marie" post and Reddit user "aninong"
<ul>
    <li>IP Address: 192.168.100.1</li>
    <li>User: telecomadmin <br> Password: Converge@huawe123</li>
    <li>User: telecomadmin <br> Password: admintelecom</li>
    <li>User: Epadmin <br> Password: adminEP</li>
    <li>User: Epadmin <br> Password: adminEP</li>
</ul>
<b>Do not use</b> <li>User: root <br> Password: adminHW 
 <br>
  since it is not a superadmin user

<h2>Steps</h2>
Directly quoting Facebook User "Jane Marie" post
<ol>
    <li><h3>First, log in using the IP Address (192.168.100.1) (The router model is there if you have the same one, same user and password)</h3></li>
        <img src="https://github.com/user-attachments/assets/bf0cc221-1c47-47e2-bf7a-9d5e8091e966" alt="image" style="width:50%">
    <hr>
    <li><h3>Second, login</h3></li>
        <img src="https://github.com/user-attachments/assets/3d67406e-7b7d-4a7f-ac38-b8a92399725d" alt="image" style="width:50%">
    <hr>
    <li><h3>Third, login using the default credential on your router then go to One-Click Diagnosis</h3></li>
        <img src="https://github.com/user-attachments/assets/6032f9e6-4f45-45f4-ad0c-2d9eb36245a5" alt="image" style="width:50%">
            <p>If it is DHCP Dial Up Failed then proceed to the next step</p>
</li>
</ol>


<h2>References</h2>
  <a href="https://www.reddit.com/r/ConvergePH/comments/1j2n4vx/no_internet_connection_dhcp_dialup_fails/">No internet Connection | DHCP dialup fails</a>
    <br>
  <a href="https://www.facebook.com/groups/890297584784216/permalink/1050308962116410/?rdid=D61jHmbqkM8esGlL&share_url=https%3A%2F%2Fwww.facebook.com%2Fshare%2Fp%2F16256P1uXJ%2F#">DHCP DIAL UP FAILED FIXED!!!</a>
