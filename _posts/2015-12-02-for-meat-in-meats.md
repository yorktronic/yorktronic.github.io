---
layout: post
title: Ordering food for a wedding, using python
---

Yes, the post title is a little weird but just bear with me! I got married in late September
and since money was tight for the wedding, I ended up writing a python script that helped
to order exactly the correct amount of entrees. In the process of doing so I created what is
probably the most humorous `for` loop I'll ever create:
{% highlight python %}for meat in meats:{% endhighlight %}

Full source below!

{% highlight python %}

#############################################
#
# Calculates how much meat we should order from our caterer based on people's preferences,
# which were submitted via a google form and saved as a CSV
#
#############################################

# Import required libraries
import pandas as pd

# Import the csv as a pandas dataframe
df = pd.read_csv('./db/attendees.csv')

# Create a dictionary containing every entree item so we can store the counts
meats = {}

# The wedding is a self-serve bbq, and people can select multiple items, so we need to
# separate and properly weight each choice
for index, row in df.iterrows():
	# Check if there is a comma in the choice, which will indicate multiple choices
	# Note: if a given row['entree'] has a single item, running .split(', ') will just
	# return that item
	choices = row['entree'].split(', ')
	numChoices = len(choices)
	partySize = int(row['partySize'])

	# Loop through choices and add to dictionary
	for choice in choices:
		if meats.has_key(choice):
			meats[choice] += (1/float(numChoices)) * partySize
		else:
			meats[choice] = (1/float(numChoices)) * partySize

# Round all the values in meatOrder to two-point precision decimals
for meat in meats:
	meats[meat] = float("{0:.1f}".format(meats[meat]))
	print meat + ': ' + str(meats[meat])

# Print the meats breakdown and a sum of all meats
print "TOTAL: " + str(sum(meats.values()))

{% endhighlight %}

<strong>Everyone got what they wanted and ate until they couldn't eat anymore.</strong> And we didn't have much
leftover. Anyway, it's a simple little script but maybe it will be useful for people. If not, hopefully it's funny that I did this.

Hopefully!

/ty
