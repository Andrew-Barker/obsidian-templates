---
id: <% tp.file.title.replace(/\s+/g, '-') %>
created_date: <% tp.file.creation_date('YYYY-MM-DD') %>
updated_date: <% tp.file.creation_date('YYYY-MM-DD') %>
type: people
---
<%*
let role = await tp.system.prompt("Enter Role/Title");
let team = await tp.system.prompt("Enter Team Name");
let manager = await tp.system.prompt("Enter Manager's Name");

let role_tag = role.replace(/\s+/g, '-').toLowerCase();
let team_tag = team.replace(/\s+/g, '-').toLowerCase();
let manager_tag = manager.replace(/\s+/g, '-').toLowerCase();
%>

> [!tldr] <% tp.file.title %>
> **Role:** <% role %>
> **Team:** [[<% team %>]] <!-- Linking to the team page -->
> **Manager:** [[<% manager %>]] <!-- Linking to the manager's page -->

## 📝 Work Notes
- Current Responsibilities:
  - 
- Key Projects/Contributions:
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

## 🏷️ Tags:
- #people
- #role/<% role_tag %>
- #team/<% team_tag %>
- #manager/<% manager_tag %>