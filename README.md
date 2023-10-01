# obsidian-templater-script-organizer-education
Creates documents for your studies with a few clicks. Stores them in a structured way. Displays them in dashboards.
## Overview
![Example of Templater Script. Creating some documents for different modules.](/example_templater_script.mp4)

If you are studying, you can use this setup to store your documents in a structured way. The script is not perfect, but it works for the workflow I show in the video.

## Pre-conditions
* [Obsidian](https://obsidian.md/)
    * [Templater Plugin](https://silentvoid13.github.io/Templater/) (You will have to enable User System Commands)
    * [Dataview Plugin](https://blacksmithgu.github.io/obsidian-dataview/)
    * [Buttons Plugin](https://github.com/shabegom/buttons)
## Installation
1. Install Obsidian and the above listed community plugins
2. Configure Templater Plugin options
    1. Make sure, that "User System Commands" are enabled
    2. Define a folder inside your vault as "Template folder location"
3. Copy the files "Template education - Document" & "Template education - Dashboard level 2" into your above defined "Template folder location"
4. Copy the folder "Education" and its content into your vault
5. You can now test the script - Go to "Education/Dashboard - Education" and click the Button "New module"
## Configuration
### Configuration of File: "Template education - Document"
This template is intended for the organization of lectures or other university documents. To keep it up to date and functional, the constants on the top of the file must be maintained:
* PATH: This script places new documents in a target location. So in a folder inside the obsidian vault. The constant "PATH" defines the path to the destination folder. E.g.: "/level1/level2/destination-folder/".
* AUTHOR: This should be the name of the owner of the Obsidian Vault. E.g.: "Donald Duck".
* LECTURERS: The lecturers that become relevant during the study can be stored here. e.g.: ["Teacher1", "Teacher2"]
* CATEGORIES For each module there are different occasions for which you want to create a document. These occasions can be defined here in the categories. e.g.: ["Lecture", "Self-study", "Other", "Tutorial", "Exercise", "Note"].
### Configuration of File: "Template education - Dashboard level 2"
This file is intended to create the dashboard for a module. The dashboard will show the documents of the specific module. To configure it, you will have to maintain the constant PATH on the top of the file. This Path defines, where new module dashboards will be created.