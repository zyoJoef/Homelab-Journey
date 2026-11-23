# Can't SSH via CMD
Unable to negotiate with (ip address) port 22: no matching MAC found. Their offer: hmac-sha1,hmac-md5

To connect immediately, add the <pre><code>-m hmac-sha1</code></pre> flag to your command: <pre><code>ssh -m hmac-sha1 admin@ip address</code></pre>
This error happens because your MikroTik is running an older RouterOS version that only supports legacy hashing algorithms <pre><code>(hmac-sha1)</code></pre> which modern Windows OpenSSH rejects by default for security reasons.

<h2>Steps</h2>
<ol>
  <li>
    <b>Option 1: One-Time Connection (Quickest)</b>
      <ul>
        <li>Run the following in Command Prompt: <pre><code>ssh -m hmac-sha1 admin@ip address</code></pre></li>
      </ul>
    <br><br>
  <li>
    <b>Option 2: Fix It Permanently on the MikroTik (Recommended)</b>
      <p>Once you are logged in, enable strong-crypto on the switch so it supports modern SHA-256 encryption and no longer requires the extra flag:</p>
      <ul>
        <li><pre><code>/ip ssh set strong-crypto=yes</code></pre></li>
      </ul>
      <p>Note: If your RouterOS version is very old, strong-crypto=yes might not be available. In that case, updating RouterOS via <b>System > Packages > Check For Updates</b> will add modern SSH algorithm support.</p>
    <br><br>
  <li>
    <b>Option 3: Save the Exception in Windows</b>
      <p>If you cannot update the MikroTik and don't want to type -m hmac-sha1 every time, add an exception to your Windows SSH config file:</p>
      <ol>
        <li>Open Notepad and open (or create) C:\Users\<YourUsername>\.ssh\config (with no file extension).</li>
        <li>Add these lines and save: <pre><code>Host 192.168.100.2 
MACs +hmac-sha1</code></pre></li>
      </ol>
  </li>
</ol>
