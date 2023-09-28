(Chap_Pandas)=
# Pandas

ACME materials link...


# Exercises

1. Consider the following GDP per capita data (in constant 2011$, source: [Maddison Project Database](https://www.rug.nl/ggdc/historicaldevelopment/maddison/releases/maddison-project-database-2020?lang=en)):
|                | IND | MYS | USA | ZAF|
|----------------|----|----|----|----|
| 1990        |  2,087  | 8,179   | 36,982   |  6,111  |
| 2000         |  2,753  | 13,475   |  45,886  |  7,583  |
| 2010         | 4,526   |  18,574  |  49,267  | 11,319   |
| 2018 |   6,806 |  24,842  | 55,335   | 12,166   |

Create a dictionary with keys `Year`, `IND`, `MYS`, `USA`, and `ZAF` and values that are lists of the GDP per capita data for each country.  Create a DataFrame named `df` from this dictionary.  Print the DataFrame.

2. Inspect this data frame.  Print `df.head(3)`.  Print `df.tail(3)`.  Get a list of column names with the `keys` method.  Finally, use the  `describe` method to print descriptive statistics.
3. Pandas DataFrames use an index to keep track of rows.  Not the default index in `df` are integers for each row.  Let's change the index so the year is the index value. Print the updated DataFrame.
4. Let's reshape this into a long panel format with a [`MultiIndex`](https://pandas.pydata.org/docs/user_guide/advanced.html) for the columns.  The first level of the `MultiIndex` should be the country name and the second level should be the year.  The values should be the GDP per capita.  To do this, use the `pivottable` or `stack` methods of the DataFrame class. Please print the resulting DataFrame.
5. Create a new variable that is the growth rate in GDP  period capita from the prior period measure. To do this,  you will use `groupby` to find growth rate for each country over the sample.
6. The DataFrame object has several methods to help output a formatted table suitable for reports or presentations. Use one of these methods to print a DataFrame formatted as a [markdown](https://www.markdownguide.org/basic-syntax/) table.
7. In most cases, you are likely to use a DataFrame as a container for a large dataset, not something simple that you can enter by manually as we did above.  Pandas has [several methods](https://pandas.pydata.org/docs/user_guide/io.html) to read in data from files are various formats.  Let's use one of these methods to read in some population data extracted from the [United Nations' World Population Prospects](https://population.un.org/wpp/).  Note that Pandas will download these data for you if you have a URL to the data file.  The URL for these data on South Africa's population is: [https://raw.githubusercontent.com/EAPD-DRB/OG-ZAF/main/ogzaf/data/demographic/un_zaf_pop.csv](https://raw.githubusercontent.com/EAPD-DRB/OG-ZAF/main/ogzaf/data/demographic/un_zaf_pop.csv).  Please read in these data (Note: the separator is the verical bar ("|") and the header is on the second line (in Python this has index 1, so you'll want to use the argument `header=1`)).  Print the first 5 rows of the DataFrame.
8. Now we'll select a subset of this DataFrame.  Please create a new DataFrame called `zaf_pop` that contains only the columns `AgeId`, `Value` and only rows where `SexId=3` (i.e., both sexes are included), `TimeLabel=2021` (i.e., only values for the year 2021). Print the first 5 rows of the DataFrame.
9. With your new `zaf_pop` DataFrame, rename the column `Value` to `Count`. Create a new variable in the DataFrame called `Density` that is the fraction of the total population for each age. Print the first 5 rows of the DataFrame.
10. Use the `plot` method to plot the population density across age for South Africa.
11. It's often the case that we need to combine more than one dataset.  Pandas offers a few options to do this, including the [`merge`] and [`join`](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.join.html) methods of the DataFrame class. Let's test this, but reading in the original data again, and finding the population of women in 2021.  Then use `merge` or `join` to combine the `zaf_pop` and `zaf_female_pop` DataFrames.  Plot the density of women and the overall population together.
12. Save your final DataFrame to disk as a csv file.