```dataview
TABLE file.name AS "File Name", file.path AS "File Path" FROM "" WHERE !contains(file.path, "/index.md") 
SORT file.name ASC
```

