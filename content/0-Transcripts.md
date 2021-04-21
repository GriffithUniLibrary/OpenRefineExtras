---
title: Transcripts
nav: true
---
## Clean MS Azure speech-to-text transcripts

These steps will remove the additional rows which contain speaker and confidence information and split the time stamp from the transcript text.  It does not include steps to clean audio transcription errors.

Open Refine makes a copy of your transcript data, it does not use your raw transcript.  You can clean the transcript copy, then export the cleaned dataset.  

It is helpful to name your transcripts with a convention that includes `raw` and `clean` in the file name.  You can also set up folders for all the raw and cleaned transcripts. See [Reproducible Research Steps] for more.

-----

{% capture text %}
Upload the transcript file from your computer.
- Launch OpenRefine [instructions](https://griffithunilibrary.github.io/intro-data-wrangle/content/2-lesson.html)
- Choose `Create Project`
- Select `Get data from this Computer`.
- Select `Choose Files` and browse to select the transcript file `yourfilename.txt` from the folder it is saved to.
- Either click `Open` or double-click on the filename to import it into OpenRefine.
- Click `Next`.{% endcapture %}
{% include card.md header="Upload the transcript file and create a project" text=text %}

{% capture text %}
OpenRefine gives you a preview to show you how it has interpreted the file you have uploaded or imported. 
The transcript data should be displayed as a `Line-based text file`. 
These next steps will start the cleaning process, then open the project.
- Choose `UTF8` as the method of encoding as this should convert any 'smart' formatting into plain text.
- Uncheck the `Store blank cells as nulls` box.  This will remove all the blank rows from the transcript.
- Check the `Ignore first` box add `1` line(s) at the beginning of file, to remove the first row which contains the total audio duration.
- Give the project a meaningful name such as `TranscriptXYZCleanV1`
- If all looks fine, click `Create Project`.{% endcapture %}
{% include card.md header="Preview and make changes" text=text %}

{% include figure.html img="ORPreviewTranscript.png" alt="Create Project" caption="Create a project in OpenRefine" width="100%" %}

{% capture text %}
This option will remove every row that contains `Speaker` and `Confidence` information and move the `time stamp` into a separate column or remove altogether.
- Go to `Column 1`
- Click down arrow, choose `Facet > Custom Text Facet`
- In Expression box, type `value.contains("| Confidence")`.  True & false results will display in Facet box.
- Select and include `true` results
- Go to `All` column, select `Edit rows > Remove matching rows`. Results now how only the transcript text lines. 

Move time stamp into separate column.
- Go to `Column 1`
- Click down arrow, choose `Edit Column > Split into several columns`. Notice the time stamps all end in a separator with a space after `: `.
- Tick  `by separator` 
- At `Separator box` enter colon with a space after `: `.  N.B. The space is important, as there are other colons in the timestamp without spaces after. 
- Ok

You can now either remove the time stamp column or rename each column. 
To rename:
- Go to `Column 1 1` (time stamp column)
- `Edit column > Rename this column`
- Enter new colun name ie. Time stamp
- Repeat for `Column 1 2`

To remove the column:
- Go to `Column 1 1` (time stamp column)
- `Edit column > Remove this column`

To export results:
- Go to `Export` button and export results in required format.  
- Select `Comma-separated value (.csv)` file format for structured data in columns. The file will save with the `project name` into your `Downloads` folder.

or
- `tab-separated value (.tsv)` format
- Select  `open with Notepad` 
- Select  `File > Save As > .txt ` {% endcapture %}
{% include card.md header="Option One - for transcripts that don't need to tag different speakers" text=text %}

{% capture text %}
This option will retain each individual speaker tag, rename them, and remove the confidence rating and time stamp information.
- Go to `Column 1` 
- Select `Text filter`
- Enter speaker name ie. `Speaker 1 |`. Results will display rows containing this text.
- Go to `Column 1` 
- `Edit cells > Transform`
- In Expression box, delete `value` and enter the speaker details within quotation marks ie. `"Interviewer: "` or `"John: "` or using a de-identified ID number ie. `"ID 27456"` which is documented securely elsewhere.
- Ok
- Repeat these steps for each Speaker in the transcript.

Remove time stamps
- Go to `Column 1`. Notice the time stamps all end in a separator with a space after `: `.
- `Edit cells > Split mulit-value cells`
- Tick  `by separator` 
- At `Separator box` enter colon with a space after `: `.  N.B. The space is important, as there are other colons in the timestamp without spaces after. 
- Ok. New rows are displayed containing the time stamps.
- Go to `Column 1`
- `Text filter` 
- Tick `regular expression` box and type: `\d\d\W\d\d\W\d\d` (you can copy and paste this into the box). This identifies and filters by the format of the time stamp ie. 00:10:23 as digit, digit, non-word character, digit, digit, non-word character, digit, digit. 
- Select `All` Column
- `Edit rows > remove matching rows` 
- Close Facet box
- Results will display transcript text without time stamps.{% endcapture %}
{% include card.md header="Option Two - for transcripts that need retain speaker tags" text=text %}

{% include button.md text="Watch the steps above on this video" link="https://vimeo.com/412189056/0d9031def0" color="info" %}
