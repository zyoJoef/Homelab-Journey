# Debian Remove Gnome Desktop Environment
Since the deployment of my very first home server (where I store all of my file/media) I haven't thought about fully running it headless, because I kept the desktop environment on it for troubleshooting and of alike, but today that will change. Since the Gnome desktop environment was taking up resources and space (I don't even use the other files that came along with GNOME).

<h2>Steps</h2>
<ol>
  <ul>Open your terminal (or switch to a TTY console using Ctrl + Alt + F3)</ul>
  <ul>Run the following command to purge the core GNOME components:
    <pre><code>sudo apt purge gnome-core gnome-session gnome-shell gdm3</code></pre>
  </ul>
  <ul>Remove all leftover configuration files and unneeded dependencies:
    <pre><code>sudo apt autoremove --purge</code></pre>
  </ul>
  <ul>Restart your machine to apply the changes:
    <pre><code>sudo reboot</code></pre>
  </ul>
</ol>

<h2>References</h2>
<ul>
  <li>https://superuser.com/questions/603392/how-to-remove-gnome-3-and-all-its-dependencies-from-a-debian-wheezy-netinst</li>
  <li>https://www.reddit.com/r/debian/comments/3z5exs/disable_gui/</li>
</ul>
