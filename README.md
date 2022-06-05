# Privacy Protecting Proxies

Serve Instagram, Reddit, and Imgur proxies with docker-compose, traefik and letsencrypt

## Deployment

1. Update DNS records to point bibliogram, libreddit and rimgo hostnames to your server's IP address
2. Install docker and docker-compose
3. Create a .env file:
```
BIBLIOGRAM_HOSTNAME=bibliogram.example.com
LIBREDDIT_HOSTNAME=libreddit.example.com
RIMGO_HOSTNAME=rimgo.example.com
LETSENCRYPT_EMAIL=alice@example.net
```
4. docker-compose up
5. delete the caserver line then `docker-compose restart` once you're confident of using actual letsencrypt SSL certs
