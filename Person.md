---
id: <% tp.file.title.replace(/\s+/g, '-') %>
created_date: <% tp.file.creation_date('YYYY-MM-DD') %>
updated_date: <% tp.file.last_modified_date('YYYY-MM-DD') %>
type: people
---
<%*
let dv = app.plugins.plugins["dataview"].api;

// Query for teams from the 'teams' directory, using the page title as the team name
let teamsQuery = dv.pages('"teams"').map(p => p.file.name).filter(t => t !== null && t !== undefined);

// Query for roles from the 'people' directory and remove the `#` from the roles
let rolesQuery = dv.pages('"people"')
    .map(p => p.role)
    .filter(r => typeof r === 'string' && r !== null && r !== undefined)
    .map(r => r.replace(/^#/, ""));  // Remove the leading `#`

// Query for managers from the 'people' directory and handle `[[ ]]` brackets
let managersQuery = dv.pages('"people"')
    .map(p => p.manager)
    .filter(m => m !== null && m !== undefined)
    .map(m => typeof m === 'object' && m.hasOwnProperty('path') ? m.path.split("/").pop().replace(/\.md$/, "") : m);

// Remove duplicates
let roles = [...new Set(rolesQuery)];
let teams = [...new Set(teamsQuery)];
let managers = [...new Set(managersQuery)];

// Check if list is empty and prompt for new value if no options are available
let roleOptions = [...roles, "Add New Role"];
let role = roles.length > 0 ? await tp.system.suggester(roleOptions, roleOptions) : await tp.system.prompt("Enter Role/Title");
if (role === "Add New Role") {
    role = await tp.system.prompt("Enter Role/Title");
}

let teamOptions = [...teams, "Add New Team"];
let team = teams.length > 0 ? await tp.system.suggester(teamOptions, teamOptions) : await tp.system.prompt("Enter Team Name");
if (team === "Add New Team") {
    team = await tp.system.prompt("Enter Team Name");
}

let managerOptions = [...managers, "Add New Manager"];
console.log("Managers for suggester:", managerOptions);
let manager = managers.length > 0 ? await tp.system.suggester(managerOptions, managerOptions) : await tp.system.prompt("Enter Manager's Name");
if (manager === "Add New Manager") {
    manager = await tp.system.prompt("Enter Manager's Name");
}

let role_tag = role.replace(/\s+/g, '-').toLowerCase();
let team_tag = team.replace(/\s+/g, '-').toLowerCase();
let manager_tag = manager.replace(/\s+/g, '-').toLowerCase();

tp.file.move(`/people/${tp.file.title}`)
%>

> [!tldr] <% tp.file.title %>
> **Role**:: #<% role_tag %>
> **Team**:: [[<% team %>]] 
> **Manager**:: [[<% manager %>]] 

## 💡 Skills/Expertise
- 

## 🕰️ Work History
- Previous Roles:
  1. **Role:** 
     **Company:** 
     **Years:** 
  2. 

## 🤝 Personal Notes
- Family: 
- Interests/Hobbies:
- Known for: 


## Recent Interactions
```dataview
table without id date as "Date", file.id as "Meeting", summary as "Summary"
from "meetings"
where contains(attendees, "[[<% tp.file.title %>]]")
sort date desc
limit 5
```

## 🏷️ Tags:
- #people
- #<% role_tag %>
- #team/<% team_tag %>
- #manager/<% manager_tag %>