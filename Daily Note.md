<%*
let today = tp.date.now("YYYY-MM-DD");
%>
**Date:** <% today %>  

---

## 🏆 Accomplishments
- **Project/Task 1**: 
- **Project/Task 2**: 

---

## 📅 Meetings
```dataview
table without id time as "Time", subject as "Meeting", attendees as "Attendees"
from "meetings/1-1s"
where contains(attendees, "Your Name") or contains(attendees, "Your Team")
sort time asc
```


---

## 📝 General Notes
- 

---

## ⏩ Follow-Ups
- [ ] Task for tomorrow
- [ ] Task for future follow-up
