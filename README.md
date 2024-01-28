- 📝 Todo: Change hardcoded values to environment variables.

---

# Home Lab Setup with Docker Compose

This repository contains Docker Compose files to quickly set up a small home lab environment featuring Flame, Portainer, Traefik, and Authelia. These tools work together to create a powerful, easy-to-manage, and secure home server setup.

Traefik, Portainer, and Flame are secured with Authelia.

## Services Overview

### Traefik
Traefik is a modern HTTP reverse proxy and load balancer that makes deploying microservices easy. Traefik integrates with your existing infrastructure components and configures itself automatically and dynamically. In this setup, it is used to route traffic to your various services and provide SSL termination.

Accessible at: `https://traefik.domain.com`

### Portainer
Portainer provides a detailed and easy-to-use interface for managing Docker containers, images, networks, and volumes. It's an essential tool for anyone working with Docker, making it easier to visualize what's happening in your Docker environment.

Accessible at: `https://portainer.domain.com`

### Flame
Flame is a simple and minimalistic dashboard for your server. It allows you to organize and manage your web applications and bookmarks with ease. Flame offers a clean interface to access all your home lab services from one place.

Accessible at: `https://flame.domain.com`

### Authelia
Authelia is an open-source authentication and authorization server providing 2-factor authentication and single sign-on (SSO). It acts as a security layer for your services, ensuring that only authorized users can access them.

Accessible at: `https://authelia.domain.com`

Note: smtp is not yet configured in this setup. You need to check notifications text file in authelia folder for activation link (2fa initial setup). 

## Installation

To set up these services, you need to:

1. **Clone the Repository**:
   ```bash
   git clone https://your-repository-url.git
   cd your-repository-directory
   ```

2. **Prepare Configuration**:
   - Replace `domain.com` with your actual domain in all configuration files.
   - Set up your email in the Traefik configuration for Let's Encrypt notifications.
   - Generate an `acme.json` file for Traefik and set the correct permissions:
     ```bash
     touch traefik/acme.json
     chmod 600 traefik/acme.json
     ```
   - change all secrets from config files to your own.

3. **Deploy with Docker Compose**:
   For each service (Traefik, Portainer, Flame, Authelia), navigate to its directory and run:
   ```bash
   docker-compose up -d
   ```

## Usage

Once deployed, you can access each service at its respective subdomain. Ensure you've configured your DNS records to point to your server's IP address (80 and 443 need to be open).

## Security

- Ensure all services are behind Traefik for SSL termination and secure access.
- Use Authelia for adding an authentication layer to your services.

---

Disclaimer: Please be aware that in the current setup of this repository, all configurations, including domain names, email addresses, and other sensitive parameters, are hardcoded. This approach might not be suitable for a production environment and is primarily intended for learning and development purposes.

Happy homelabbing! 🚀