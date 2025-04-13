---
banner: "![[howls.gif]]"
banner_y: 1
banner_lock: "true"
---
```widgets
type: clock
```

>[!multi-column]
> 
>> [!todo]+ Todo 
>> ```dataview 
>> task
>>where !completed and contains(tags, "") and !contains(text, ">scheduled")
>> ```
> 
> >[!example]+ Tags
> >🔖 Tagged:  #code/javascript 
> >`$=dv.list(dv.pages('#code/javascript').sort(f=>f.file.name,"desc").limit(3).file.link)`
> 
> >[!summary]+ Recent files
> >`$=dv.list(dv.pages('').sort(f=>f.file.mtime.ts,"desc").limit(6).file.link)`

### InComplete Tasks 
```dataview
task
where !completed and contains(tags, "") and !contains(text, ">scheduled")
```
### Daily Note in The Last Week
```dataview
table file.cday AS "Created"
from "05 - Daily Notes/2025"
where file.cday >= date(today) - dur(1 week)
sort file.name desc
```

### My Daily Boards In The Last Week
```dataview
table file.cday AS "Created"
from #excalidraw
where file.cday >= date(today) - dur(1 week)
sort file.cday desc
```
### List files Created In The Last Week
```dataview
TABLE file.ctime AS "Created"
WHERE file.ctime >= date(today) - dur(1 week)
sort file.cday desc
```

