# CasaOS Portainer Client sent an HTTP request to an HTTPS server
When I first installled Portainer in my new server, it first gave me an error of <b>"Client sent an HTTP request to an HTTPS server"</b> which luckily is just an easy fix.

<h2>Steps</h2>
<ol>
  <li>Go to your CasaOS dashboard</li>
  <li>Navigate over to the Portainer app/container</li>
  <li>Click the three dots (...), and select Setting</li>
  <li>Look for the Web UI settings</li>
  <li>And change the Web UI protocol from http:// to https://</li>
</ol>

<h2>Note</h2>
  <p>
    Milage may vary, so you might encounter a different problem from mine and vice versa.
  </p>
