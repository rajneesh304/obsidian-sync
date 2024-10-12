```dataview
TABLE file.name AS "File Name", file.path AS "File Path" FROM "Tools" 
WHERE file.name != "index"
SORT file.name ASC
```

