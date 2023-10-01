<%*
// https://github.com/DerCarlauer/obsidian-templater-script-organizer-education

const PATH = "/Education"
const AUTHOR = "Nobody"
const LECTURERS = ["Lecturer 1", "Lecturer 2", "Lecturer 3", "Lecturer 4", "Others"]
const CATEGORIES = ["Lecture","Self-study", "Other", "Tutorium", "Exercise", "Note"]
/*
This template is intended for the organization of lectures or other university documents. To keep it up to date and functional, the constants above this comment must be maintained.

PATH: This script places new documents in a target location. So in a folder inside the obsidian vault. The constant "PATH" defines the path to the destination folder. E.g.: "/level1/level2/destination-folder/".

AUTHOR: This should be the name of the owner of the Obsidian Vault. E.g.: "Donald Duck".

LECTURERS: The lecturers that become relevant during the study can be stored here. e.g.: ["Teacher1", "Teacher2"]

CATEGORIES For each module there are different occasions for which you want to create a document. These occasions can be defined here in the categories. e.g.: ["Lecture", "Self-study", "Other", "Tutorial", "Exercise", "Note"].
*/

//Fields are sorted alphabetically:
if (tp.file.title == "Untitled" || tp.file.title == "Unbenannt")  {
	var module = (await tp.system.prompt("Module description:")).trim()
} else {
	var module = tp.file.title
}

var lecturers = LECTURERS.sort()
var categories = CATEGORIES.sort()

//Dropdown menus are opened and values are assigned:
var lecturer = (await tp.system.suggester(lecturers, lecturers, false, "Lecturer:", 50)).trim()
var category = (await tp.system.suggester(categories, categories, false, "Category:", 50)).trim()

//For the hashtags, spaces are removed and everything is converted to lowercase:
var tagModule = module.replace(/ /g, '_').toLowerCase()
var tagCategory = category.replace(/ /g, '_').toLowerCase()

var dateYyyymmdd = tp.date.now("YYYY-MM-DD")
var dateDdmmyyyy = tp.date.now("DD.MM.YYYY")

//Create document name and file name:
var documentName = module + " - " + category
fileName = dateYyyymmdd + " " + documentName

//Name file and move it to the destination folder:
await tp.file.rename(fileName)
await tp.file.move(PATH + "/" + module + "/"+ fileName)
-%>
---
note_title: <% documentName %>
note_type: document
note_creation_date: <% tp.date.now("YYYY-MM-DD") %>
note_creation_time:  <% tp.date.now("HH:mm:ss") %>
note_author: <% AUTHOR %>
lecturer: <% lecturer %>
module:  <% module %>
topic:
document_date: <% dateDdmmyyyy %>
tags: [ " #education/<% tagModule %> ", " #<% tagCategory %> " ]

---
# <% documentName %>
#education/<% tagModule %>  #<% tagCategory %>
Dozent:in: <% lecturer %>
Datum: <% dateDdmmyyyy %>

---
