<%*
let dv = app.plugins.plugins["dataview"].api;

// Query for people from the 'people' directory to autocomplete names
let peopleQuery = dv.pages('"people"').map(p => p.file.name).filter(name => name !== null && name !== undefined);

// Prompt for the person’s name
let personOptions = [...peopleQuery];
let person = await tp.system.suggester(personOptions, personOptions);

// Prompt to select meeting type: In Person or Virtual
let meetingTypeOptions = ["In Person", "Virtual"];
let meetingType = await tp.system.suggester(meetingTypeOptions, meetingTypeOptions);

// Set the title format: YYYY-MM-DD - [Person]
let formattedDate = tp.date.now("YYYY-MM-DD");
tp.file.move(`/meetings/1-1s/${formattedDate} -- ${person}`);
%>

# 1-1 Meeting with <% person %>

**Date:** <% formattedDate %>  
**Type:** <% meetingType %>  
**Attendees:** [[<% person %>]]; [[Andrew Barker]]

---
## ❓ Questions & Answers 
1. **Question 1**
---

## 💻 Status Updates
- 

---

## 📝 Meeting Notes
Summary:


---

## 📌 Action Items
- [ ] 
