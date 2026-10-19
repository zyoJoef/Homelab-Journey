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
    I wanted to have a dedicated/separate server for development and for testing various things that is separate from my main media/file server. And I know it would make more sense if I would install something like Proxmox into it, but I still find the simplicity of Debian with CasaOS runs perfectly for my case. Also, since the included processor, is only 2 Core 4 Thread one, I didn't want it to do some heavy tasking that would lead to bottleneck, hence why there is only a few services running as of the writing of this README file.
</p>

<h2>What are the services that you are running into it?</h2>
<p>The following are the services that I'm running:</p>
<ul>
  <li>Code Server</li>
  <li>Gitea</li>
  <li>Pi-hole</li>
  <li>Tailscale</li>
  <li>Virtual Machine Manager</li>  
</ul>

<h2>There are issues?</h2>
<p>
    Yes, there is! At first when I tried it out on my first two set of 2x 4GB RAM, it gave me 2 short beeps followed by 1 long beep, which signifies a memory is not detected. Tried swapping both sticks, and turns out it was one of the stick were broken (that I got from my friend's broken Lenovo IdeaPad laptop), while the other one that I salvaged from my old broken Lenovo IdeaPad 330 laptop works just as fine. I tried out my second set of 2x 4GB RAM which is from my Acer Aspire 3 and my younger sister's HP laptop, which works right out of the box without any problem. I thought the problem was finished, but then I tried connecting it to the LAN cable. It seems like this particular model has a quirk of flaw with the ethernet not working on Linux (since it works just as fine in Windows), tried resolving it for hours; from flashing the update via USB and UEFI Shell to Updating the BIOS, none of which resolved the problem, at the moment it is currently running on Wi-Fi only and I am planning to buy an USB-to-Ethernet Adapter for it, even if it is a bit sketchy for my setup.
</p>

<h2>Why the Pi-hole helped with the ISP DNS issues?</h2>
<p>
    Since the deployment of this new server into my homelab, it significantly improved the constant DNS issues we keep having from the ISP. Because when we using the default ISP DNS, it would frequently have problems loading websites from time to time. Whereas now, it only has a slight issue upon turning on or starting the new server, and becomes smooth sailing from there, together with the ads being reduced in some ad pestered websites.
</p>

<h2>Note for setting up Pi-hole with Unbound as Recursive DNS Server</h2>
<p>
    Since I've run Pi-hole together with Unbound as my Recursive DNS Server, upon copy pasting the path file from the Pi-hole unbound documentation gave me an error:
        <pre><code>/etc/unbound/conf.d/pi-hole.conf</code></pre> 
        <pre><code>Error writing /etc/unbound/conf.d/pi-hole.conf: No such file or directory</code></pre>
    I then turned to Google's AI; Gemini for the fix, which worked for me:
        <pre><code>sudo nano /etc/unbound/unbound.conf.d/pi-hole.conf</code></pre>
</p>

<h2>References</h2>
<ul>
    <li>https://support.lenovo.com/hk/en/solutions/ht505216-post-beep-symptoms-thinkcentre</li>
    <li>https://www.youtube.com/watch?v=6YbG5UOvrvw</li>
    <li>https://www.reddit.com/r/Lenovo/comments/qo2yoi/thinkcentre_m710q_keeps_dropping_wired_ethernet/</li>
    <li>https://www.reddit.com/r/homelab/comments/1ssa5bb/lenovo_thinkcentre_m710q_tiny_intel_i219v_2_nic/</li>
    <li>https://www.reddit.com/r/Ubuntu/comments/1ssa8kz/lenovo_thinkcentre_m710q_tiny_intel_i219v_2_nic/</li>
    <li>https://www.youtube.com/watch?v=FnFtWsZ8IP0</li>
    <li>https://docs.pi-hole.net/guides/dns/unbound/</li>
</ul>
