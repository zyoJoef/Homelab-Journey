# 10/16/2026

<p>
    It's been months since I've wanted to add a secondary home server to my homelab. Although I would occasionally use my old LG laptop for it, but personally it isn't ideal and it's a bit bulky too! Govern that it has the screen, keyboard, touchpad, and even the battery. Not until I saw an online listing of a Lenovo ThinkCentre M710q Tiny Mini PC that came with power adapter, but doesn't include the RAM nor Disk, which is okay since I currently have a few spare ones in hand, which I snagged for a fair price point.
</p>

<h2>Specification:</h2>
<ul>
  <li>Model : Lenovo M710q Tiny</li>
  <li>CPU : Intel Core i3-7100T 3.40GHz</li>
  <li>Memory : 8GB DDR4 RAM (2x 4GB)</li>
  <li>Disk : Toshiba 2.5" 256GB SATA SSD</li>
  <li>I/O Ports : 2 DisplayPort, Headset port, 6 USB ports, Wi-Fi, and LAN</li>
</ul>

<a href="https://psref.lenovo.com/syspool/Sys/PDF/ThinkCentre/ThinkCentre_M710_Tiny/ThinkCentre_M710_Tiny_Spec.PDF">Lenovo ThinkCentre M710q Tiny Spec PDF</a>

<h2>Why did I brought it in the first place?</h2>
<p>
    I wanted to have a dedicated/separate server for development and for testing various things that is separate from my main media/file server. And I know it would make more sense if I would install something like Proxmox into it, but I still find the simplicity of Debian with CasaOS runs perfectly for my case.
</p>

<h2>What are the services that you are running into it?</h2>
<p>The following are the services that I'm running:</p>
<ul>
  <li>Gitea</li>
  <li>Code Server</li>
  <li>Pi-hole</li>
  <li>Tailscale</li>
</ul>

<h2>wait there are issues?</h2>
<p>
    Yes, there is! At first when I tried it out on my first two set of 2x 4GB RAM, it gave me 2 short beeps followed by 1 long beep, which signifies a memory is not detected. Tried swapping both sticks, and turns out it was one of the stick were broken (that I got from my friend's broken Lenovo IdeaPad laptop), while the other one that I salvaged from my old broken Lenovo IdeaPad 330 laptop works just as fine. I tried out my second set of 2x 4GB RAM which is from my Acer Aspire 3 and my younger sister's HP laptop, which works right out of the box without any problem. I thought the problem was finished, but then I tried connecting it to the LAN cable. It seems like this particular model has a quirk of flaw with the ethernet not working on Linux (since it works just as fine in Windows), tried resolving it for hours; from flashing the update via USB and UEFI Shell to Updating the BIOS, none of which resolved the problem, so at the moment it is currently running of Wi-Fi only, and I am planning to buy an USB-to-Ethernet Adapter, even if it is a bit sketchy for my setup.
</p>

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
