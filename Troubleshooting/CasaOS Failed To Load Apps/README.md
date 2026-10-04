# CasaOS Failed To Load Apps 
Directly quoting the answer from Github User <b>Fauster</b> on the thread <b>[Feedback]Can't get apps to load or update #2387</b>

Not so painful way to downgrade on Debian linux:

<h2>1. Update the package list:</h2>
  <pre><code>sudo apt update</code></pre>



<h2>2. List available docker-ce versions:</h2>
  <pre><code>apt-cache policy docker-ce</code></pre>

You will see a list of versions. Copy the exact version string (e.g., 5:25.0.5-1debian.12bookworm) of the version you want to downgrade to.
Example snippet string:
5:28.3.2<s>debian.12</s>bookworm /last known running



<h2>3. Stop Docker Service</h2>
  <pre><code>sudo systemctl stop docker</code></pre>



<h2>4.Remove Current Docker Packages</h2>
Remove the existing Docker packages using apt remove. This step removes the binaries, but critically, it leaves your configuration files, images, and containers (stored in /var/lib/docker) intact.
  <pre><code>sudo apt remove -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin</code></pre>

<b>Warning:</b> Do NOT use sudo apt purge or manually run sudo rm -rf /var/lib/docker, as this will delete all your containers and images.



<h2>5. Install the Specific Older Version</h2>
  <pre><code>sudo apt install -y docker-ce=[VERSION_STRING] docker-ce-cli=[VERSION_STRING] containerd.io</code></pre>

Where I used to make it run again :
  <pre><code>sudo apt install -y docker-ce=5:28.3.2~debian.12~bookworm docker-ce-cli=5:28.3.2~debian.12~bookworm containerd.io</code></pre>



<h2>6. Start the Docker service</h2>
  <pre><code>sudo systemctl start docker</code></pre>



<h2>7. Verify the new version and check your containers</h2>
  <pre><code>docker version</code></pre>
  <pre><code>docker ps -a</code></pre>



<h2>8.Prevent Future Upgrades (Optional)</h2>
To HOLD the upgrade of Docker until CasaOS is updated:
  <pre><code>sudo apt-mark hold docker-ce docker-ce-cli containerd.io</code></pre>

To UNHOLD the upgrade of Docker until CasaOS is updated:
  <pre><code>sudo apt-mark unhold docker-ce docker-ce-cli containerd.io</code></pre>

Hope this helps!



<h2>References</h2>
<ul>
  <li>https://www.youtube.com/watch?v=R8miC0--RzY</li>
  <li>https://github.com/IceWhaleTech/CasaOS/issues/2387</ul>
</ul>
