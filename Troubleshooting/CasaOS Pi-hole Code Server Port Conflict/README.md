# CasaOS Pi-hole Code Server Port Conflict
As I install CasaOS in the SSD of the upcoming new secondary server. I stumbled upon a problem where the Pi-hole and Code Server Ports have conflict with one another

Not so painful way to downgrade on Debian linux:

<h2>1. Update the package list:</h2>
  <pre><code>sudo apt update</code></pre>



<h2>2. List available docker-ce versions:</h2>
  <pre><code>apt-cache policy docker-ce</code></pre>

You will see a list of versions. Copy the exact version string (e.g., 5:25.0.5-1debian.12bookworm) of the version you want to downgrade to.
Example snippet string:
5:28.3.2<s>debian.12</s>bookworm /last known running
