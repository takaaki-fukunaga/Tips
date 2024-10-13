# Dpcker

## docker run
### Run arm64 Container on x86_64 Machine
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
