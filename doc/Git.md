# Tips for Git
## Reference
- GitHub Training Kit
  - https://training.github.com/

## git config
### Set user name and email address
```sh
git config --global user.name "your-name"
```
```sh
git config --global user.email "your-email-address"
```

### Set proxy server
```sh
git config --global http.proxy http://<your-proxy-server>
```
```sh
git config --global https.proxy http://<your-proxy-server>
```

### List all variables
```sh
git config --list
```
```sh
git config -l
```

## git log
### Check the differences between forked and original repository
1. Clone the forked repository.
   ```sh
   git clone https://github.com/nxp-imx/linux-imx.git
   ```
1. Move to the cloned directory (e.g., linux-imx).
1. Add the original repository.
   ```sh
   git remote add stable https://gitlab.com/linux-kernel/stable.git
   ```
   - `stable`: You can set any name (e.g., upstream, mainline, vanilla). In this case, I set `stable`.
1. Downloads all history from the remote tracking branches.
   ```sh
   git fetch stable
   ```
1. Check the differences.
   ```sh
   git log --oneline --no-merges stable/linux-6.6.y..origin/lf-6.6.y
   ```
   - Command result: 
     ```
     $ git log --oneline --no-merges stable/linux-6.6.y..origin/lf-6.6.y
     b586a521770e (HEAD -> lf-6.6.y, tag: lf-6.6.23-2.0.0, origin/lf-6.6.y, origin/HEAD) LF-12620 firmware: se_fw: Fix 8ULP iMEM issue when RTD is power down
     da4e1bbc0a6a LF-12593-4 driver: firmware: enable she support
     (snip)
     ```
1. Get the line numbers of differences.
   ```sh
   git log --oneline --no-merges stable/linux-6.6.y..origin/lf-6.6.y|wc -l
   ```
   - Command result:
     ```
     $ git log --oneline --no-merges stable/linux-6.6.y..origin/lf-6.6.y|wc -l
     6064
     ```

### Reference
- https://zenn.dev/link/comments/871bc0b55961a9
- https://scrapbox.io/kadoyau/%E3%83%95%E3%82%A9%E3%83%BC%E3%82%AF%E5%85%83%E3%83%96%E3%83%A9%E3%83%B3%E3%83%81%E3%81%A8%E3%81%AE%E5%B7%AE%E5%88%86%E3%82%92%E6%AF%94%E8%BC%83%E3%81%97%E3%81%9F%E3%81%84