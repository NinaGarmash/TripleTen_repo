# #9.Project: Videogame Market

**Description of the data:**
User and expert reviews, genres, platforms (e.g. Xbox or PlayStation) on game sales from open sources gathered for the online store Ice selling videogames all over the world.
**Task:**
to analyze sales, to find market trends per region.

Libraries used: pandas, numpy, matplotlib, seaborn, scipy,sidetable.

**Results:**
After EDA A user profile for each region was created.
- Top 5 profitable platforms and Top 5 genresfor each region were revealed. There's strong positive correlation between rating and sales in NA and EU(0.98). No correlation found between these regions and JP: 0.025 for NA and JP, 0.016 for EU and JP. 2 hypotheses were tested:
- Average user ratings of the Xbox One and PC platforms are the same.
- Average user ratings for the Action and Sports genres are different.

Both hypotheses were accepted.
