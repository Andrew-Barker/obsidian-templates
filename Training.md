<%*
let courseTitle = await tp.system.prompt("Enter the Course Title");

// Retrieve the list of topics by finding folder names in the "trainings" directory
let trainingPath = app.vault.getAbstractFileByPath("trainings");
let trainingFolders = [];

if (trainingPath && trainingPath.children) {
    trainingFolders = trainingPath.children
        .filter(item => item.children !== undefined) // Ensure it's a folder by checking for children
        .map(folder => folder.name);
}

// Add "Add New Topic" option
let topicOptions = [...trainingFolders, "Add New Topic"];
let topic = await tp.system.suggester(topicOptions, topicOptions);

if (topic === "Add New Topic") {
    topic = await tp.system.prompt("Enter New Topic");
}

// Convert topic into a tag format
let topicTag = topic.replace(/\s+/g, '-').toLowerCase();
tp.file.move(`/trainings/${topic}/${courseTitle}`);
%>

# <% courseTitle %> Training Notes

**Course Title:** <% courseTitle %>  
**Date Started:** <% tp.date.now("YYYY-MM-DD") %>  
**Topic:** #<% topicTag %>  

---

## 📖 Course Overview
- **Platform/Provider**: 
- **Course Objective**: 

---

## 🛠️ Key Concepts
- **Concept 1**: Description or definition
- **Concept 2**: 

---

## 📚 Notes by Module

### Module 1: [Module Name]
- **Overview**: Brief summary of the module
- **Key Points**:
  - Point 1
  - Point 2

### Module 2: [Module Name]
- **Overview**: 
- **Key Points**: 
  - 

---

## ❓ Questions
- Question 1: 
- Question 2: 
