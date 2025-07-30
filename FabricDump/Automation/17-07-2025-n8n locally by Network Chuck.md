
https://www.youtube.com/watch?v=-ErfsM2TYsM

This video provides a comprehensive guide on how to self-host N8N, a powerful workflow automation tool, either on-premises in your lab or on a Virtual Private Server (VPS) in the cloud. The main purpose is to walk users through the technical setup, including prerequisites for external access, Docker installation, and N8N deployment using Docker Compose, catering to both publicly accessible and fully local instances.

### Video Summary

#### [00:00:00] Introduction to Self-Hosting N8N

*   The video focuses on self-hosting N8N on-prem or on a VPS.
*   It acknowledges that users might already know N8N, but for newcomers, it recommends a prior introductory video.
*   **Key point:** N8N can be exposed to the internet for best functionality or kept fully local.

#### [00:01:00] Prerequisites for External Access (Domain & Cloudflare Tunnel)

*   N8N's connectivity needs can be challenging when hosted behind a firewall.
*   **Two essential prerequisites for public access:**
    *   **[00:01:20] Domain Name:** A purchased domain or subdomain (e.g., `n8n.hackwell.com`), costing around $3-5 per year.
    *   **[00:02:00] Cloudflare Tunnels:** A free Cloudflare product that creates a secure, secret tunnel from your public domain to your N8N instance, bypassing firewalls. This is highly recommended for securely exposing N8N.

#### [00:02:50] Setting Up Cloudflare Account & Domain

*   **Sign up for a free Cloudflare account.**
*   **[00:03:00] Register or connect a domain:** The video demonstrates registering a new domain (e.g., `n8niscool.cc`) through Cloudflare.

#### [00:03:50] Configuring Cloudflare Zero Trust Tunnel

*   Navigate to Cloudflare's **Zero Trust** dashboard.
*   Go to **Networks > Tunnels** and click "Create a tunnel."
*   Select **Cloudflared** and name your tunnel (e.g., `n8n-tunnel`).
*   **[00:04:30] Install Cloudflared Agent:** Copy the provided installation commands for your OS (e.g., Debian Linux) and run them on your N8N server (or any Linux machine with network access to the N8N host).
    *   Install the Cloudflared service to ensure it runs continuously.
*   **[00:06:00] Configure Tunnel Connection:**
    *   Set **Subdomain** to `n8n`.
    *   Choose your new **Domain**.
    *   For **Service**, select `HTTPS` and enter the *internal IP address* of your N8N server (e.g., `10.7.7.1`).
    *   Under **Additional application settings**, enable `No TLS Verify`.
    *   Save the tunnel configuration.

#### [00:07:00] Installing N8N Server

*   **[00:07:20] SSH into your server:** Access your server (on-prem or VPS) via SSH, typically as a root user.
*   **[00:07:40] Install Docker:** N8N will be installed using Docker. The video guides through installing Docker on Ubuntu using the APT repository (referencing official Docker documentation).
*   **[00:09:00] Install N8N with Docker Compose:**
    *   **[00:09:20] Create a directory:** `mkdir n8n-compose` and `cd n8n-compose`.
    *   **[00:09:40] Create a `.env` file:** Use `nano .env` and paste the configuration from N8N's official documentation.
        *   **[00:10:00] Configure `N8N_HOST`:**
            *   For **Cloud/Public access:** Use your root domain (e.g., `n8niscool.cc`) or VPS domain (e.g., `sv.blah.hostinger.cloud`).
            *   For **Fully Local access:** Create a custom local domain (e.g., `mycoolwebsite.local`). This requires setting up a DNS entry on your local DNS server pointing to your N8N Docker host's IP.
        *   **[00:13:00] Other settings:** Set `SUBDOMAIN` to `n8n`, `TZ` to your timezone (e.g., `America/Chicago`), and `SSL_EMAIL` for certificate generation (primarily for cloud users).
    *   **[00:13:50] Create local files directory:** `mkdir local_files`.
    *   **[00:14:00] Create `docker-compose.yml`:** Use `nano docker-compose.yml` and paste the provided Docker Compose configuration, which includes both **Traefik** (as a reverse proxy) and **N8N** containers. While Traefik isn't strictly necessary with Cloudflare Tunnels, it's kept for simplicity and adherence to official N8N documentation.
    *   **[00:15:20] Run Docker Compose:** Execute `docker compose up -d` to pull the images and spin up the N8N and Traefik containers.
*   **[00:16:00] Verify Installation and Access:**
    *   Use `docker ps` to confirm both `n8n` and `traefik` containers are running.
    *   Access your N8N instance via the configured subdomain (e.g., `https://n8n.n8niscool.cc` or `https://n8n.mycoolwebsite.local`).

### Conclusion

By following these steps, you will have successfully **self-hosted your very own N8N instance**, accessible either publicly via a Cloudflare Tunnel or locally within your network. You are now ready to begin building your first automation projects.