---
layout: post
title:  "Hanukkah or Chanukah? A Look at the Data Reveals an Emerging Consensus"
date:   2013-11-26T18:18:26
---
<iframe src="https://player.vimeo.com/video/8264593" width="740" height="555" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>
["How Do You Spell Channukkahh?"](http://vimeo.com/8264593) is the title of song recorded by The LeeVees, and for this year's Hanukkah holiday I wondered if we could answer the question once and for all.
 
The Hebrew word for Hanukkah is חנוכה. But what is the English transliteration? Hanukkah? Chanukkah? Hannukah?  To find out and settle the question for good (or at least put you on the right side of history), I decided to take a look at the data.
 
We'll look at three data sources: SAP's Social Media Analytics by NetBase, Google Search Trends, and Google Ngram Viewer, which shows us how often a particular term has been used in books.  The confusion around the spelling is wether it begins with a C or an H, and just how many N's and K's are required. The spellings we'll consider are:

* Hanukah
* Hanukkah
* Hannukah
* Hannukkah
* Chanukah
* Chanukkah
* Channukah
* Channukkah

First up, SAP Social Media Analytics by NetBase, which will give us access to a broad set of social data, including Twitter, Facebook, forums, blogs, and more.  Figure 1 shows the number of mentions of each spelling over the past year, and the spelling favorite is clear: Hanukkah.  Chanukah and Hannukah pull in a distant 2nd and 3rd.  The bottom three spellings are so infrequent that we could chalk them up to spelling mistakes.

![Figure 1 - Hanukkah Mentions Netbase Absolute](/images/2013-11-26/Figure 1 - Hanukkah Mentions Netbase Absolute.jpg)
 
So how does this compare to our other data sources?  Next up, Google searches.
 
Google provides a wealth of interesting public information, including data on people's search history.  You can study searches via the Google Trends tool; for example, [here is a simple comparison between "hanukkah" and "chanukah" going back to 2004](http://www.google.com/trends/explore?q=hanukkah%2C+chanukah).  The scale is a bit wonky to understand since they don't provide the absolute search volume of a term.  Rather, everything is scaled using the maximum point on the graph.  So in essence, one unit equals 1/100th of the search volume of the term which had the highest search volume for a period of time on the graph ([you can read Google's explanation here](https://support.google.com/trends/answer/87285?hl=en)).

![Figure 2 - Hanukkah Google Search Share 12 Months](/images/2013-11-26/Figure 2 - Hanukkah Google Search Share 12 Months.jpg)

Let's start by comparing how often each spelling is used in Google searches over the past year vis-a-vis each other.  We can see that the top three spellings make up roughly the same share in Google searches as they do in the NetBase dataset.  Beyond the top three (which together account for 96% of spelling variants) the bottom diverges a bit more; for example, while "hanukah" appears on 0.03% of the time in the NetBase data it makes up 2% of the share here.  Since the Google data is less granular I suspect these small difference are due to noise.
 
In the end, we draw the same conclusion: **about three out of four people spell the Jewish holiday Hanukkah, no C, one N and two K's.**
 
Now the interesting thing about the Google data is that we can go back in time to see if there are any interesting patterns to detect.  I collected the data for our search terms going back to 2005.  Unsurprisingly, search volume dramatically peaks each year around the time that Hanukkah takes takes place.  In order to more easily compare year-over-year changes, I looked at only the three weeks before, during, and after the week in which the first day of Hanukkah fell (it varies each year).  What I found was pretty interesting.

![Figure 3 - Share of Google Search Results Timeline](/images/2013-11-26/Figure 3 - Share of Google Search Results Timeline.jpg)
 
As you can see in Figure 3, it appears that **a consensus is emerging on how to spell Hanukkah.**  The current dominant spelling variant was much less so in 2005, where it accounted for roughly 30-35%.  That means over the past decade, adoption of this spelling variant has doubled, mainly at the expense of the other two spelling variants that begin with H.  For the C variants, Chanukah remains the most popular option, with the other variants slowly fading away.
 
Finally, we can go even further back in time by means of Google's ngram data set of the books its scanned.  An ngram is a continous sequence of items from a text; it can include single words, syllables, or sentence fragments.  You can explore Google's data set with its [ngram viewer](https://books.google.com/ngrams), or [download the data itself here](http://storage.googleapis.com/books/ngrams/books/datasetsv2.html).  I downloaded the 1-gram data (single words) for 'c' and 'h' and loaded it into R.  What I was interested in is how many books each spelling variant appeared in.

![Figure 4 - Number of Books Containing Spelling Variant](/images/2013-11-26/Figure 4 - Number of Books Containing Spelling Variant.jpg)
 
Figure 4 shows the number of books that each spelling appeared in from 1950 to 2008 (the latest year that Google provides data for).  While this show us that there's been an exponential  increase of the mentions of the holiday in books since 1980, we can compare spelling popularity more easily by comparing the share of spellings. 

![Figure 5 - Share of Books Containing Spelling Variant](/images/2013-11-26/Figure 5 - Share of Books Containing Spelling Variant.jpg)

Figure 5 shows us the relative frequency with which each spelling variant has been used. The first thing to notice is that the proportions of each roughly match our previous two data sets.  But here the long-term trend has been a bit more stable.  The "Hanukkah" spelling does seem to gain a bit more share after 1980, and in general some of the less popular spellings decrease over time.
 
If you want to know how to spell Hanukkah, you're best bet is **Hanukkah**, but you'll be in good company if you prefer **Chanukah**.  The advantage of using several different data sets is that we can be more comfortable in our conclusions if the data reinforce one another, and in our case we were also able to inspect trends over different time horizons.
 
Happy Hanukkah!

<iframe width="740" height="555" src="https://www.youtube.com/embed/Rd1Pyu9_rxo" frameborder="0" allowfullscreen></iframe>