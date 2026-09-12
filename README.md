# thorium

A Docker container setup configured with Tor and an `obfs4` bridge to provide a SOCKS proxy service, alongside Privoxy for HTTP(S) proxy capabilities.

> [!WARNING]
> **Legal Warning:** The legality of using Tor varies by jurisdiction. In some countries, using or even discussing Tor is illegal. In others, it may only be illegal to use Tor to access restricted resources. Please seek competent legal advice from a qualified professional in your jurisdiction.

> [!CAUTION]
> **Security Warning:** Use this container setup only if you know exactly what you are doing. Otherwise, it is highly recommended to use the official [Tor Browser](https://www.torproject.org/).
> 
> Routing standard browsers through Tor via a proxy does **not** provide the same privacy protections as Tor Browser. Standard browsers can still leak your real IP address (via DNS leaks or WebRTC), reveal OS/font fingerprinting details, and retain tracking cookies. 
> 
> For more details, please read the official precautions: [Using Tor with Other Browsers](https://support.torproject.org/tor-browser/security/using-tor-with-other-browsers/).

## How to set up

1. **Install Docker and Docker Compose** on your host machine. Refer to the [official Docker documentation](https://docs.docker.com/) for instructions specific to your operating system.
2. **Download the configuration**: Obtain the `compose.yaml` file from this repository and save it to your local working directory.
3. **Configure the bridge**: Edit `compose.yaml` to include at least one `obfs4` bridge obtained from the Tor Project or a trusted source. Update the relevant configuration lines at the bottom of the file, then save your changes.
4. **Start the containers**: From your working directory, run `docker compose up -d` in your terminal. You can monitor the startup process by checking the logs with `docker compose logs -f`.
5. **Configure your software**: Point your applications to use the SOCKS5 proxy at `<your_host_ip>:9050` or the HTTP(S) proxy at `http://<your_host_ip>:8118`.
6. **Stop the containers**: Run `docker compose stop` in your terminal to halt the containers, or `docker compose down` to stop and completely remove them.
