(Chap_OGcalibration)=

# Calibrating the `OG-Core` model

As noted in the introduction, the `OG-Core` model must be parametrized to represent a specific country. We refer to the process of finding parameter values that represent a specific economy as "calibration".  Because data sources for country-specific data differ, there's not a single way to calibrate all economies. We have therefor have created country-specific calibration packages.   Some examples of these include the [United States](https://github.com/PSLmodels/OG-USA), the [United Kingdom](https://github.com/PSLmodels/OG-UK), [South Africa](https://github.com/EAPD-DRB/OG-ZAF), [India](https://github.com/Revenue-Academy/OG-IND), and [Malaysia](https://github.com/Revenue-Academy/OG-MYS).

In this chapter, we describe the process of creating a country-specific calibration and provide exercises related to certain components of that calibration.  We will use as an example the calibration of `OG-Core` to South Africa, in the [`OG-ZAF`](https://github.com/EAPD-DRB/OG-ZAF) package.

(SecDemographics)=
# Demographics

A key feature of OG models is the ability to model the impacts of economic shocks or policy changes across generations. Because they capture generations of finitely-lived agents, OG models can be made to reflect realistic demographics.  Demographic trends are of massive importance to economic trends [TODO: add CITATIONS here]. Furthermore, there is a tremendous amount of variation in demographic trends across countries.  Consider Figure {ref}{TODO: create and reference 3 panel figure}, which shows the population distributions, and their evolution over time, for three countries: South Africa, India, and the United States. In each figure, we plot the 2023 population distribution (according to data from the [UN World Population Prospects](https://population.un.org/wpp/)) and then the evolution of the population as we age it forward two, 40, and 80 years and then to it's steady state distribution using the `demographics.py` module from the relevant country calibration (i.e., `OG-ZAF`, `OG-IND`, `OG-USA`). Comparing the 2023 distributions first, we see that South African distribution has humps, which reflect the initial wave of the HIV epidemic and then it's echo on the next generation.  We see also that India has more young adults than the two other countries, but displays a relatively flat gradient as the number of individuals decline quickly with age, reflecting relatively high mortality rates in that country.  The United States has a more right skewed distribution than South Africa and India, with more individuals of advanced age, reflecting relatively low mortality rates for adults. As each population is simulated forward in time, we see the age distribution move to the right, with older individuals representing a larger share of the population in each country.  After about 40 years, these populations are very close to their steady-state. Since older individuals make significantly different labor supply and savings decisions than young individuals, these evolutions of the population will have profound effects on wages, interest rates, and economic growth.


TODO: HOW TO MAKE ONE FIGURE WITH 3 PANELS?
:::{figure-md} zaf_pop_fig
<img src="./images/ZAF_pop_distribution.png" alt="ZAF_demog" class="bg-primary mb-1" width="80%">

South Africa
:::

:::{figure-md} ind_pop_fig
<img src="./images/IND_pop_distribution.png" alt="ZAF_demog" class="bg-primary mb-1" width="80%">

India
:::

:::{figure-md} usa_pop_fig
<img src="./images/USA_pop_distribution.png" alt="ZAF_demog" class="bg-primary mb-1" width="80%">

United States
:::

<!-- Below I test using sphinx panels, but it doesn't seem to work -->
````{panels}
:container: container-fluid
:column: col-lg-6 col-md-6 col-sm-6 col-xs-12
:card: shadow-none border-0

```{figure} "./images/ZAF_pop_distribution.png"
:width: 100%
:name: example1

Sub-caption 1
```

---

```{figure} "./images/IND_pop_distribution.png"
:width: 100%
:name: example2

Sub-caption 2
```

````

Figure {ref}{TODO: add reference to 3 panel figure} plots population growth rates over time for the three countries illustrated above.  The growth rates are determined by the same mortality, fertility, and immigration trends that drive the evolution of the population in Figure {ref}{TODO: create and reference 3 panel figure}. In terms of population growth, we see that in all countries the population growth rate is declining in each of the three counties over the next 60 years.  This is consistent with what we saw in the evolution of the population distribution in the three countries above: each economy is aging and with relatively more older individuals, total fertility will be declining.  Looking at the level of population growth in the long run in {numref}`Figure %s <pop_growth_rates_fig>`, we see that India and the United States will have negative population growth, which will put downward pressure on their long run economic growth rates.  In contract, South Africa will have positive population growth, owing to it's relatively high fertility rates, which will contribute positively to that economy in the long run.

:::{figure-md} pop_growth_rates_fig
<img src="./images/pop_growth_rates.png" alt="ZAF_demog" class="bg-primary mb-1" width="80%">

Population Growth Rates in South Africa, India, and the United States
:::

The population distribution and growth rates in the plots above were created using the `demographics.py` module from the relevant country calibration repository. Each of these country calibrations utilizes population data from the [UN World Population Prospects](https://population.un.org/wpp/) database, which provides consistent data on the population distribution and age-specific mortality, fertility, and immigration rates by country for many countries.  Note that although immigration rates are provided, the `demographics.py` module imputes them as the residual between the population counts by age and what would be expected given the measured fertility and mortality rates.  This is done for two reasons.  First, it ensures that the evolution of the distribution of population by age is consistent with the three forces affecting it: fertility, mortality, and immigration. Second, it is difficult to accurately measure immigration since not all immigrants are documented (with substantial variation in this across country).  Using the residual method to identify immigration may therefore be more accurate than official statistics.

`demographics.py` has several functions with the module. For the South Africa version of `demographics,py` you can find a summary of those functions in the API documentation [here](https://eapd-drb.github.io/OG-ZAF/content/api/public_api.html).  Below we offer several exercise that have you interact with this module help you learn better understand its inputs and outputs.

## Exercises

```{exercise-start}
:label: ExerCalib-demo_country
:class: green
```
First, let's create a utility to get population data from the UN Population Prospects for a country of interest to you.  Start by making a copy of [`demographics.py`](https://github.com/EAPD-DRB/OG-ZAF/blob/main/ogzaf/demographics.py) from the `OG-ZAF` repository.  Next, modify the `demographics.py` you just copied to gather population data for another country (i.e., not South Africa).  Each country in the UN database has a two or three digit code.  You can find a list of these [here](https://unstats.un.org/unsd/methodology/m49/)
```{exercise-end}
```

```{exercise-start}
:label: ExerCalib-demo_fert
:class: green
```
Using your modified `demographics.py`, plot the fertility rates in this country.  Note that you can do this directly from the `demographics.get_fert()` function.
```{exercise-end}
```

```{exercise-start}
:label: ExerCalib-demo_mort
:class: green
```
Let's do the same for mortality rates.  In this case, you will want interact with the `demographics.get_mort` function.
```{exercise-end}
```

```{exercise-start}
:label: ExerCalib-demo_pop_dist
:class: green
```
The `demographics.py` module uses current fertility and mortality rates (and the implied immigration rates) to project the population forward.  This ensures a population distribution in each year of the model that is consistent with the fertility, mortality, and immigration rates.  Use the `demographics.get_pop_objs` function to return a dictionary with the population object that are inputs to calibrating `OG-Core` (Use `E=20`, `S=80`, `T=320`, `curr_year=2023`).  From this dictionary, extract the population distribution object (the key for this is `omega` and it is an array with shape `TxS`, where `T` are the number of time periods and `S` is the number of age groups in the model).  Create a line plot of the population distribution in the first year, the 20th year, the 100th year, and the last year in the `omega` object.  Describe what you see happening to the distribution of people across age as you more forward in time?
```{exercise-end}
```

```{exercise-start}
:label: ExerCalib-demo_pop_growth
:class: green
```
Also in the dictionary returned from `demographics.get_pop_objs`, is the population growth rate. This is a NumPy array object with key `g_n`.  Plot `g_n`.  How does the population growth rate change over time?  Given what you've seen in the plots you've created, what can you say about the driver(s) of population growth (i.e., how are fertility and mortality rates contributing?  What about immigration (something we haven't yet plotted, but about which you might be able to infer something given fertility and mortality rates and the change in the age distribution over time...))
```{exercise-end}
```

```{exercise-start}
:label: ExerCalib-demo_sims
:class: green
```
Now that you've visualized the different demographic trends in the country you've chosen, let's see how these affect the equilibrium in the OG model.  This will combine what you learned in {ref}`Chap_OGsimulation` with what you've learned here about population demographics objects for the model. You'll proceed with the following steps:

1. Instantiate a `Specifications` class object from `OG-Core` with:
   ```python
     p = Specifications(
           baseline=True,
           baseline_dir=base_dir,
           output_base=base_dir,
       )
   ```
where you set the directory you'd like this output saved with a string `base_dir`.
1. Use the `ogcore.execute.runner()` function to solve for the steady state of the model.
2. Now, create a new Specifcations object with:
   ```python
     p2 = Specifications(
           baseline=True,
           baseline_dir=base_dir,
           output_base=base_dir,
       )
   ```
where you set the directory you'd like the output from this second model run saved with a string `reform_dir`.
1. Use the demographics module you edited above to return the a dictoinary of population objects from `demographics.get_pop_objs`.  Use these to update the `p2` object:
```python
p2.update_specifications(pop_obs_dict)
```
1. Use `ogcore.execute.runner()` to solve the model again, this time with the parameters in `p2`.
2. Finaly, comparet the differences in the steady-state macroeconomics variablkes using `ogcore.output_tables.macro_table_SS`.  What do you see?  How did demographics affect aggregate output?  Wages?  Interest rates?  Do you have intuition about why this happened?
```{exercise-end}
```

# Macro parameters

There are a number of parameters of the `OG-Core` model that are calibrated using macroeconomic data from national accounts or national government reports.  In general, we've tended to read in data that inform these values in a single module, such as the [`macro_params.py`](https://github.com/EAPD-DRB/OG-ZAF/blob/main/ogzaf/macro_params.py) module in `OG-ZAF`.  We break the discussion of the parameters calibrated from macro data into separate groupings based in what they represent in `OG-Core`.

## Economic growth and production

The `OG-Core` model needs to be stationary in order to employ traditional solution methods.  This means that in the model solution, there cannot be underlying growth in the model objects.  However, the model is able to allow for such underlying growth, which may be driven by population growth rates (as discussed above) or underlying changes in productivity.  In order to solve the model, then, trend growth from these sources are removed.[^stationary_note].  However, since different variables grow at different rates, we need to know both the underlying growth rates of the population and of technological growth.  The population growth rate was determined from the demographic data and described in Section {ref}`SecDemographics`. We use macroeconomic data, namely the growth rate in gross domestic product per capita to pin down the rate of growth in (labor-augmenting) technological change, `g_y_annual` in `OG-Core`.  Let $\hat{y}_t$ represent the growth rate in GDP per capital from year $t-1$ to year $t$.  We find the value of `g_y_annual` as equal to the long-run average of $\hat{y}_t$:

```{math}
:label: g_y_calib
 g_y = \sum_{t = \text{First year of data}}^{\text{Most recent year of data}} \hat{y}_t
```

Note that you will want to use some judgement in what is the appropriate time period for the "first year of data". For example, if the economy in question is now a market economy, but your data extend back to a time when it was not a market economy, you will probably want to exclude those data from the non-market economy period.  In addition, you might alter the calibration of `g_y` to be more forward looking and, rather than base future growth on recent history, you may use long run economic forecasts for GDP per capita.  But in either case the important thing is to be sure you are correctly mapping the data to the theoretical concept of `g_y`, which is measuring the constant rate of growth in output per person in the long run.


### Firm production
Changes in productivity in the short run are accounted for by changes in total factor productivity (TFP).  This parameter is denoted as `Z` in `OG-Core` and is represented by a 2-dimensional array that is `TxM` in size, where `T` is the number of time periods over the transition path and `M` is the number of industries.  Thus, you may have total factor productivity, that changes over time and varies across production industry. Values of `Z` are found through [growth accounting](https://www.imf.org/external/pubs/ft/wp/1999/wp9977.pdf) techniques. However, you may not want to (or easily be able to) do the accounting yourself because it is often difficult to find the necessary data to do such accounting, which requires industry specific capital stocks.  You might find research on sectoral TFP from central banks or other sources.  For the calibration of sectoral TFP from South Africa, we used data published by the central bank. You can find a nice discussion of the process used in that case in [this GitHub Issue](https://github.com/EAPD-DRB/OG-ZAF/issues/29).

In addition to the level of TFP, the production functions of firms are determined by the shares of income attributable to capital, labor, and infrastructure (public capital) and the elasticity of substitution between these inputs. These are the parameters `gamma`, which is the share of income attributable to capital, and `gamma_g`, which is the share of income attributable to infrastructure. The remainder, $1-\gamma-\gamma_g$ is the share attributable to labor.  Factor shares can be determined through national accounts data.  The share out output paid to labor is found from the ration of labor income (wages and salaries) to GDP, while capital's share of income can be found through the payments to capital (interest, dividends, profits) divided by GDP.  The share of output attributed to infrastructure will then be found as a residual (= 1 - labor share - capital share), as the OG-Core model requires a constant returns to scale production function.  Determining the elasticity of substitution between inputs is more involved and would require detailed panel with prices and quantities.  We therefore recommend using a default calibration with a unit elasticity ($\epsilon_m = 1$) for each industry -- or finding other research from your economy of interest where this parameter has been estimated.

Finally, we need to map the $M$ output goods to the $I$ consumption goods.  The `OG-Core` model assumes what is called a "fixed coefficient" matrix for the mapping between producer outputs and consumption goods.  That is, a fixed share of each output good is required to produce each consumption good.  This is represented by an `MxI` matrix denoted as $\Pi$, which has elements $\pi_{m,i}$ that is the share out consumption good $i$ that is from output good $m$.  Note that the columns of this matrix must sum to one (i.e., we need to fully account for the output goods that go into each input good).  The $\Pi$ matrix can be calibrated directly from a input-output tables that are typically produced through national accounts.  In the `OG-ZAF` project, there is a nice example of calibrating the $\Pi$ matrix using input-output data in detailed producer outputs and consumer goods categories available in the social accounting matrix files available from [UNU Wider](https://www.wider.unu.edu/social-accounting-matrices).


## International finance

The `OG-Core` model parameterizes the degree of economic openness with two parameters relating to international capital flows.  The first is the fraction of new government debt issues which are purchased by foreign investors, `zeta_D`.  This parameter can be calibrated through financial accounts data that shows the location of buyers of government debt.  The second parameter reflects the amount of excess capital demand that is satisfied by foreign investors.  Here, excess demand is defined as the difference between the capital demand of firms at the interest rate outside the domestic economy (i.e., the world interest rate) and the capital of demand from firms if they face teh domestic interest rate.  The  parameter `zeta_D` takes a value between zero and one and is the share of this excess demand for capital that foreign investors make up.  A value of zero would represent a closed economy, which no foreign investment in domestic capital. While a value of one represented a small open economy, where the domestic interest rate is equated to the world interest rate since capital flows in (or out) freely.  One cannot look just at financial accounts data to calibrate `zeta_D` , because the excess demand concept is model based and there's not a direct analog in the data.  Rather, we have utilized an approach of moving the value of `zeta_D` up or down based on the size of the economy relative to the world, with countries that have a smaller share of world financial market activity having a `zeta_D` closer to one. Of course, one would also like to consider any capital controls that may be in place in the economy of interest.  If there are capital controls, then the value of `zeta_D` should be set to a smaller value.

## Fiscal policy

Governments in the `OG-Core` model may raise revenue through the taxation of personal and corporate income,  payroll taxes, consumption taxes, taxes on bequests, and wealth taxes. These revenues, along with government borrowing, as you used to finance expenditures on transfers, government investment in infrastructure, spending on a public good, and interest payments on debt.  Here, we discuss the calibration of each of these parameters.

### Tax rates


### Pension systems


### Spending parameters

Government spending, at least that is modeled outside of the net tax functions or pension functions, is modeled as an exogenous fraction of GDP, with an exception in some parameterizations that we discuss below.  By calibrating spending as a fraction of GDP, on avoids any need to convert between model and data units and it also more accurately mimics the empirical fact that the size of governments tends to grow with the size of the economy.  There are three spending related parameters that are shares of GDP.  These are `alpha_G`, the ratio of government spending on public goods to GDP, `alpha_T`, the ratio of government spending on transfers to GPD, and `alpha_I`, the ratio of government spending on infrastructure to GDP.

To calibrate these ratios, one can generally use national accounts data in combination with government budget reports.  The challenging piece to ensure that the definition of spending in the data and the model are aligned.  For example, if you are explicitly modeling the pension system and using the net tax functions to capture some non-pension spending programs (such as income-tested welfare benefits), then you will want to exclude those spending programs when computing total transfers by year as the numerator in the `alpha_T` ratio.  Another strategy, to make sure you are fully capturing government outlays, is to compute one of the spending ratios as a residual.  For example, if you have data on government spending on public goods and transfers (again, after taking out what is accounted for in the modeling of pensions and taxes), you can compute the infrastructure spending ratio as a residual (= 1 - `alpha_G` - `alpha_T`).

The default way in which total transfers, $TR_t = alpha_{T,t} * GDP_{t}$ gets allocated to households is as a lump-sum, uniformly distributed transfer.  But you can adjust this distribution to match the true distribution of transfers across the population by adjusting the `eta` parameter. This is a three dimensional array that is `TxSxJ`. It sums to one in each model period and represents the fraction of transfers in that year distributed to each age (`S`) and lifetime income group (`J`). You can thus approximate the age and mean-tested transfers with this matrix, as well as policy changes that affect the distribution of transfers across the population over time.

As a final note, one will need to set the value for the initial infrastructure to GDP ratio, `initial_Kg_ratio`.  To find this, one needs an estimate of the stock of public infrastructure.  If no report exists reporting this an approximation would be to say that $K_g = \frac{I_g,t} / \delta_{g}$, where $I_{g,t}$ is the among of infrastructure spending (at present or averaged over recent years) and $\delta_g$ is the ratio of depreciation on this infrastructure (e.g., 2\% per annum).

### Government financing parameters

Governments can run an unbalanced budget, but in order for an equilibrium to exist, deficits must be restricted such that they do not grow faster than GDP (if they did, interest payments on the debt would grow beyond available resources).  Governments therefore can borrow to finance outlays.  As there is no idiosyncratic risk on private capital in the model, we build in a risk premium by allowing the government to borrow at a rate lower than the private market.  If the rate the private market pays is given by `r`, then the government pays an interest rate of `r_gov = r_gov_scale * r - r_gov_shift`.  The `r_gov_scale` and `r_gov_shift` parameters are two that one would calibrate to the economy in question.  We advise doing this by looking at the historical haircut on private interest rates that the government has paid.  For example, if the government has paid an average interest rate of 1.5 percentage points below the private market, then `r_gov_scale` would be 1.0 and `r_gov_shift` would be 0.015.  One can do this in a systematic manner by finding time series data on government debt and corporate debt of the same maturity and estimating the two parameters directly.  For example, with these data you can estimate, via OLS, the following equation:

```{math}
r_{gov,t} = \alpha + \beta r_{corp,t} + \epsilon_t
```

where $r_{gov,t}$ is the interest rate on government debt and $r_t$ is the interest rate on corporate debt.  The parameter $\beta$ would then be the value of `r_gov_scale` and $\alpha$ would be the negative of the value of `r_gov_shift`.

Finally, we need to calibrate the initial government debt to GDP ratio, `initial_debt_ratio`.  This is done by finding the ratio of government debt to GDP in the most recent year of data and setting `initial_debt_ratio` equal to that value.


## Exercises
```{exercise-start}
:label: ExerCalib-macro_datareader
:class: green
```
The [Federal Reserve Economic Database](https://fred.stlouisfed.org) (FRED) contains macroeconomic data for a number of countries and a user friendly interface.  In addition, tools, such as [`pandas-datareader`](https://pandas-datareader.readthedocs.io) make it extremely easy to access the FRED API.  In this exercise, use `pandas-datareader` to download the quarterly, real GDP time series for South Africa from FRED.  Plot it.
```{exercise-end}
```

```{exercise-start}
:label: ExerCalib-macro_freq
:class: green
```
Now, use the [`datetime`](https://docs.python.org/3/library/datetime.html#datetime-objects) object functions to collapse the quarterly GDP data to annual data.  Plot it.
```{exercise-end}
```

```{exercise-start}
:label: ExerCalib-macro_gy
:class: green
```
With your annual data, compute the annual growth rate for each year.  Plot the time series of growth rates.
```{exercise-end}
```

```{exercise-start}
:label: ExerCalib-macro_reg
:class: green
```
Now let's estimate the autocorrelation in GDP growth, assuming is a first order auto-regressive process (AR1).  We'll do this with the `statsmodles.OLS` function.

First, create a new column in your data frame that is the lagged value of GDP growth.  Then, use the [`statsmodels.regression.linear_model.OLS`](https://www.statsmodels.org/dev/generated/statsmodels.regression.linear_model.OLS.html) function to estimate the following equation:

   ```{math}
   y_{t} = \alpha  + \rho y_{t-1} + \varepsilon_{t}
   ```

What did you estimate as $\alpha$?  What does this represent?  How persistent is the growth process in South Africa?

```{exercise-end}
```

```{exercise-start}
:label: ExerCalib-macro_???
:class: green
```
Other??
```{exercise-end}
```

# Earnings Processes

An important component of the `OG-Core` model are the household earnings processes.  These help to match real difference across age and households in earnings ability and are a key set of parameters to model income inequality. Household earnings are endogenous and depend on the households' decisions to work and save given the state of the economy and household preferences and ability.  What is exogenous to the model are how productive households are with each unit of labor they supply, i.e., their earnings ability.  `OG-Core` assumes that there are `J` groups of households with different earnings abilities.  Within each group, the earnings ability process is deterministic and known to the household, although labor productivity of these workers vary over their working life.  Fore example, consider {numref}`Figure %s <USA_earn>`, which shows the log of effective labor units for each of seven lifetime income groups, estimated in the United States.  Each group is defined by their "potential" earnings over their lifetime (i.e., if they worked full time, what would they earn over a 40 year career) and grouped by their percentile rank in the distribution of lifetime incomes. We can see that the top 1\% of lifetime earnings have higher productivity in each year of working life, but because productivity varies with age, this gap is not constant.  Rather, it's largest during the peak earnings year of middle age and then is quite small at older ages.

:::{figure-md} USA_earn
<img src="./images/USA_ability_profiles.png" alt="USA_earn" class="bg-primary mb-1" width="80%">

Log Effective Labor Units by Lifetime Income Group, Estimated in the United States
:::

In `OG-Core`, these earnings processes are described by `SxJ` matrix, with each cell representing the effective labor units for a given age and lifetime income group.  Note that this matrix is normalized such that the average value of earnings ability is one.  It is assumed that these processes remain constant over time, so despite growth in the level of productivity through the exogenous technological growth,

To estimate the earnings processes in {numref}`Figure %s <USA_earn>`, we used administrative data from tax returns the covered a panel of US taxpayers over four decades.  A detailed description of this process is given in the [`OG-USA` documentation](https://pslmodels.github.io/OG-USA/content/calibration/earnings.html). Suffice it to say, this estimation process is quite involved and requires a large panel dataset in individual or household earnings, ideally without censoring the top end. In many contexts, these data may not be available.  We therefore will describe here an approximation technique that is less data intensive, and leave the more involved estimation process for the interested reader to explore in the `OG-USA` documentation.

To approximate the earnings processes in a country of interest, we recommend starting with the `OG-USA` calibration and then applying a transformation to these earnings processes to match the distribution of income in the target country.[^e_mat_zaf_note].  Specifically, one will find mean earnings by age for the target country... TODO: getcode to link to in OG-ZAF from Marcelo *or* just reference the methods in OG-IND/MYS.

## Exercises
```{exercise-start}
:label: ExerCalib-earn_plot
:class: green
```
Use [`income.py` from `OG-USA`](https://github.com/PSLmodels/OG-USA/blob/master/ogusa/income.py) to retrieve the earnings process matrix.  Read through the docstrings of each function to see which to use.  With the `e` matrix that is returned, create a line plot of the earnings at each age for the `J` different types.
```{exercise-end}
```

```{exercise-start}
:label: ExerCalib-earn_approx
:class: green
```
Now we're going to adjust the above earnings process to match the Gini coefficient in a country that isn't the U.S. (note that the Gini coefficient for income in the U.S. was 41.5 in 2019). The transformation we'll make is:

   ```{math}
   e_{C} = e_{USA} e^{a * e_{USA}}
   ```

where $C$ represents the country of interest. We will find $a$ by matching the Gini coefficient in the country of interest.  To do this, we'll use the `scipy.optimize` module.  First, create a function that takes $a$ as an argument and returns the Gini coefficient in the country of interest (hint: the [`ogusa.utils.Inequality`](https://github.com/PSLmodels/OG-Core/blob/9d7c814bafd210a581ffebf7df6f357aa5b2a048/ogcore/utils.py#L463) class object will be helpful here).  Then, use the `scipy.optimize.minimize_scalar` function to find the value of $a$ that minimizes the difference between the Gini coefficient in the country of interest and the Gini coefficient in the U.S.  Finally, use the value of $a$ you found to transform the `e` matrix from the U.S. to the country of interest.  Plot the earnings processes in the U.S. and the country of interest.  How do they differ?
```{exercise-end}
```



(SecOGCalibrationFootnotes)=
## Footnotes

[^stationary_note]: For specifics on how this is done, please see the `OG-Core` [Stationarization Chapter](https://pslmodels.github.io/OG-Core/content/theory/stationarization.html).
[^e_mat_zaf_note]:  For a discussion with the original application of this method from Marcelo LaFluer see the `OG-ZAF` repo's [Pull Request #28](https://github.com/EAPD-DRB/OG-ZAF/pull/28).