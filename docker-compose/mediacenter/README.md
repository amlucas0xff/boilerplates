**Media Center Stack**

A dockerized solution to effortlessly set up your personal media center.

### Prerequisites

- Ensure the Traefik container is running (in the same `Docker Network`) and is properly configured. You can find setup instructions in the [Traefik README](https://github.com/amlucas0xff/boilerplates/docker-compose/traefik/README.md).
  
> [!NOTE]
> Alternatively, you have the option to not use a reverse proxy. In this case, configure each service by adding the respective service ports and remove the Traefik label entries from the \`compose.yaml\` file.

1. **Configuration**: Rename the `.env.sample` file to `.env` and adjust the variables to suit your requirements.

2. **Initial Plex Setup**:

   - Visit the [Plex Claim Token Page](https://www.plex.tv/claim/) to generate your Plex claim token.
   - Update the `.env` file by setting the `PLEX_CLAIM_TOKEN` variable with the generated token.

3. **Network Creation**:

   - Before deploying, create a network for your services using the command below (only if it does not already exist):
     ```
     docker network create traefik
     ```

4. **Deploy the Stack**:

   - Run the following command to deploy the Media Center Stack:

     ```
     docker compose up -d --force-recreate
     ```

   - If everything works correctly, all services will be up and running. You can then start configuring the individual services. Note that this guide does not cover the detailed configuration of each service.

   - **Stack Overview**:

     - **Plex**: A media server to stream your personal collection of movies, TV shows, and music. The free version of Plex can be used for this project without requiring a paid subscription.

     - **Prowlarr**: An indexer manager that integrates with your download clients, such as QBittorrent, to download media files either manually or upon request from Sonarr or Radarr.

     - **Sonarr**: Automates downloading and managing TV shows.

     - **Radarr**: Automates downloading and managing movies.

     - **Lidarr**: Manages and downloads music albums.

     - **Readarr**: Manages and downloads eBooks.

     - **Emby**: An additional media server that complements Plex, offering features like live TV, DVR capabilities, parental controls, and customizable metadata management. Emby integrates with plugins for extended functionality, providing more flexibility in managing and streaming media.

     - **QBittorrent**: A popular torrent client used for downloading media files based on requests from services like Sonarr and Radarr.

     - **Flaresolverr**: A proxy solution that helps indexers, such as Prowlarr, connect to indexes protected by Cloudflare.

> [!NOTE]
> Once the stack is deployed and running, you can automate your media center experience. Prowlarr, Sonarr, Radarr, Lidarr, and Readarr can work together to find, download, and organize your media content automatically.

5. **General Configuration Instructions**:
      
    - Start by configuring the Plex application. Note that this procedure does not cover the entire configuration of the media center. If you do not have an account, sign up on the Plex website. Once signed up, issue a `PLEX\_CLAIM\_TOKEN` from the official [Plex Claim Token Page](https://www.plex.tv/claim/) to register your server endpoint. This step will promote your Plex instance into a media server.

    - After obtaining the claim token, configure the Plex application by specifying where your TV shows and series are stored. At this point, Plex should be mostly configured. Adjust language settings and other preferences as needed.

    - Once Plex is configured, proceed to set up the rest of the stack applications, such as Prowlarr, Radarr, and Sonarr.

### License

MIT License
