---
title: RegEx
date: "2020-05-30T12:40:32.169Z"
description: Setting up password requirements
---

# RegEx

Password Requirement

```jsx
//7-16 only characters, numeric digits, underscore
//first character must be a letter
/^[A-Za-z]\w{7,16}$/

//6-20 at least one numeric digit, one uppercase and one lowercase
/^(?=.*\d)(?=.*[a-z])(?=.*[A-Z]).{6,20}$/

//7-15 at least one numeric digit, a special character
/^(?=.*[0-9])(?=.*[!@#$%^&*])[a-zA-Z0-9!@#$%^&*]{7,15}$/

//6 or more characters, at least one digit, at least one lowercase and at least one uppercase
/(?=.*\d)(?=.*[a-z])(?=.*[A-Z]).{6,}/;
```
