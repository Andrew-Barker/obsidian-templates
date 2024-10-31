<%*
let dv = app.plugins.plugins["dataview"].api;

// Prompt for the meeting subject
let subject = await tp.system.prompt("Enter the Meeting Subject");

// Prompt to select if this meeting is linked to a project
let projectLinkOptions = ["None", ...dv.pages('"projects"').map(p => p.file.name)];
let projectLink = await tp.system.suggester(projectLinkOptions, projectLinkOptions);
projectLink = projectLink !== "None" ? `[[${projectLink}]]` : "";

// Prompt to select if this meeting is linked to a team
let teamLinkOptions = ["None", ...dv.pages('"teams"').map(p => p.file.name)];
let teamLink = await tp.system.suggester(teamLinkOptions, teamLinkOptions);
teamLink = teamLink !== "None" ? `[[${teamLink}]]` : "";

// Prompt to select attendee type (Teams or Individuals)
let attendeeTypeOptions = ["Teams", "Individuals"];
let attendeeType = await tp.system.suggester(attendeeTypeOptions, attendeeTypeOptions);

// Initialize the attendees list
let attendees = [];
let continueAdding = true;

// Loop to add attendees until "End Selection" is chosen
while (continueAdding) {
    let options = attendeeType === "Individuals" 
        ? [...dv.pages('"people"').map(p => p.file.name), "End Selection"]
        : [...dv.pages('"teams"').map(p => p.file.name), "End Selection"];

    let selectedAttendee = await tp.system.suggester(options, options);
    if (selectedAttendee === "End Selection") {
        continueAdding = false;
    } else {
        attendees = [...attendees, `[[${selectedAttendee}]]`];
    }
}

// Set the file name to include the subject and date
let formattedDate = tp.date.now("YYYY-MM-DD");
tp.file.rename(`${subject} - ${formattedDate}`);
%>

# <% subject %> - <% formattedDate %>

**Subject:** <% subject %>  
**Date:** <% formattedDate %>  
**Project:** <% projectLink %>  
**Team:** <% teamLink %>  
**Attendee Type:** <% attendeeType %>  

---

## 👥 Attendees
<%* attendees.forEach(attendee => { %>- [ ] <% attendee %>
<%* }) %>

## 📋 Agenda
1. 

## 📝 Discussion Notes
- **Topic 1**:
  - 
- **Topic 2**:
  - 

## 🗳️ Decisions
- 

## 📌 Action Items
- [ ] 
