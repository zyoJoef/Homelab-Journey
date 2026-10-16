# CasaOS Pi-hole Code Server Port Conflict
As I install CasaOS in the SSD (via the old LG Laptop) of the upcoming new secondary server that I'm waiting to arrive. I stumbled upon a problem where the Pi-hole and Code Server Ports have conflict with one another, which was frustrating. But luckily the AI chatbot <b>Google Gemini</b> helped me resolved it.


<h2>What is Pi-hole?</h2>
  <p>Pi-hole is a free, open-source DNS sinkhole that blocks advertisements, trackers, and malicious domains across an entire home network without needing ad-blocking software on individual devices.</p>


<h2>What is Code-Server?</h2>
  <p>code-server is an open-source project by Coder that runs Microsoft’s Visual Studio Code (VS Code) on a remote server and makes it accessible through a standard web browser.</p>

<h2>Deep Dive Into the Problem</h2>
<ul>
  
  Code Server
    <pre><code>
        Web UI Port :8080  
        Port Host :8080
        Port Container :8443
    </code></pre>

  Pi-hole
    <pre><code>
        Web UI Port :8080  
        Port Host :8080
        Port Container :80
    </code></pre>
  </ul>

Right out of the bat there is indeed a conflict in the Port :8080

<h2>Fix</h2>
<ul>
  <li>First, uninstall Pi-hole. On the dashboard, find the <b>+</b> sign, and select <b>Install a customized app</b></li>
  <li>Hover to the Import next to <b>X or exit button</b></li>
  <li>Paste the YAML bellow (if you've done a fresh download of Pi-hole like I did) then select submit
    <pre><code>
version: "3"

services:
  pihole:
    container_name: pihole
    image: pihole/pihole:latest
    ports:
      - "8800:80/tcp"      # Web Interface Port mapped to 8800
      - "53:53/tcp"        # DNS Port (TCP)
      - "53:53/udp"        # DNS Port (UDP)
      - "67:67/udp"        # DHCP Port (Only needed if Pi-hole is your DHCP server)
    environment:
      TZ: "Asia/Manila"
      WEBPASSWORD: "SetYourSecurePasswordHere" # Change this to your desired admin password
    # Volumes store your data persistently so it isn't lost on restart
    volumes:
      - "/DATA/AppData/pihole/etc-pihole:/etc/pihole"
      - "/DATA/AppData/pihole/etc-dnsmasq.d:/etc/dnsmasq.d"
    cap_add:
      - NET_ADMIN # Required if you want to use Pi-hole as a DHCP server
    restart: unless-stopped
    </code></pre>
  </li>
  <li>Go to the settings of the container/app</li>
  <li>On the Web UI section, enter the port value :8800 (or any port that isn't being used, in my case 8800 isn't being used)</li>
  <li>Below it. Set the Network mode from <b>brdige</b> to <b>host</b> (Since our device won't be able to point to it when set to bridge)</li>
  <li>On the Environment Variable, click add</li>
  <li>Then add the followng
    <pre><code>
    Key: WEB_PORT
    Value: 8800
      <br>
    (Below is optional if adding the one above won't load the Pi-hole Web UI dashboard)
      <br>
    Key: FTLCONF_webserver_port
    Value: 8800 
    </code></pre>  
  </li>
  <li>Toggle Apply and it would restart</li>
  <li>Once finish, viola! No more conflict!</li>


<h2>Important Note</h2>
  <p>Milage may vary</p>
  <p>
    You may also need to go to the terminal of the container/app or the web interface if you forgot your password
        <pre><code>sudo pihole setpassword</code></pre>  
  </p>


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
