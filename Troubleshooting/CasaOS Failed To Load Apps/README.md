# CasaOS Failed To Load Apps 
Directly quoting the answer from Github User <b>Fauster</b> 

Not so painful way to downgrade on Debian linux:

<h2>1. Update the package list:</h2>
  <pre><code>sudo apt update</code></pre>


<h2>2. List available docker-ce versions:</h2>
  <code><pre>apt-cache policy docker-ce</code></pre>

You will see a list of versions. Copy the exact version string (e.g., 5:25.0.5-1debian.12bookworm) of the version you want to downgrade to.
Example snippet string:
5:28.3.2<s>debian.12</s>bookworm /last known running


<h2>3. Stop Docker Service</h2>
  <code><pre>sudo systemctl stop docker</code></pre>


<h2>4.Remove Current Docker Packages</h2>
Remove the existing Docker packages using apt remove. This step removes the binaries, but critically, it leaves your configuration files, images, and containers (stored in /var/lib/docker) intact.
  <code><pre>sudo apt remove -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin</code></pre>

<b>Warning:</b> Do NOT use sudo apt purge or manually run sudo rm -rf /var/lib/docker, as this will delete all your containers and images.


<h2>5. Install the Specific Older Version</h2>
sudo apt install -y docker-ce=[VERSION_STRING] docker-ce-cli=[VERSION_STRING] containerd.io

Where I used to make it run again :

sudo apt install -y docker-ce=5:28.3.2~debian.12~bookworm docker-ce-cli=5:28.3.2~debian.12~bookworm containerd.io

Start the Docker service
sudo systemctl start docker

Verify the new version and check your containers
docker version
docker ps -a

8.Prevent Future Upgrades (Optional)

To HOLD the upgrade of Docker until CasaOS is updated:

sudo apt-mark hold docker-ce docker-ce-cli containerd.io

To UNHOLD the upgrade of Docker until CasaOS is updated:

sudo apt-mark unhold docker-ce docker-ce-cli containerd.io

Hope this helps!

Reacted by jone79, Ry, Andrei Filippov, Simos Sigma, blitzespiee, chchia, Mujtaba Asif, z3rodown, Anil Kumar, mkart7 and 18 more
Reacted by Erlam Castanho, Noa, Ömer Emre Bozkurt and Alex


<h2>References</h2>
<ul>
  <li>https://www.youtube.com/watch?v=R8miC0--RzY</li>
  <li>https://github.com/IceWhaleTech/CasaOS/issues/2387</ul>
</ul>
