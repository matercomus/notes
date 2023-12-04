# Home Dashboard
### Incomplete Daily Note Tasks
```dataview
TASK
FROM "Daily_Notes"
WHERE !completed
SORT created ASC
GROUP BY file.link
SORT rows.file.ctime DESC
```
