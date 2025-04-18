# Docker-Compose Setup for Media Services

This `docker-compose.yml` file configures and deploys multiple Docker containers that manage services for a media server, utilizing tools like Transmission, Sonarr, Radarr, Jellyfin, and more. Each service is configured to run independently, yet interconnected, allowing for efficient media management and automated downloads.

## Configured Services

### 1. **Transmission with VPN (Mullvad)**
   - **Purpose**: Runs Transmission alongside a VPN (Mullvad) to ensure anonymous downloading.
   - **Ports**: 7001 (Access Transmission's web interface)
   - **Volumes**: Configures paths for downloaded files and Transmission's settings.

### 2. **Sonarr**
   - **Purpose**: Sonarr is used for managing TV shows and automating their downloads.
   - **Ports**: 7002 (Access Sonarr's web interface)
   - **Volumes**: Configures paths for Sonarr's settings and TV series files.

### 3. **Prowlarr**
   - **Purpose**: Prowlarr is an indexer for media, particularly designed to integrate with Sonarr and Radarr.
   - **Ports**: 7003 (Access Prowlarr's web interface)
   - **Volumes**: Configures the path for Prowlarr's settings files.

### 4. **Jellyseerr**
   - **Purpose**: Jellyseerr is a tool that allows you to manage media content, such as movies and TV shows, through a web interface.
   - **Ports**: 7004 (Access Jellyseerr's web interface)
   - **Volumes**: Configures paths for Jellyseerr's settings and media libraries (movies, music, TV shows).

### 5. **Radarr**
   - **Purpose**: Radarr is used to manage and automate the downloading of movies.
   - **Ports**: 7005 (Access Radarr's web interface)
   - **Volumes**: Configures paths for Radarr's settings and movie files.

### 6. **Jellyfin**
   - **Purpose**: Jellyfin is an open-source media server similar to Plex, allowing you to watch movies and TV shows on any compatible device.
   - **Ports**: 7006 (Access Jellyfin's web interface)
   - **Volumes**: Configures paths for Jellyfin's settings and media data (movies, TV shows, music).

## Volume Structure
Each container is assigned a specific volume for configuration files and data (such as downloads, TV shows, movies, and music). The volumes are:

- **/docker/config/**: Directory to store each service's configuration.
- **/docker/data/**: Directory to store Transmission's downloaded files.
- **/docker/media/**: Directory to store media files (movies, TV shows, music).

## Environment Variables
The following environment variables are configured in the `docker-compose.yml` file:

- **OPENVPN_PROVIDER**: Defines the VPN provider. In this case, Mullvad.
- **OPENVPN_CONFIG**: The OpenVPN configuration file to be used for the connection.
- **OPENVPN_USERNAME** and **OPENVPN_PASSWORD**: Credentials for your Mullvad account.
- **LOCAL_NETWORK**: Defines the local network that should not go through the VPN.
- **TZ**: The server's time zone.

## Usage

1. **Prepare the Environment**: Make sure you have Docker and Docker Compose installed on your server.
2. **Clone the Repository**: If you don’t have the `docker-compose.yml` file on your machine, clone it from GitHub or create one similar.
3. **Configure the Paths**: Replace the paths in the volumes with the correct paths on your system.
4. **Run Docker Compose**: Navigate to the directory where the `docker-compose.yml` file is located and run:

   ```bash
   docker-compose up -d
