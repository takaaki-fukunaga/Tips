# Docker
## Set a proxy server
1. Create the following directory.
   ```sh
   sudo mkdir /etc/systemd/system/docker.service.d
   ```
1. Set proxy server on http-proxy.conf.
   ```sh
   sudo tee /etc/systemd/system/docker.service.d/http-proxy.conf <<EOF
   [Service]
   Environment="HTTP_PROXY=http://<your-proxy-server>"
   Environment="HTTPS_PROXY=http://<your-proxy-server>"
   EOF
   ```
1. Restart Docker daemon.
   ```sh
   sudo systemctl daemon-reload
   ```
   ```sh
   sudo systemctl restart docker
   ```

## docker run
### Run arm64 container on x86_64 machine
1. Run the `docker run` command wiht `--platform` option.
   ```sh
   docker run -d -it --name ubuntu2204-arm64 --platform linux/arm64/v8 ubuntu:22.04 bash
   ```
1. Check the architecture.
   ```
   $ docker exec -it ubuntu2204-arm64 bash
   root@5262284ad1f6:/# arch 
   aarch64
   ```
