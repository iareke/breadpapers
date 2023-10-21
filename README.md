[//]: # "Title: BreadPaper"
[//]: # "Author: Fabio Iareke"
[//]: # "Date: 2019-07-05"
[//]: # "Comments: BreadPaper about BreadPapers stuff"

# BreadPaper

# Abstract

Description of Bread Paper Technology: philosophy, history, approach, techniques, the stuff of life, the universe and everything else.

# Bread Paper Philosophy

Since the early days of my career i was crazy about documenting the things i do. Why? Because i forget things, specially those little details that a first glance seems to be insignificant but turned to be important. What the hell, like is said: "the devil is in the details". I needed to retrieve them from the catacombs of my mind and could not do it, then my _alfarrábios_ bad written, almost not understandable with my grotesque handwriting, saved the world many more times that i remember.

As the time passes by the amount of information tends to grow and with it the difficulty to search for a specific piece of data. 

...

Where to write: anywhere you can read in the future.

Like the attendant / owner of the neighbourhood old groceries store that sells everything, usually called here _mercearia_, when he is going to calculate the values of your items: he takes the pen from behind the ear and searches for a paper to do the math under the desk but normally that is not there, then he takes a piece of the bread paper that is always at hand and do the calculation. I loved that workaround since i was a child and went there to buy candies.

There is a methodology in there.

That piece taken from the bread paper cannot be used again to hold the bread (or at least should not!) so there is two courses of action now: trow in the trash or store it for future use, like to verify the store's incomings. Normally goes to the trash, of course, all the transactions there runs by owner itself and he knows the transactions of the day by heart.

# Bread Paper Technology

Initially the main objective of Bread Papers was to document a procedure for a fast deployment.

## File Header

Every time is the same shit: the file was moved, imported, edited, copied, processed by the motherfucker NAS changing the file's metadata (ownership, permissions, [c,m,a]date, etc), whatever, the 'file system' where the file resides not always guarantees the consistency of the file's metadata information. 
So, it is very useful, not to say quite important, to have at least the file's creation date information and the author to track the historic information. This information may be lost in the technology shenanigans.

### Minimal File Header

```
Title: Title of the document
Author: Author Name
Date: YYYY-MM-DD
Version: N[.N]{0,}
```

```markdown
[//]: # "Title: Title of the document"
[//]: # "Author: Author Name"
[//]: # "Date: YYYY-MM-DD"
[//]: # "Version: N[.N]{0,}"
```

### Basic File Header

```
Title: Title of document
Author: Author Name
Date: YYYY-MM-DD
Version: N[.N]{0,}
File: filename
Summary: 
```

```markdown
[//]: # "Title: Title of the document"
[//]: # "Author: Author Name"
[//]: # "Date: YYYY-MM-DD"
[//]: # "Version: N[.N]{0,}"
[//]: # "File: filename"
[//]: # "Summary: "
```

### File Header with versioning history

CSV (Comma Separated Values) -> SSV (Semicolon Separated Values)

```markdown
[//]: # "Title: Title of the document"
[//]: # "Author: Author Name;;Another Author"
[//]: # "Date: YYYY-MM-DD;YYYY-MM-DD;YYYY-MM-DD"
[//]: # "Version: N[.N]{0,};N[.N]{0,};N[.N]{0,}"
[//]: # "File: filename"
[//]: # "Summary: "
```

Processing tools can have especial format of metadata information, like [pandoc][] with it's [metadata blocks](https://pandoc.org/MANUAL.html#metadata-blocks)

```
% title
% author(s) (separated by semicolons)
% date
```

[pandoc]: https://pandoc.org

# The Surprising Power of Documentation

https://vadimkravcenko.com/shorts/proper-documentation/