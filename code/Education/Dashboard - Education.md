---
buttons: "`button-education-module-1`"
note_type: Dashboard level 1
note_author: DerCarlauer
note_date_creation: 2023-08-04 09:42:49
tags:
  - "#dataview"
  - "#dashboard"
---

```button
name New module
type note(Untitled) template
action Template education - Dashboard level 2
color blue
```
^button-education-module-1

```dataview
	table WITHOUT ID link(file.link, module) as "Modules", semester as Semester, buttons as Buttons from #education
	WHERE note_type = "Dashboard level 2" sort semester desc, file.name	asc
```
