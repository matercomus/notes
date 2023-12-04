---
created: <% tp.file.creation_date() %>
---
tags:: [[+Daily Notes]]

# <% moment(tp.file.title,'YYYY-MM-DD').format("dddd, MMMM DD, YYYY") %>

<< [[<% fileDate = moment(tp.file.title, 'YYYY-MM-DD-dddd').subtract(1, 'd').format('YYYY-MM-DD-dddd') %>|Yesterday]] | [[<% fileDate = moment(tp.file.title, 'YYYY-MM-DD-dddd').add(1, 'd').format('YYYY-MM-DD-dddd') %>|Tomorrow]] >>

---
## 📅 Daily Questions
##### 🌜 Last night, after work, I...
- 

##### 🙌 One thing I've excited about right now is...
- 

##### 🚀 One+ thing I plan to accomplish today is...
- [ ] <% tp.file.cursor() %>

##### 👎 One thing I'm struggling with today is...
- 

---
## 📝 Notes
- 

---
### Notes created today
```dataview
List FROM "" WHERE file.cday = date("<% moment(tp.file.title,'YYYY-MM-DD').format('YYYY-MM-DD') %>") SORT file.ctime asc
```

### Notes last touched today
```dataview
List FROM "" WHERE file.mday = date("<% moment(tp.file.title,'YYYY-MM-DD').format('YYYY-MM-DD') %>") SORT file.mtime asc
```

---
## Routines
### Start
<% tp.file.include("[[Templates/Routines/Waking_Up_Routine.md]]") %>

### 🌜 Bed-time
<% tp.file.include("[[Templates/Routines/Before_Bed_Routine_Template]]") %>
