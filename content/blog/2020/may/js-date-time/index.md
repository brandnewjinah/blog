---
title: Javascript Date and Time
date: "2020-05-04T16:14:02.467Z"
description: Dealing with date and time in Javascrit.
---

### Date formatting in Gatsby

One of the ways you can set date in front matter is in ISO 8601 format. It stands for International Organization for Standardizationt and it is an internationally agreed way to represent dates. It can present:
- Date
- Time of day
- Coordinated Universal Time (UTC)
- Local time with offset to UTC
- Date and time
- Time intervals
- Recurring time intervals

I'm using the format YYYY-MM-DD HH:MM:SS +/-TTTT; which represents hours, minutes, seconds, and timezone offset. Date and time is separated by "T", for the sake of readability. I decided to write a javascript code to get the current local time in ISO 8601 format.

``` javascript
const frontMatter = new Date();
// Sun May 10 2020 10:07:08 GMT+0900 (Korean Standard Time)

const localIsoTime = frontMatter.getTimezoneOffset() * 60 * 1000;
// time zone difference in minutes, from current local to UTC
// need to change to milliseconds by multiplying * 60 * 1000

let convertLocal = frontMatter - localIsoTime;
//subtract the offset from frontMatter

convertLocal = new Date(convertLocal);
//create shifted Date

let isoTime = convertLocal.toISOString();
//convert to ISO format string

console.log(isoTime);
```