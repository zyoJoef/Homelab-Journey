# Gitea ConvertX Port Conflict
<p> 
  Because both Gitea and BigBear ConvertX default to port 3000 on CasaOS, they cannot run simultaneously on the same host port. 
  Since Gitea is already established and running on 3000, the cleanest approach is to move ConvertX to an unused port like 3001.
</p>

<h2>What is Gitea?</h2>
<p>
  Gitea is a lightweight, open-source Git hosting and DevOps platform designed for self-hosting and team collaboration. Built in Go, it runs as a single binary with minimal server requirements compared to heavier alternatives like GitLab.
</p>

<h2>What is ConvertX?</h2>
<p>ConvertX most commonly refers to an open-source, self-hosted web application for converting files locally across more than 1,000 formats, though the name is also used by a few unrelated software tools.</p>

<h2>Why do Docker port conflict happen?</h2>
<p>
  A Docker port conflict occurs when you try to bind a container to a host port that is already occupied by another container or a native process running on your host machine. 
  This results in errors like port is already allocated or Bind for 0.0.0.0:XXXX failed: port is already taken.
</p>

<h2>How to resolve Docker port conflict?</h2>
<p>To solve a Docker port conflict is to change the host port mapping so your container binds to a different, available port on your machine without disrupting whatever else is currently running.</p>

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
  <li>https://about.gitea.com/</li>
  <li>https://www.xda-developers.com/gitea-more-than-self-hosted-github-alternative/</li>
  <li>https://www.youtube.com/watch?v=Kg0ct2lBUVg</li>
  <li>https://www.reddit.com/r/DigitalEscapeTools/comments/1qzcsvs/convertx_selfhosted_file_converter/</li>
  <li>https://github.com/C4illin/ConvertX</li>
  <li>https://selfhostedworld.com/software/convertx</li>
  <li>https://github.com/knadh/listmonk/issues/1573</li>
  <li>https://github.com/Mailu/Mailu/issues/2521</li>
  <li>https://forums.docker.com/t/port-conflict-between-the-local-application-and-the-container/135788</li>
  <li>https://stackoverflow.com/questions/48281970/how-do-i-avoid-port-collision-when-using-docker</li>
  <li>https://oneuptime.com/blog/post/2026-01-16-docker-port-conflicts/view</li>
  <li>https://helpcenter.online.usc.edu/s/article/Docker-Port-Binding-Conflict-for-Port-number</li>
  <li>https://www.youtube.com/watch?v=X63Wt1WSVbE&t=1s</li>
</ul>
