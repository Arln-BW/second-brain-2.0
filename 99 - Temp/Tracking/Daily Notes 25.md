```dataview
TABLE file.folder AS Path, file.etags AS "File Tags" FROM #daily and !"Templates" and "05 - Daily Notes/2025"
sort file.name desc
```
