# 🛠 Team: <% tp.file.title %> 

## 🎯 Purpose/Responsibility
- 

## 👥 Team Members
```dataview
table without id file.link as "Team Member", join(filter(file.tags, (t) => contains(t, "#role/")), ", ") as "Role/Title"
from "people"
where contains(file.tags, "#team/<% tp.file.title.replace(/\s+/g, '-').toLowerCase() %>")
sort file.name asc
```

## 🚀 Current Projects
- Project 1: 
- Project 2: 

## 📝 Notes
- 