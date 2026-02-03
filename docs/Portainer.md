### [⬅ Back](../README.md)

# [Portainer](https://www.portainer.io/)

> Portainer is an open-source, universal container management platform that provides a graphical user interface (GUI) to simplify the deployment, management, and monitoring of containerized applications on platforms like Docker, Kubernetes, and Podman.

- GUI instead of needing a CLI
- Quickly view: Images, Container, Ports, Networks, Logs, etc...

### Alternatives

> There are many different alternatives, but normally divided into Kubernetes or Docker specific.

- [NetGoat](https://github.com/Cloudable-dev/netgoat)
- [Dockge](https://github.com/louislam/dockge)
- [Yacht](https://dev.yacht.sh/)

### Login Credentials

```
# "Username": "admin",
# "Password": "localdev1234", // Required 12 Characters | Can NOT override
# Docs - https://docs.portainer.io/advanced/cli
# We need to ESCAPE `$` => `$$` to translate correctly
# > htpasswd -nb -B admin "localdev1234" | cut -d ":" -f 2 | sed -e s/\\$/\\$\\$/g
```

### Entrypoint is Unavailable | No Shell Available

To get around the usage of using secrets and NOT using a entrypoint file we create 2 variables

```
# .env
# Use Docker Secrets or Fallback to PORTAINER_PASSWORD -> ${PORTAINER_PASSWORD_FILE:-PORTAINER_PASSWORD}
PORTAINER_PASSWORD_FILE=/run/secrets/portainer_password
# Portainer requires 12 characters ->  pw: 'localdev1234'
PORTAINER_PASSWORD="$$2y$$05$$oNTl/ND/ZUS0qSXn/NfJ9enRmrojst9r6DDmg8cjMtHCjJUFZCQyy"
```

In the compose yaml we use a fallback | use the secret file OR use the .env variable
```
# docker-compose.yam
environment:
  - PORTAINER_PASSWORD_FILE=${PORTAINER_PASSWORD_FILE:-PORTAINER_PASSWORD}
