---
layout: post
title:  "Leaked Snapchat Data Uncovers Surprising Patterns"
date:   2014-01-08 17:12:16
---
A new year, a new data leak.

On New Year’s Eve an anonymous group or person leaked about 4.6 million Snapchat usernames along with the associated phone numbers, save for the last two digits.

The leak came about a week after Snapchat dismissed the threat – brought to their attention by Gibson Security - in a [blogpost](http://blog.snapchat.com/post/71353347590/finding-friends-with-phone-numbers): “Theoretically, if someone were able to upload a huge set of phone numbers, like every number in an area code, or every possible number in the U.S., they could create a database of the results and match usernames to phone numbers that way. Over the past year we’ve implemented various safeguards to make it more difficult to do. We recently added additional counter-measures and continue to make improvements to combat spam and abuse.”

Apparently their counter-measures weren’t enough.

Soon after the breach, the alleged hackers responded to requests for comment by _[The Verge](http://www.theverge.com/2014/1/1/5263156/alleged-snapchat-hackers-explain-how-and-why-they-leaked-data-on-accounts)_: “Our motivation behind the release was to raise the public awareness around the issue, and also put public pressure on Snapchat to get this exploit fixed,” they say. “Security matters as much as user experience does.”  Snapchat CEO responded to the breach in [this NBC interview](http://www.today.com/video/today/53971379): “We thought we had done enough.”

I examined the data to see if there’s anything we can learn.

What I discovered was something I hadn’t really thought of before, namely information encoded within other information.  A straight-forward example is geographical information being encoded in the first three digits of a telephone number. Looking at usernames, I learned that we humans sometimes include quite a bit of information about ourselves in those usernames – for example our actual, real name.  So a username can be more than just a username.

Let’s start by taking a look at the telephone numbers. We can see what users have been affected by this data breach by taking a look at the area codes of the phone numbers (to see if you are part of the leaked data, [you can search for your name here](http://lookup.gibsonsec.org/).) As mentioned in various reports, the leaks only affect North American users.  You can find the [list of North American phone numbers on Wikipedia](http://en.wikipedia.org/wiki/List_of_North_American_Numbering_Plan_area_codes): there are 323 American and 41 Canadian area codes.  After loading up the data in R (the application for statistical computing), I split the telephone numbers and counted the area codes.  There are 76 in total, two from Canada and the rest from the U.S. ([download CSV here](/files/Snapchat Area Code Frequencies and States.csv)).

Here are the top 10 area codes:

|Area Code|Frequency|State|
|---|---|---|
|815|215,953|Illinois|
|909|215,855|California|
|818|205,544|California|
|951|200,008|California|
|310|196,183|California|
|847|195,925|Illinois|
|720|188,285|Colorado|
|323|168,565|California|
|347|166,374|New York|
|917|165,420|New York|

Next I fired up SAP Lumira to take advantage of the great mapping features it has ([you can get your free copy here](http://go.sap.com/product/analytics/lumira.html)).  Here’s a choropleth map showing which states have been affected the most by the leak. If you live in a grey state, you’re not part of the leak.  If you’re in a green state, you may want to check to see if you’re data has been compromised ([you can check here](http://lookup.gibsonsec.org/)).

![Snapchat Data Map](/images/snapchat_leaks_image_1.png)

The leaked data also comes marked up with regional information below the state level, which after looking into a bit I’m confident is accurate.  Here are the top 10 regional locations affected by the leaks ([download CSV here](/files/Snapchat Regional Frequencies.csv)):

|Region|Frequency|
|---|---|
|New York City|334,445|
|Miami|222,321|
|Chicago Suburbs|215,953|
|Eastern Los Angeles|215,855|
|Los Angeles|209,888|
|San Fernando Valley|205,544|
|Southern California|200,008|
|Northern Chicago Suburbs|195,925|
|Denver-Boulder|188,285|
|Downtown Los Angeles|168,565|

As this dataset is incomplete, we can only really draw conclusions about what users have been affected by this leak.  Some larger urban areas – like my Philadelphia – are fairly low on the list. I wouldn’t conclude that Snapchat is unpopular there, simply that it wasn’t hit as hard.

Now let’s take a look at the usernames and see what kind of information is contained in those.  To start, we’ll just get a sense of how long these usernames are.  What we get is a nice, nearly normal distribution with a bit of right skew.  Looking at the data, I would guess that Snapchat requires a username of between 3 and 15 characters.  However, there are exactly 5 notable outliers (excluded in the histogram below), users for whom their email address has been published instead of their username (unless these 5 could choose to have their username be their email?).  I wonder how these 5 got to be included in this data set.

![Distribution of Name Length](/images/snapchat_leaks_image_2.png)

A lot of usernames appear to be people’s actual names.  After Googling random ones, it turns out it’s almost trivially easy to start connecting this data to additional information like names, pictures, Facebook accounts, Tumblr blogs, Twitter accounts, etc.

So what are popular names of Snapchat users?  I decided to count how many usernames started with an actual first name.  To get a list of first names to search against, I got a list of [popular baby names posted by the Social Security Administration](http://www.ssa.gov/oact/babynames/limits.html) and created a list of the top 50 boy and girl names (so 100 names in total) since 1980.  Next I counted how many times each name occurred at the beginning of a Snapchat username.  Of all Snapchat usernames, about 8% start with a top 100 name. Here’s the top 10 list of most common first names a username starts with:

1. John
2. Sarah
3. Ashley
4. Emily
5. Daniel
6. Ryan
7. Eric
8. Brian
9. Maria
10. Lauren

Another common pattern in usernames is to append a number at the end of your usernames.  How many numbers?

![Distribution of Length of Appending Digits](/images/snapchat_leaks_image_3.png)

Although two digits is the most common number of ending digits, we’ll take a look at four digits to get a better look at years.  What does this distribution look like?

![Distribution of Four Number Digits](/images/snapchat_leaks_image_4.png)

Clearly a lot of numbers other than years are chosen, so let’s zoom into the thick spike around the 1900s.  Also, let’s assume that the years are birth years and then turn the years into age.  Here is a five to 50 age distribution:

 ![Four Year Digits Converted to Age](/images/snapchat_leaks_image_5.png)

We see a big spike for age 13, which means many people chose to end their username in the number 2000.  Same for age 44: ending your username in 1969 was unusually popular.  I wouldn’t be surprised if the actual Snapchat age distribution looked similar to this.  We see the biggest change of users ranging in age from 13 to 23, so roughly middle school through college.  Keep in mind, however, that these conclusions are based on a number of assumptions and should be taken with a very large grain of salt.

Finally, there are all kinds of other factoids contained in these names.  The word “cat” occurs twice as many times as “dog”.  Lions are twice as popular as tigers.  There are over 5,000 sexy Snapchat users.  And so on.  A username is not just a username, but often tells us a bit more about the person lurking behind that name.

Gibson security has [some good advice](http://lookup.gibsonsec.org/) for those whose information has been compromised: you can delete your Snapchat account, change your phone number, and never give out your phone number if you don’t have to.  The moral of the story is that even super-popular services getting billion dollar buyout offers aren’t immune to user data leaks, so be sure you take your online privacy seriously.

_[This story was originall published on Forbes.](http://www.forbes.com/sites/sap/2014/01/08/leaked-snapchat-data-uncovers-surprising-patterns/)_