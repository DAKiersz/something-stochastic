---
tags: Hugo
---

# Hugo - List all pages in the sub-directory

## Example
 
```
{{ range where (where .Site.RegularPages "Type" "blog") "File.Dir" "blog/tips/" }}
```

## References

https://discourse.gohugo.io/t/list-all-pages-in-sub-folder/28063

