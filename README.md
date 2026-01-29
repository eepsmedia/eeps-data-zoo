# eeps-data-zoo
Data for analysis, mostly `csv`s suitable for CODAP.

## To add a new dataset (or edit the existing set)

There are three elements to coordinate:

* The "table of contents" of the zoo.
  This is in `Sites/eeps-data-zoo/zoo-toc.json`.
* The data file, which can be a `csv` or a `codap` file.
  Put this file into `Sites/eeps-data-zoo/cages/`.
* Background information on the data. This usually shows up in a Notion page (but could be anywhere). Search for "zoo".

### Key things to realize

On my computer, these files live in `Sites/eeps-data-zoo/`. NOT `Sites/eeps/`! You'll use that for the underlying software.

Don't worry about ftp-ing the files. 
Unlike everything else I do, I was smart this time.

The underlying software gets the toc and the data files _from github_.

That means that you edit the toc and maintain the files using a git-compatible IDE such as IntelliJ IDEA.
Simply 

* Put the data file into the "cages" directory and add it to git.
* Edit the `zoo-toc.json` file and save it.
* Commit the changes
* Push that commit.

And shazam! The site is updated.

### `zoo-toc` format

Typically:
```
    "titanic-passengers": {
      "name": "Titanic passengers",
      "rows": 1309,
      "columns": 14	,
      "filename": "titanic-passengers.csv",
      "keywords" : "people, disasters, classification",
      "blurb" : "1309 passenges from the Titanic. Who has the best chance of surviving? Famous dataset!",
      "infoUrl" :   "https://www.notion.so/eeps/eeps-data-zoo-9f5286dad5744fcca334d8741806e521?source=copy_link#27afe7c5e7ee802eb935d94c3d32cbef"
    },
```
If the data are in `.codap` format, it will look like this:

```
  "fishers irises": {
    "name": "Fisher's irises",
    "rows": 150,
    "columns": 6,
    "sharedUrl": "https://codap.concord.org/releases/latest/static/dg/en/cert/index.html#shared=https%3A%2F%2Fcfm-shared.concord.org%2FuuqhmMMfi5yL4eaZ1odq%2Ffile.json",
    "keywords" : "classification,machine learning,plants",
    "blurb" : "Famous dataset! Measurements of three different species of iris. Can you tell them apart?",
    "infoUrl" :   ""
  },
```

### URL format

When making a url to render the file directly in CODAP, use this format:
```
https://codap.concord.org/app?url=https://raw.githubusercontent.com/eepsmedia/eeps-data-zoo/main/cages/coins.csv
```

## Underlying software

The underlying software is elsewhere and has to be uploaded to the eeps site,
which of course is actually in `codap.xyz/eeps`.

Online, you'll find the relevant files in two places:
* `/public_html/eeps/zoo/index.html` is the root html file.
* `/public_html/eeps/js/zoo.js` is the javascript that it uses to retrieve and render the data.

On my computer, these are in the `Sites/eeps/` folder, not in `Sites/eeps-data-zoo`.

