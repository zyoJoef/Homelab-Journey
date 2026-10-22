# CasaOS Portainer Skip Setup Token
Upon setting up Portainer in CasaOS for the first time in my new server, I stumbled across the setup token which in my old server didn't asked me. And so we could have a quick turnaround for this via Environment Variable

<h2>Steps</h2>
<ol>
  <li>Open your CasaOS dashboard</li>
  <li>Hover over the Portainer app/container app icon, click the three dots (...), and select Setting.</li>
  <li>Scroll down to the Environment Variables section</li>
  <li>Click Add or fill in an empty row with</li>
      <pre><code>
        Key: PORTAINER_NO_SETUP_TOKEN 
        Value: 1
    </code></pre>
  <li>Click Save</li>
  <li>Wait for it to restart, open it and now the setup token is removed</li>
</ol>
