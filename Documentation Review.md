<%*
let docTitle = await tp.system.prompt("Enter Document Title");
let docUrl = await tp.system.prompt("Enter Document URL");

// Set the file name to "Documentation Review - [Document Title]"
tp.file.rename(`Documentation Review - ${docTitle}`);
%>
**Source:** [Confluence Document](<% docUrl %>)  
**Date Reviewed:** <% tp.date.now("YYYY-MM-DD") %>

---

## 📌 Summary
- 

## 🛠️ Technical Details
### Key Concepts
- **Concept 1**: 
- **Concept 2**: 

### Important Terms and Definitions
- **Term 1**: 
- **Term 2**: 

### System Architecture
- **Component 1**: 
- **Component 2**: 

## ❓ Questions
- Question 1: 
- Question 2: 

## 🔧 Action Items
- [ ] 
