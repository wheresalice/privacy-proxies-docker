# Privacy Protecting Proxies

Serve Instagram, Reddit, and Imgur proxies with docker-compose, traefik and letsencrypt

## What is included?

| Name | Description | Docker image | Dockerfile |
| --   | --          | --           | --         |
| [Traefik](https://doc.traefik.io/traefik/) | Open source edge router | [traefik:v2.7](https://hub.docker.com/_/traefik) | [Dockerfile](https://github.com/traefik/traefik-library-image/blob/master/scratch/Dockerfile) |
| [Bibliogram](https://sr.ht/~cadence/bibliogram/) | An alternative front-end for Instagram. | [quay/pussthecatorg/bibliogram](https://quay.io/repository/pussthecatorg/bibliogram) | [Dockerfile](https://github.com/PussTheCat-org/docker-bibliogram-quay/blob/master/docker/Dockerfile) |
| [Libreddit](https://github.com/spikecodes/libreddit) | Libreddit is a portmanteau of "libre" (meaning freedom) and "Reddit". It is a private front-end like Invidious but for Reddit. Browse the coldest takes of r/unpopularopinion without being tracked. | [spikecodes/libreddit](https://hub.docker.com/r/spikecodes/libreddit) | [Dockerfile](https://github.com/spikecodes/libreddit/blob/master/Dockerfile) |
| [Rimgo](https://codeberg.org/video-prize-ranch/rimgo) | An alternative frontend for Imgur. Based on rimgu and rewritten in Go. | [quay.io/pussthecatorg/rimgo](https://quay.io/repository/pussthecarorg/rimgo) | [Dockerfile](https://github.com/PussTheCat-org/docker-rimgo-quay) |



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
5. Delete the caserver line then `docker-compose restart` once you're confident of using actual letsencrypt SSL certs
6. Copy the systemd service template to privacy-proxies-docker.service and edit as required
7. `systemctl enable $(pwd)/privacy-proxies-docker.service && systemctl start privacy-proxies-docker`

## How to update?


To update the stack:

```sh
docker-compose pull
docker-compose down
docker-compose up
```

To update this `docker-compose.yml` file check out the latest version on GitHub: [wheresalice/privacy-proxies-docker](https://github.com/wheresalice/privacy-proxies-docker)

