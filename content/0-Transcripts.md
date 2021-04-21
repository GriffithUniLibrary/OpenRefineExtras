---
title: Transcripts
nav: true
---
## Cleaning MS Azure speech-to-text transcripts

These steps will remove the additional rows which contain speaker and confidence information and split the time stamp from the transcript text.  It does not include steps to clean transcription errors.

Open Refine makes a copy of your transcript data, it does not use your raw transcript.  You can clean the transcript copy, then export the cleaned dataset.  

It is a good idea to name your transcripts with a convention that includes `raw` and `clean` in the file name.  You can also set up folders for all the raw and cleaned transcripts. 

-----

{% capture text %}
Upload the transcript file from your computer.
- Choose `Create Project`
- Select `Get data from this Computer`.
- Select `Choose Files` and browse to select the transcript file `yourfilename.txt` from the folder it is saved to.
- Either click `Open` or double-click on the filename to import it into OpenRefine.
- Click `Next`.{% endcapture %}
{% include card.md header="Create a project by uploading transcript file from your computer" text=text %}

{% capture text %}
OpenRefine gives you a preview to show you how it has interpreted the file you have uploaded or imported. 
The transcript data should be displayed as a `Line-based text file`. 
There are options to indicate whether the dataset has column headers included and whether OpenRefine should skip a number of rows before reading the data. 
- Choose `UTF8` as the method of encoding as this should convert any 'smart' formatting into plain text.
- Uncheck the `Store blank cells as nulls` box.  This will remove all the blank rows from the transcript.
- Check the `Ignore first` box add `1` line(s) at the beginning of file, to remove the first row which contains the total audio duration.
- Give the project a meaningful name such as `TranscriptXYZCleanV1`
- If all looks fine, click `Create Project`.
{% include card.md header="Preview and make changes" text=text %}

{% include figure.html img="ORPreviewTranscript.png" alt="Create Project" caption="Create a project in OpenRefine" width="75%" %}


{% capture text %}
This option will remove every row that contains `Speaker` and `Confidence` information and move the `time stamp` into a sepearte column or remove altogether.
- Go to Column `1`
- Click down arrow, choose `Facet > Custom Text Facet`
- In Expression box, type `value.contains(" | Confidence")`.  True & False results will display in Facet box.
- Select and include `true` results
- Go to `All` column, select `Edit rows > Remove matching rows`. Results now how only the transcript text lines. 
Move time stamp into separate column.
- Go to Column `1`
- Click down arrow, choose `Edit Column > Split into several columns`. Notice the time stamps all end in a separator with a space after `: `.
- Tick  `by separator` 
- At `Separator box` enter colon with a space after `: `.  N.B. The space is important, as there are other colons in the timestamp without spaces after. 
- Ok
You can now either remove the time stamp column or rename each column. To rename:
- Go to Column `1 1` (timestamp column)
- `Edit column > Rename this column`
- Enter new colun name ie. Time stamp
- Repeat for Column `1 2`
To remove
- Go to Column `1 1` (timestamp column)
- `Edit column > Remove this column`
- {% include card.md header="Option One - for transcripts that don't need to identify speakers" text=text %}


### Option Two - for transcripts that need to identify speakers
This option will 

{% include button.md text="Watch the steps above on this video" link="https://vimeo.com/412189056/0d9031def0" color="info" %}

  
<p align="center">
  <a href="https://griffithunilibrary.github.io/intro-data-wrangle/"><-- BACK</a> |
  <a href="https://griffithunilibrary.github.io/intro-data-wrangle/content/1-intro.html">NEXT --></a>
</p> 
