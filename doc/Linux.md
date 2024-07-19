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
- Run `diffstat` with `diff`.
  ```
  $ diff 01_before/ 02_after/ 
  diff 01_before/main.c 02_after/main.c
  4c4
  <     printf("Hello, The World!\n");
  ---
  >     printf("Hello, Star Platinum!\n");
  ```
  ```
  $ diff 01_before/ 02_after/ |diffstat 
   main.c |    2 +-
   1 file changed, 1 insertion(+), 1 deletion(-)  
  ```

## grep
```sh
grep foo  --include='*.c' -r
```
