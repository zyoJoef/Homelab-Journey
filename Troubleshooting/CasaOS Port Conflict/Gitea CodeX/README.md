# Gitea CodeX Port Conflict

<p> 
  Because both Gitea and BigBear ConvertX default to port 3000 on CasaOS, they cannot run simultaneously on the same host port. 
  Since Gitea is already established and running on 3000, the cleanest approach is to move ConvertX to an unused port like 3001.
</p>

<h2>How to Change the Port in CasaOS</h2>
<ul>
  <li>Open your CasaOS Dashboard in your web browser.</li>
  <li>Locate the ConvertX app icon (it may appear grayed out or stopped because it failed to start).</li>
  <li>Hover over the ConvertX icon, click the three vertical dots (⋮) in the top-right corner of the app card, and select Settings.</li>
  <li>Scroll down to the Ports section. You will see a mapping where the Host port is 3000 and the Container port is 3000.</li>
  <li>Change the Host port from 3000 to 3001 (leave the Container port as 3000).</li>
  <li>6. Scroll up to the Web UI section (at the top of the settings window) and update the port number there to 3001 as well. (This ensures clicking the app icon on your dashboard opens the correct URL).</li>
  <li>Click Save at the bottom right.</li>
  <p>CasaOS will automatically recreate the container with the new port binding and start it up. You can now access Gitea at http://<your-debian-ip>:3000 and ConvertX at http://<your-debian-ip>:3001.</p>
</ul>

<h2>If You Installed ConvertX via Custom Docker Compose</h2>
<p>If you deployed ConvertX manually via SSH on your Debian machine instead of through the CasaOS App Store, edit your docker-compose.yml file to update the left side of the port mapping:</p>
<ul>
  <li>Then add the followng
    <pre><code>
services:
  big-bear-convertx:
    # ... other settings ...
    ports:
      - "3001:3000"
    </code></pre>  
  </li>
  <li>Then apply the change by running docker compose up -d in that directory.</li>
</ul>

<h2>References</h2>
<ul>
  <li>https://pi-hole.net/</li>
  <li>https://www.reddit.com/r/pihole/comments/1dobl9v/so_what_exactly_is_the_point_of_a_pihole_i/</li>
  <li>https://medium.com/@light.pen8923/pi-hole-what-is-it-and-why-you-might-want-to-use-it-5e76feb8efdc</li>
  <li>https://privacyinternational.org/guide-step/4341/raspberry-pi-setup-and-run-pi-hole</li>
  <li>https://github.com/coder/code-server</li>
  <li>https://coder.com/blog/exploring-code-server-and-coder-unleashing-the-power-of-web-based-development-en</li>
  <li>https://marketplace.digitalocean.com/apps/vs-code-server</li>
  <li>https://www.youtube.com/watch?v=_jV2n_fbRxU</li>
  <li>https://www.reddit.com/r/CasaOS/comments/1k2yqni/casaos_pihole_cant_get_past_the_password/</li>
</ul>
