(Chap_OGcalibration)=

# Calibrating the `OG-Core` model

As noted in the introduction, the `OG-Core` model must be parametrized to represent a specific country. We refer tot he process of finding parameter values that represent a specific economy as "calibration".  Because data sources for country-specific data differ, there's not a single way to calibrate all economies. We there for have created country-specific calibration packages.   Some examples of these include the [United States](https://github.com/PSLmodels/OG-USA), the [United Kingdom](https://github.com/PSLmodels/OG-UK), [South Africa](https://github.com/EAPD-DRB/OG-ZAF), [India](https://github.com/Revenue-Academy/OG-IND), and [Malaysia](https://github.com/Revenue-Academy/OG-MYS).

In this chapter, we describe the process of creating a country-specific calibration and provide exercises related to certain components of that calibration.  We will use as an example the calibraiton of `OG-Core` to South Africa, in the [`OG-ZAF`](https://github.com/EAPD-DRB/OG-ZAF) package.


# Demographics

A key feature of OG models is the ability to model the impacts of economic shocks or policy changes across generations. Because they capture generations of finitely-lived agents, OG models can be made to reflect realistic demographics.  Demographic trends are of massive importance to economic trends [add CITATIONS here]. And there is a tremendous amount of variation in these trend across countries.  Consider Figure \ref{fig:pop_growth}, which shows the population distributions, and their evolution over time, for three countries: South Africa, India, and the United States. In each figure, we plot the 2023 population distribution (according to data from the [UN World Population Prospects](https://population.un.org/wpp/)) and then the evolution of the population as we age it forward two, 40, and 80 years and then to it's steady state distribution using the `demographics.py` model from the relevant country calibration (i.e., `OG-ZAF`, `OG-IND`, `OG-USA`). Comparing the 2023 distributions first, we see that South African distribution has humps, which reflect the initial wave of the HIV epsidemic and then it's echo on the next generation.  India also has more young adults than most other countries, but show a relatively flat gradient as the number of individuals decline quickly with age, reflecting relatively high mortality rates in that country.  The United States has a more right skewed distribution than South Africa and India, with more individuals of high age, reflecting relatively low mortality rates for adults. As each population is simulated forward in time, we see the age distribution move to the right, with more older individuals.  After just about 40 years, these populations are very close to their steady-state. Since older individuals make significantly different labor supply and savings decisions than young individuals, these evolutions of the population will have profound effects on wages, interest rates, and thus the macroeconomy.


HOW TO MAKE ONE FIGURE WITH 3 PANELS?
:::{figure-md} zaf_pop_fig
<img src="./images/ZAF_pop_distribution.png" alt="ZAF_demog" class="bg-primary mb-1" width="200px">

South Africa
:::

:::{figure-md} ind_pop_fig
<img src="./images/IND_pop_distribution.png" alt="ZAF_demog" class="bg-primary mb-1" width="200px">

India
:::

:::{figure-md} usa_pop_fig
<img src="./images/USA_pop_distribution.png" alt="ZAF_demog" class="bg-primary mb-1" width="200px">

United States
:::

Figure \ref{} plots population growth rates over time for the three countries illustrated above.  The growth rates are determined by the same mortality and fertility trends that drive the evolution of the population in Figure \ref{}. DESCRIBE the trends here

<!-- :::{figure-md} markdown-fig
<img src="../images/pop_growth_rates.png" alt="ZAF_demog" class="bg-primary mb-1" width="200px">

Population Growth Rates in South Africa, India, and the United States
::: -->

## Exercises
1. Make a copy of `demographics.py` and modify to get UN data for specific country.
2. Plot fert rates.  Do again with alternative forecast?
3. Plot mort rates
4. Plot pop distribution over different years
5. Get pop objects and sim model SS with OG-Core defaults then your new pop objects.  Compare SS macro vars using `ogcore.output_tables.macro_table_SS`.

# Macro parameters

## Exercises
1. Use pandas datareader to get GDP series from country XXX from FRED
2. Collapse quarterly data to make annual
3. Compute average growth rate
4. Other??
# Firm Production Functions

Describe industry models, types of sources of data, etc.  SAM files... (UNU Wider)

# Earnings Processes

Earnings processes

## Exercises
1. Use `income.py` from OG-USA to retrieve e matrix.  Plot it.
2. Do approximation method of Marcelo to match a specific gini coefficient



