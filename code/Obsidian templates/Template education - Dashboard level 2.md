<%*
// https://github.com/DerCarlauer/obsidian-templater-script-organizer-education

console.log("Executing Templater: Template education - Dashboard level 2")
const PATH = "/Education/"

if (tp.file.title == "Untitled" || tp.file.title == "Unbenannt")  {
	var module
	try {	
	  module = await tp.system.prompt("Module name (Important: Write it correctly):")
	  if(module == "" || module == null) throw 'Empty variable "module"'
	  } catch (e) {
	  console.log(e)
	  fileName = "Delete me"
	  await tp.file.rename(fileName)
	}
} else {
	var module = tp.file.title
}
fileName = "Dashboard - " + module
var buttonModule = module.replace(/ /g, '-')
var tagModule = module.replace(/ /g, '_').toLowerCase()

var path = PATH + module + "/"
var buttonName = "New document (" + module + ")"
var buttonTypeNote = module
var buttonId = "button-education-" + buttonModule.toLowerCase() + "-document-1"
//Name file and move it to the destination folder:
await tp.file.rename(fileName)
await tp.file.move(path + fileName)

//The ID of the button only works if there are no umlauts. Therefore, these are removed for the ID.
function replaceUmlauts(string)
{
    value = string.toLowerCase();
    value = value.replace(/ä/g, 'ae');
    value = value.replace(/ö/g, 'oe');
    value = value.replace(/ü/g, 'ue');
    value = value.replace(/ß/g, 'ss');
    return value;
}
-%>
---
semester:
module:  <% module %>
buttons: "`<% replaceUmlauts(buttonId) %>`"
note_title:  <% fileName %>
note_type: "Dashboard level 2"
note_author: Nobody
note_creation_date: <% tp.date.now("YYYY-MM-DD") %>
note_creation_time:  <% tp.date.now("HH:mm:ss") %>
tags: [ " #dataview ", " #dashboard ", " #education/<% tagModule %> " ]

---

#education/<% tagModule %>

```button
name <% buttonName %>
type note(<% buttonTypeNote %>) template
action Template education - Document
color green
```
^<% replaceUmlauts(buttonId) %>


```dataview
	table WITHOUT ID link(file.link, note_title) as Document, document_date as Date, lecturer as "Lecturer", topic as Topic from #education
	WHERE note_type = "document" AND contains(tags, "#education/<% tagModule %>") sort file.name	
```
