# 10/16/2026

<p>
    It's been months since I've wanted to add a secondary home server to my homelab. Although I would occasionally use my old LG laptop for it, but personally it isn't ideal and it's a bit bulky too! Govern that it has the screen, keyboard, touchpad, and even the battery. Not until I saw an online listing of a Lenovo ThinkCentre M710q Tiny Mini PC that came with power adapter, but doesn't include the RAM nor Disk, which is okay since I currently have a few spare ones in hand, which I snagged for a fair price point.
</p>

<h2>Specification:</h2>
<ul>
  <li>Model : Lenovo M710q Tiny</li>
  <li>CPU : Intel Core i5-6400T 2.80GHz</li>
  <li>Memory : 8GB DDR4 RAM (2x 4GB)</li>
  <li>Disk : Toshiba 2.5" 256GB SATA SSD</li>
  <li>I/O Ports : 2 DisplayPort, Headset port, 6 USB ports, Wi-Fi, and LAN</li>
</ul>

<a href="https://psref.lenovo.com/syspool/Sys/PDF/ThinkCentre/ThinkCentre_M710_Tiny/ThinkCentre_M710_Tiny_Spec.PDF">Lenovo ThinkCentre M710q Tiny Spec PDF</a>

<h2>Why did I brought it in the first place?</h2>
<p>
    After noticing that the laptop gets really hot easily, I was concern about using it from extended periods of time, where I also read somewhere that using a laptop for homelab isn't advisable too since they're not primarily designed to run 24/7, and you get the risk of the spicy pillow too! Moreover, the new machine still is running the same Debian + CasaOS setup, just enclosed on a new machine that is more compact (since the screen, keyboard, touchpad, and battery are out of the equation). 
</p>

<p>
    I went for this Mini PC instead of buying a proper System Unit or computer, since they're really quiet, power efficient, and somewhat easier to maintain as compared to their more capable or expandable yet big computer tower or rack-mount server.
</p>

<h2>What happened to the laptop?</h2>
<p>
    Well it sat on the shelf again being unused, which I'm now just using for experimental stuff (such as trying different Linux distro, Trying DietPi + PiHole, etc.)
</p>

<h2>What are the services that you are running into it?</h2>
<p>The following are the services that I'm running:</p>
<ul>
  <li>Jellyfin</li>
  <li>Swing Music</li>
  <li>Tailscale</li>
  <li>Virtual Machine Manage</li>
  <li>Downtify</li>
  <li>Memos</li>
  <li>Crafty</li>
  <li>Portainer</li>
  <li>OpenSSH</li>
</ul>

<h2>Note</h2>
<p>
    On the later part I've actually attached that secondary 2TB HDD back, but this time with an external USB Disk Enclosure, since there's no more space left inside for another one, and so that I could do a RAID 1 Setup again. 
</p>

<p>
    I know the way I placed the server in the picture was wrong because they should be somewhere in/at the bottom instead of being in the middle, which is why redid it after doing some researching about putting the heavier equipments on the bottom and the lighter one obviously in the middle or at the top (top-down approach). 
</p>
<p>
   Also, a few months ago I did try to run Ollama local LLM on my LG Laptop server, but then it really showed it's hardware limitation and the bare minimum needed in order to run one. Hence why I didn't bother installing Local LLM, especially with the current price of RAM and Disk nowadays being all over the roof.
</p>
