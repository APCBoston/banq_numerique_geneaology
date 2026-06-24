# BanQ Numérique Geneaology Assistant

[![CC BY-SA 4.0][cc-by-sa-image]][cc-by-sa]

[cc-by-sa]: http://creativecommons.org/licenses/by-sa/4.0/
[cc-by-sa-image]: https://licensebuttons.net/l/by-sa/4.0/88x31.png
[cc-by-sa-shield]: https://img.shields.io/badge/License-CC%20BY--SA%204.0-lightgrey.svg

This repository houses an AI-assisted workflow for Geneaological research in 19th century Quebec.  In particual, I created this to help me with a reccurring problem: once I identified an ancestor's date and place of birth, I needed to download the digitized baptismal record from the Quebec National Library and Archive Online, or [BanQ Numérique](https://numerique.banq.qc.ca/).  But these archives are tough to decipher.  They are the handwritten scrawl of a priest, often faded, digitized over a century later.  They contain scribal abbrevations that are unfamiliar to me--and also I don't read French!

This tool consists of a Claude skill that allows you to dump zip files with dozens of these records into Claude Cowork, go do anything else for a while, and have Claude make you a very nice bilingual transcript of the records.  I've been using it for a few days, I've found it HIGHLY reliable, and so I am releasing it into the wild, in the hope, as they say, that it will be useful.  This will, of course, also work on documents from the Drouin Collection--which is just a different digitization of the same source material.

## How to use with Claude Cowork

### Install the skill
Go to https://claude.ai/customize/skills and click the plus button.  Select "upload a skill" and drag the whole skill.zip file into the box.  You should only need to do this once.  

### Find your parish registry in BanQ Numérique

Go to https://numerique.banq.qc.ca/ and enter the word `Registres` followed by the parish name in the search box.  This is nearly always Saint- or Sainte-somebody, with a hyphen and no space, like Sainte-Helene.  You need to spell the saint's name exactly right--there's no "sounds like" match and Guillame will not match Guillaume or Guillarne.  However, you do not need to get the saint's gender (Saint/Sainte) right.  You cannot abbreviate St or Ste.  If you see a longer name like Sainte-Somebody-de-Somewhere, just put in Sainte-Somebody for now.  The rest of it is the location, which we'll get to in a minute.  Go ahead and hit enter, or click the button to search

### Filter the results

You will now have a long and mystifying list of results in French.  The browser auto-translate is quite good but it can still be overwhelming.  So want to filter by "civil registers," so go ahead and click `Registres de l'état civil` in the filters.  In the case shown below, this reduced the results from 5,426 to 5.
<img width="1069" height="603" alt="image" src="https://github.com/user-attachments/assets/5fca912a-b7fa-4d20-9b1e-b73ae2a31f9c" />

### Select the desired archive

Here you probably have a list of records corresponding to parishes with the same Saint name in different places, and with different start and end years.  Remember when we talked about saint-somebody-de-somewhere?  This is where you find the one that says "somewhere!"  BAM!

### Select the desired year

You should now see a screen like the one below with digital images, and a variety of menus on the left.  From the `Fichiers` list, select the correct year.  You should now be looking at the certification page (where the priest certified to the Superior Court judge that the records were true and complete, and the judge took a copy into the Court's civil register)

<img width="1495" height="1560" alt="image" src="https://github.com/user-attachments/assets/3555adbc-05fe-44d1-82dc-a87fc8a37098" />

### Batch download

I like to download the entire year's file.  You can learn a lot about the life of a rural village by perusing just a few months of these records.  On the left sidebar, select  Téléchargement en lot  (batch download).  Agree to the terms of service and enter the page number(s) you want, in groups of up to 50.  You'll have to repeat this process for the index.

### Throw it in the hopper

Drag and drop the .zip files you just downloaded into Claude Cowork.  Don't worry about unzipping them--it's actually easier not to.  You can prompt claude by just typing `/quebec-parish-register` into the chat box, or even nothing at all.  You do need to select the model--I find it works _okay_ with Sonnet 4.8 and _great_ with Opus 4.8-high.  I would not have Hauku even attempt this task.  If you give it a little context on the people you're interested in and the goals of your research, it will highlight those people and call interesting facts to your attention.  Or you can just have it translate and transcribe.

For larger groups of records, Claude will need multiple "turns" (prompt and response) to get through them all.  Every 20 minutes or so, you'll get a chat with a progress update and something like "shall I continue?"  Just tell it to continue and let it do its thing.
