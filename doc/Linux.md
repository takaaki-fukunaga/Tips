# Tips for Linux


## diffstat
- 01_before/main.c
  ```c
  #include <stdio.h>
  
  int main() {
      printf("Hello, The World!\n");
  }
  ```
- 02_after/main.c
  ```c
  #include <stdio.h>
  
  int main() {
      printf("Hello, Star Platinum!\n");
  }
  ```
- Run `diff` only.
  ```
  $ diff 01_before/ 02_after/ 
  diff 01_before/main.c 02_after/main.c
  4c4
  <     printf("Hello, The World!\n");
  ---
  >     printf("Hello, Star Platinum!\n");
  ```
- Run `diff` with `diffstat`.
  ```
  $ diff 01_before/ 02_after/ |diffstat 
   main.c |    2 +-
   1 file changed, 1 insertion(+), 1 deletion(-)  
  ```

## Docker
### Set Proxy Server
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

## grep
```sh
grep -r -i foo --include='*.c'
```
