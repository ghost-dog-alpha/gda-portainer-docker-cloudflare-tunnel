
# Docker Compose: Cloudflare Tunnel and Portainer

This project provides a Docker Compose setup to deploy and manage:

1. **Cloudflare Tunnel** for securely exposing local services to the internet via Cloudflare Zero Trust.
2. **Portainer** for managing your Docker environment through a web-based interface.

## Getting Started

### Prerequisites
Ensure you have Docker and Docker Compose installed on your system.

### Configuration

This setup uses a `.env` file to manage configuration variables. Below is a description of the required and optional settings.

#### .env File Settings

```env
# Cloudflare Zero Trust TOKEN
# The token needed for your tunnel if you are using it.
CLOUDFLARE_TUNNEL_TOKEN=exaMpLetOkeNString

# Uncomment to switch to the business edition of Portainer.
# PORTAINER_IMAGE=portainer/portainer-ee:latest

# Uncomment if you need a specific version of Cloudflare Tunnel.
# CLOUDFLARED_IMAGE=cloudflare/cloudflared
```

- **`CLOUDFLARE_TUNNEL_TOKEN`** (Required): The unique token for your Cloudflare tunnel. Obtain this from your Cloudflare account.
- **`PORTAINER_IMAGE`** (Optional): Specify a custom Portainer image. Defaults to `portainer/portainer-ce:latest`. Uncomment to use the Business Edition (`portainer/portainer-ee:latest`).
- **`CLOUDFLARED_IMAGE`** (Optional): Specify a custom Cloudflare Tunnel image or version. Defaults to `cloudflare/cloudflared:latest`.

### How to Use

1. **Clone the Repository:**
   ```bash
   git clone <repository-url>
   cd <repository-folder>
   ```

2. **Create a .env File:**
   Copy the example settings and save them in a `.env` file.
   ```bash
   cp .env.example .env
   ```
   Edit the `.env` file with your preferred text editor to provide the necessary values.

3. **Start the Services:**
   Run the following command to start the services:
   ```bash
   docker-compose up -d
   ```

4. **Access Portainer:**
   - Open your browser and navigate to `https://<host-ip>:9443`.
   - Follow the setup wizard to configure your Portainer instance.

### Stopping the Services
To stop the services, use:
```bash
docker-compose down
```

## Additional Notes

- **Persistent Storage:**
  Portainer data is stored in the `portainer_data` volume. Ensure this volume is properly managed to avoid data loss.

- **Customizing Versions:**
  If you want to use a specific version of either `cloudflared` or Portainer, update the `.env` file accordingly.

- **Networking:**
  The Cloudflare Tunnel securely exposes your local services. Ensure you have a valid configuration for your tunnel in Cloudflare.

### Troubleshooting

- **Missing Tunnel Token:** Ensure `CLOUDFLARE_TUNNEL_TOKEN` is set in your `.env` file.
- **Portainer Issues:** Check logs using:
  ```bash
  docker-compose logs portainer
  ```
- **Cloudflare Tunnel Issues:** Check logs using:
  ```bash
  docker-compose logs tunnel
  ```

For further assistance, consult the [official documentation for Portainer](https://documentation.portainer.io/) and [Cloudflare Tunnel](https://developers.cloudflare.com/cloudflare-one/connections/connect-apps/).
