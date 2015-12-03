---
layout: post
title: Education v. GDP by Country 
---

Right now I'm working on an analysis of the number of years people spend being educated (which is called "School Life Expectancy" by the UN) as it relates to national GDP. Here's the <a href="http://web.archive.org/web/20110514112442/http://unstats.un.org/unsd/demographic/products/socind/education.htm" target="_blank">education dataset provided by the UN</a>, and <a href="http://api.worldbank.org/v2/en/indicator/ny.gdp.mktp.cd?downloadformat=csv" target="_blank">GDP data courtesy of the World Bank</a>. Since you're unlikely to open either data set and view it, I'll give you a quick summary: there is data, there is more than I need to solve this problem, and about 18% of the country names don't match due to differences in spelling, abbreviation, punctuation, etc. So, a typical data science problem :)

To start out I figured I'd look and see what specific countries were in the education dataset but not in the GDP dataset, which logically includes both countries that are named differently in either dataset, as well as countries that simply may not be in the GDP dataset. The results are:

{% highlight python %}
['Anguilla', 'Bolivia (Plurinational State of)', 'British Virgin Islands', 'Cape Verde', 'China, Hong Kong SAR','China, Macao SAR','Congo','Cook Islands', "Cte d'Ivoire",'Democratic Republic of the Congo', 'Egypt', 'Gambia', 'Iran (Islamic Republic of)', 'Kyrgyzstan', "Lao People's Democratic Republic", 'Libyan Arab Jamahiriya', 'Montserrat', 'Nauru', 'Netherlands Antilles', 'Niue', 'Occupied Palestinian Territory', 'Republic of Korea', 'Republic of Moldova', 'Saint Lucia', 'Saint Vincent and the Grenadines', 'Slovakia', 'TFYR of Macedonia', 'Tokelau', 'United Kingdom of Great Britain and Northern Ireland', 'United Republic of Tanzania', 'United States of America', 'Venezuela (Bolivarian Republic of)', 'Viet Nam', 'Yemen']
{% endhighlight %}

So some are named in a not so smart way, others are territories that belong to other countries, and for all I know, some could be countries that don't even exist anymore, considering the UN data is from the Wayback Machine. Great. I then used <a href="https://github.com/seatgeek/fuzzywuzzy" target="_blank">FuzzyWuzzy</a>, to try to throw fuzzy string matching at the problem, but for this particular scenario the results were about 50% accurate and there is no unsupervised way to actually [accurately] make use of the results.

From talking to some people on Thinkful's Slack channel, as well as to some programming buddies, I think I have two options: 1) Build a translation table with keys corresponding to some standard naming convention for countries, and then have the naming conventions from the education and gdp datasets as values (or two translation tables, not sure which would be more efficient) and / or 2) Use an API call to <a href="https://restcountries.eu/" target="_blank">REST Countries</a> to see if we can get those 34 mismatches down to a more manageable number.

I realize that I could just manually fix this problem in Excel or something, but I'm stubborn and so instead I'm going to build a python script that takes in a list of country names and returns a dictionary that contains the properlly formatted names as keys, and the poorly formatted names as values. If it's unable to match a properly formatted key, it'll just have blank text as the value in the key-value pair. Or something like that. More to come.

<a href="https://github.com/yorktronic/data_science/tree/master/thinkful/Unit3/data_scraping" target="_blank">analysis source code</a>

/ty 