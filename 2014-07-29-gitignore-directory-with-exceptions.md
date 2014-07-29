add the directory to your top-level `.gitignore`, then add another `.gitignore` to the directory, and tell it to keep certain files:

```
# Ignore everything in this directory
*
# Except this file
!.special.css
```