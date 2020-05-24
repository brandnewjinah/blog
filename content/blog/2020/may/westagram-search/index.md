---
title: Westagram search functionality
date: "2020-05-11T22:40:32.169Z"
description: Adding search functionality to the Westagram desktop site.
---

### HTML and CSS

```HTML
<div class="search">
  <input type="search" placeholder="Search" class="searchinput">
  <div class="suggestions">
  </div>
</div>
```

- Div 안에
- Search Input 넣어주고
- Search drop down

```javascript
const users = [
  { id: "brandnewjinah" },
  { id: "finallywknd" },
  { id: "patrickchoimd" },
  { id: "janekh" },
  { id: "euneuney" },
]

const searchInput = document.querySelector(".searchinput") //grab input box
const suggestionsWrapper = document.querySelector(".suggestions")

searchInput.addEventListener("input", function (e) {
  let searchWord = searchInput.value
  searchWord = searchWord.toLowerCase()
  suggestionsWrapper.innerHTML = ""
  const suggestions = users.filter(user => {
    return user.id.includes(searchWord)
  })
  suggestions.forEach(suggested => {
    const div = document.createElement("div")
    div.innerHTML = suggested.id
    suggestionsWrapper.appendChild(div)
  })
  if (searchWord === "") {
    suggestionsWrapper.innerHTML = ""
  }
})
```
