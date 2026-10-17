# Custom DNS with Tailscale 

<h2>What is DNS?</h2>
<p>
  DNS, or Domain Name System, is the phonebook of the internet. It translates human-readable web addresses (like example.com) into machine-readable numeric IP addresses (like 192.0.2.1) so computers can find and talk to each other.
</p>

<h2>What is Tailscale?</h2>
<p>
  Tailscale is a zero-configuration, identity-based mesh virtual private network (VPN) built on top of the WireGuard protocol. It creates a secure, encrypted private network—known as a tailnet—that connects your devices, servers, and cloud infrastructure directly to each other, no matter where they are located.
</p>

<h2>How to use Custom DNS on Tailscale?</h2>
  <ul>
  <li>On the admin console, look into the <b>Network</b> (located in the left-side), and below you'll find DNS. </li>
      <img src="https://github.com/user-attachments/assets/fbfd3952-0862-4941-a822-c66de97dfa39" alt="image" style="width:20%">
    <li>On DNS, scroll down to the <b>Nameservers</b> section</li>
      <img src="https://github.com/user-attachments/assets/0413767f-6374-4897-8f5d-3c6e15fcfd2e" alt="image" style="width:50%">
      <img src="https://github.com/user-attachments/assets/ab8228cc-33f4-4132-b5f9-5f9d6af36d98" alt="image" style="width:50%">
    <li>Select <b>Add nameserver</b>, click Custom, then your desired IP Address, and click save</li>
      <img src="https://github.com/user-attachments/assets/55123e8f-39f8-4c5a-a18a-cb937e2790ee" alt="image" style="width:20%">
        <br>
      <img src="https://github.com/user-attachments/assets/ec33a201-2804-4664-8a2c-5a5ecbb9c624" alt="image" style="width:30%">
  </ul> 

<h2>Important note when using Pi-hole as DNS in Tailscale</h2>
<p>If you're going to use your Pi-hole device with DNS on Tailscale, you must use the dedicated IP Address given by Tailscale and not the local IP Address</p>
 
<h2>References</h2>
<ul>
  <li>https://tailscale.com/docs/reference/dns-in-tailscale</li>
  <li>https://www.fortinet.com/resources/cyberglossary/what-is-dns</li>
  <li>https://aws.amazon.com/route53/what-is-dns/</li>
  <li>https://tailscale.com/docs/concepts/what-is-tailscale</li>
  <li><https://dev.to/hugovalters/what-is-tailscale-the-vpn-that-doesnt-suck-3b66/li>
  <li>https://www.youtube.com/watch?v=GVPhBSmMuq8</li>
</ul>
