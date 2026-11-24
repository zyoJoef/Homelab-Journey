# ConvertX KeePassXC Port Conflict Documentation
The Web Ul is currently set to port <code>3003</code>, which connects to the container's HTTP port (<code>3000</code>) instead of the required HTTPS port (<code>3001</code>).

Even though you changed the prefix to <code>https://</code>, sending HTTPS traffic to container port <code>3000</code> causes a protocol mismatch or triggers the secure connection block. Because host port <code>3001</code> is already mapped directly to container port <code>3001</code>, you only need to change the Web Ul port number.

<h2>How to Fix It</h2>
<ul>
  <li>In your CasaOS KeePassXC Settings, go back to the Web Ul section at the top.</li>
  <li>Keep the dropdown set to <code>https://</code> and the domain as the <code>server's ip address</code></li>
  <li>Change the port field from <code>3003</code> to <code>3001</code>.</li>
  <li>Click Save at the bottom of the settings panel.</li>
  <li>Click the KeePassXC icon on your dashboard-it will now open the <code>server's ip address</code>.</li>
  <li>When your browser shows a security/certificate warning, click Advanced > Proceed to <code>server's ip address</code> (unsafe) to open KeePassXC.</li>
</ul>

<p>
    My current configuration has two issues: ConvertX and KeePassXC are fighting over port <code>3001</code>, and KeePassXC has two different host ports mapped to the exact same <code>3002</code> port
</p>

<h2>What Is Wrong in The Setup</h2>
<ul>
  <li><strong>Host Port <code>3007</code> Collision (KeePassXC):</strong> Mapped both container port <code>3000</code> (HTTP) and container port <code>3001</code> (HTTPS) to Host <code>3002</code>. Docker will reject this because two container ports cannot share one host port.</li>
  <li><strong>Web UI Port Mismatch (KeePassXC):</strong> KeePassXC Web Ul is still pointing to <code>3801</code>, which currently belongs to ConvertX (<code>server's ip address:3001</code>).</li>
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
        <td><code>server's ip address</code></td>
        <td><code>3001</code></td>
        <td><code>3000</code></td>
        <td>TCP</td>
      </tr>
      <tr>
        <td><strong>KeePassXC (HTTP)</strong></td>
        <td><em>(Used only for reverse proxy)</em></td>
        <td><code>3002</code></td>
        <td><code>3000</code></td>
        <td>TCP</td>
      </tr>
      <tr>
        <td><strong>KeePassXC (HTTPS)</strong></td>
        <td><code>server's ip address</code></td>
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

<h2>Fix for KeepassXC won't open</h2>
<p>
    KeePassXC won't open because <strong>its Web UI field is still set to port <code>3001</code> instead of <code>3003</code></strong>.
</p>
<p>
    Your Network port mappings (<code>3003 -> 3000</code> and <code>3001 -> 3001</code>) are now completely right, so CasaOS is just sending your browser to the old <code>3001</code> address (which is running ConvertX over HTTP, causing an SSL/protocol error when KeePassXC tries to open it with <code>https://</code>).
</p>

<ol>
  <p>Steps:</p>
  <li>Open <strong>KeePassXC Settings</strong> (<code>⋮ -> Settings</code>).</li>
  <li>Look at the very top section labeled <strong>Web UI</strong>:
    <ul>
      <li>Protocol: <code>https://</code></li>
      <li>Domain/IP: <code>server's ip address</code></li>
      <li>Port: Change <code>3001</code> to <code>3003</code></li>
    </ul>
  </li>
  <li>Click <strong>Save</strong>.</li>
</ol>

