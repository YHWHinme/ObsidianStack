https://www.youtube.com/watch?v=Gd9bvdkIXOQ&t=286s
# Setting up a Webtop Containerized Desktop in a Browser

**Timestamp:** 00:00:00

**Step-by-Step Actions:**

1. **Obtain the Webtop Docker Image:**

    * **Timestamp:** 00:01:55
    * **Prerequisites:**  Internet access, Docker installed and running.  The user's home directory is assumed to exist.  No user-defined prerequisites are omitted in this step.
    * **Action:** Navigate to linuxserver.io and locate the Webtop image.  The video demonstrates selecting a specific version (Ubuntu Mate) but other options are available.


2. **Create a Docker Compose Configuration File:**

    * **Timestamp:** 00:04:41
    * **Prerequisites:**  A directory created for the Webtop service (e.g., `mkdir webtop` and `cd webtop`). A text editor (like `nano` or `vim`).
    * **Action:** Create a `docker-compose.yml` file within the `webtop` directory.  The video provides a sample configuration which includes:

        * **Service Name:** `webtop` (can be changed)
        * **Image:** `linuxserver/webtop:<tag>`  (e.g., `linuxserver/webtop:ubuntu-mate` for Ubuntu Mate).  The `<tag>` specifies the Linux distribution and desktop environment.  Refer to linuxserver.io for available tags.
        * **Privileged Mode:** `privileged: true` (required for some desktop environments like KDE and i3 on Ubuntu; optional for others like Ubuntu Mate).
        * **Environment Variables:**
            * `PUID` and `PGID`:  These should be set to the user ID and group ID of the user running the container (obtain using the `id` command on the host system).  Example: `PUID=1000 PGID=1000`.
            * `TZ`:  Set this to your server's time zone (e.g., `TZ=America/New_York`).
        * **Volumes:**
            * `/config:/config`: Maps a directory on the host machine (e.g., `/home/<user>/webtop/config`) to the `/config` directory inside the container. This is for persistent configuration.
            * Optional: `/var/run/docker.sock:/var/run/docker.sock` (This is *not* recommended in the video, as it grants the container access to the host's Docker daemon).
        * **Ports:** `3000:3000` (maps port 3000 on the host to port 3000 in the container).
        * **shm_size:**  Sets the shared memory size (recommended: at least 2GB,  e.g., `shm_size: 2g`).
        * **Restart Policy:** `restart: unless-stopped` (restarts the container automatically unless manually stopped).


3. **Determine PUID and PGID:**

    * **Timestamp:** 00:06:27
    * **Prerequisites:**  SSH access to the server where the container will run.
    * **Action:** Execute the command `id` on the server to retrieve the user ID (PUID) and group ID (PGID).  Use these values in the `docker-compose.yml` file.


4. **Create Config Directory:**

    * **Timestamp:** 00:06:51
    * **Prerequisites:**  The `webtop` directory from Step 2.
    * **Action:** Create a `config` directory inside the `webtop` directory.  This directory will be mapped to the `/config` directory within the container.  The absolute path to this directory will be used in the `docker-compose.yml` volume mapping.


5. **Update Docker Compose File (Volumes and Paths):**

    * **Timestamp:** 00:06:57
    * **Prerequisites:**  The `docker-compose.yml` file from Step 2, the `config` directory from Step 4.
    * **Action:** Update the `volumes` section of `docker-compose.yml` to reflect the correct absolute path to the `config` directory on your server.  The video uses an absolute path, but a relative path is also possible.


6. **Run Docker Compose:**

    * **Timestamp:** 00:08:37
    * **Prerequisites:** Updated `docker-compose.yml` file.
    * **CLI Command Details:**
        * **Timestamp:** `00:08:37`
        * **Prerequisites:** Docker Compose installed and running.
        * **Command Anatomy:** `docker-compose up -d` [Starts the container in detached mode (background).]


7. **Access the Webtop:**

    * **Timestamp:** 00:08:46
    * **Prerequisites:** Running Webtop container.
    * **Action:** Open a web browser and navigate to `http://<server_ip_address>:3000` or `http://<server_dns_name>:3000` to access the desktop environment.  The default login credentials are `abc/abc`.



8. **(Optional) Install Additional Applications:**

    * **Timestamp:** 00:10:53
    * **Prerequisites:** Access to the Webtop desktop environment.
    * **Action:** The video demonstrates installing VLC, LibreOffice, and VS Code using the package manager within the Ubuntu Mate desktop environment.  Installing other applications would involve similar steps, potentially requiring additional dependencies or adjustments based on the application.


9. **(Optional) Enable Privileged Mode (If Necessary):**

    * **Timestamp:** 00:13:24
    * **Prerequisites:**  Issues encountered running applications that require privileged access (like VS Code in this example).
    * **Action:**  Set `privileged: true` in the `docker-compose.yml` file, restart the container using `docker-compose down` followed by `docker-compose up -d`.

10. **(Optional) Install Node.js (using nvm):**

    * **Timestamp:** 00:13:57
    * **Prerequisites:**  Access to the Webtop terminal.  nvm (Node Version Manager) may need to be installed first.
    * **CLI Command Details:**
        * **Timestamp:** 00:14:08
        * **Prerequisites:** nvm installed.
        * **Command Anatomy:** `nvm install 14.16.1` (or your preferred Node.js version)

11. **(Optional) Verify Node.js Installation:**

    * **Timestamp:** 00:14:16
    * **Prerequisites:** Node.js installation.
    * **CLI Command Details:**
        * **Timestamp:** 00:14:16
        * **Command Anatomy:** `node -v` (Verifies the Node.js version)


12. **(Optional) Install Additional Utilities:**

    * **Timestamp:** 00:15:36
    * **Prerequisites:**  Access to the Webtop terminal.
    * **Action:** The video demonstrates installing `iputils-ping` and `dnsutils` using the apt package manager to enable ping and nslookup commands.


This detailed breakdown provides a comprehensive guide to replicating the steps shown in the video. Remember to replace placeholders like `<server_ip_address>`, `<user>`, and PUID/PGID with your actual values.  Also, be mindful of security implications, especially regarding the optional Docker socket mapping.
