<%*
let term = await tp.system.prompt("Enter the Term or Acronym");
let categoryOptions = ["EDI", "Software", "Logistics", "Other"];
let category = await tp.system.suggester(categoryOptions, categoryOptions);
let categoryTag = category.toLowerCase().replace(/\s+/g, '-');  // Convert category to lowercase and hyphenated format

tp.file.move(`/dictionary/terms/${term}`);
%>
# <% term %>

**Category:** <% category %>  
**Date Documented:** <% tp.date.now("YYYY-MM-DD") %>  

**Tags:** #dictionary #<% categoryTag %>

---

## 📖 Definition


## 📝 Context of Use
- **Example 1**: 
- **Example 2**: 

## 🔗 Related Terms
```dataview
list from "dictionary/terms"
where contains(file.tags, "#<% categoryTag %>")
sort file.name asc
```

## 📚 Sources or References
- [Confluence Page](URL)
- [External Documentation](URL)
