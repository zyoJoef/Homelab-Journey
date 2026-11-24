# ConvertX KeePassXC Port Conflict Documentation
The Web Ul is currently set to port 3003, which connects to the container's HTTP port (3000) instead of the required HTTPS port (3001).

Even though you changed the prefix to https://, sending HTTPS traffic to container port 3000 causes a protocol mismatch or triggers the secure connection block. Because host port 3001 is already mapped directly to container port 3001, you only need to change the Web Ul port number.

<h2>How to Fix It</h2>
<ul>
  <li>In your CasaOS KeePassXC Settings, go back to the Web Ul section at the top.</li>
  <li>Keep the dropdown set to https:// and the domain as the server's ip address</li>
  <li>Change the port field from 3003 to 3001.</li>
  <li>Click Save at the bottom of the settings panel.</li>
  <li>Click the KeePassXC icon on your dashboard-it will now open the server's ip address.</li>
  <li>When your browser shows a security/certificate warning, click Advanced > Proceed to server's ip address (unsafe) to open KeePassXC.</li>
</ul>

<p>
    My current configuration has two issues: ConvertX and KeePassXC are fighting over port 3001, and KeePassXC has two           different host ports mapped to the exact same 3002 port
</p>

<h2>What Is Wrong in Your Setup</h2>
<ul>
  <li>Host Port 3007 Collision (KeePassXC): You mapped both container port (HTTP) and container port 3881 (HTTPS) to Host 3002. Docker will reject this because two container ports cannot share one host port.</li>
  <li>Web UI Port Mismatch (KeePassXC): Your KeePassXC Web Ul is still pointing to 3801, which currently belongs to ConvertX (server's ip address:3001).</li>
</ul>

<h2>Cleanest Working Configuration</h2>
  <p>Leave <strong>ConvertX</strong> exactly as you have it now, and update <strong>KeePassXC</strong> so each service has its own unique host port.</p>
  <table border="1" cellpadding="8" cellspacing="0">
    <thead>
      <tr>
        <th>App</th>
        <th>Web UI URL</th>
        <th>Host Port</th>
        <th>Container Port</th>
        <th>Protocol</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td><strong>ConvertX</strong> <em>(Keep as-is)</em></td>
        <td><code>http://development-server.local</code></td>
        <td><code>3001</code></td>
        <td><code>3000</code></td>
        <td>TCP</td>
      </tr>
      <tr>
        <td><strong>KeePassXC (HTTP)</strong> <em>(Used only for reverse proxy)</em></td>
        <td></td>
        <td><code>3002</code></td>
        <td><code>3000</code></td>
        <td>TCP</td>
      </tr>
      <tr>
        <td><strong>KeePassXC (HTTPS)</strong></td>
        <td><code>https://development-server.local</code></td>
        <td><code>3003</code></td>
        <td><code>3001</code></td>
        <td>TCP</td>
      </tr>
    </tbody>
  </table>

<h2>Steps to Fix KeePassXC in CasaOS</h2>
<ol>
  <li>Open KeePassXC Settings (<strong>&#8942;</strong> &rarr; <strong>Settings</strong>).</li>
  <li>Under <strong>Web UI</strong>, change the port from <code>3001</code> to <code>3003</code> (keep the protocol set to <code>https://</code>).</li>
  <li>Under <strong>Ports</strong>, make sure your two rows look like this:
      <ul>
        <li>Row 1: Host <code>3002</code> &rarr; Container <code>3000</code> (TCP)</li>
        <li>Row 2: Host <code>3003</code> &rarr; Container <code>3001</code> (TCP)</li>
      </ul>
  </li>
  <li>Click <strong>Save</strong>.</li>
</ol>

