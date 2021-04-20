---
title: Transcripts
nav: true
---
## Cleaning MS Azure speech-to-text transcripts

These steps will remove the additional rows which contain speaker and confidence information and split the time stamp from the transcript text.  It does not include steps to clean transcription errors.

Open Refine makes a copy of your transcript data, it does not use your raw transcript.  You can clean the transcript copy, then export the cleaned dataset.  

It is a good idea to name your transcripts with a convention that includes `raw` and `clean` in the file name.  You can also set up folders for all the raw and cleaned transcripts. 

-----

### Create a Project

Upload the transcript file from your computer.

{% capture text %}
- Choose `Create Project`
- Select `Get data from this Computer`.
- Select `Choose Files` and browse to select the transcript file `yourfilename.txt` from the folder it is saved to.
- Either click `Open` or double-click on the filename to import it into OpenRefine.
- Click `Next`.{% endcapture %}
{% include card.md header="Create a project by uploading transcript file from your computer" text=text %}

### Preview the data

OpenRefine gives you a preview to show you how it has interpreted the file you have uploaded or imported. The transcript data should be displayed as a `Line-based text file`. 

There are options to indicate whether the dataset has column headers included and whether OpenRefine should skip a number of rows before reading the data. 
- Choose `UTF8` as the method of encoding as this should convert any 'smart' formatting into plain text.
- Check the `Store blank cells as nulls` box.  This will remove all the blank rows from the transcript.
- Check the `Ignore first` box add `1` line(s) at the beginning of file, to remove the first row which contains the total audio duration.
- Give the project a meaningful name such as `TranscriptXYZCleanV1`
- If all looks fine, click `Create Project`.

{% include figure.html img="ORPreviewTranscript.png" alt="Create Project" caption="Create a project in OpenRefine" width="75%" %}


{% include button.md text="Watch the steps above on this video" link="https://vimeo.com/412189056/0d9031def0" color="info" %}

  
<p align="center">
  <a href="https://griffithunilibrary.github.io/intro-data-wrangle/"><-- BACK</a> |
  <a href="https://griffithunilibrary.github.io/intro-data-wrangle/content/1-intro.html">NEXT --></a>
</p> 
