# COVID-19 Spread Simulation

## Introduction

This project simulates the spread of COVID-19 in specified countries using a set of provided data. The simulation involves creating a sample population based on the population and age structure in each country. Then, for each individual in the sample, a Markov Chain simulation is run for a specific period (days). The simulation considers 5 states: Healthy (H), Infected without symptoms (I), Infected with symptoms (S), Deceased (D), and Immunity by infection (M). The simulation results are then exported to a CSV file (a3-covid-simulated-timeseries.csv) and summarized for each specified country and date in another CSV file (a3-covid-summary-timeseries.csv). Finally, a chart (a3-covid-simulation.png) is created to visualize the simulation results.

## Input Data

The input dataset is provided in CSV form named `a3-countries.csv`. It contains demographic and age-structure information about 153 countries.

Columns in `a3-countries.csv`:
- `country`: the name of the country.
- `population`: the population of the country.
- `median_age`: the median age in the country.
- `less_5`: the percentage of people aged less than 5 years old.
- `5_to_14`: the percentage of people aged 5 to 14 years old.
- `15_to_24`: the percentage of people aged 15 to 24 years old.
- `25_to_64`: the percentage of people aged 25 to 64 years old.
- `over_65`: the percentage of people aged 65 or more years old.

## Program Structure and Flow

The program follows these steps:

1. Read `a3-countries.csv` and store it in a suitable data structure (e.g., pandas DataFrame).
2. Create a sample population for each specified country based on the population and age group distributions.
3. Create a timeline for all individuals in the population for the specified days of simulation.
   - You can use a long table or wide table approach for this.
4. For each individual in the timeline, run the Markov Chain simulation as specified and fill in the timeline data structure.
5. Save the timeline data to `a3-covid-simulated-timeseries.csv`.
6. Summarize the number of states for each date and country and save it to `a3-covid-summary-timeseries.csv`.
7. Call the `create_plot()` function to plot the final result, resulting in `a3-covid-simulation.png`.

Note: The actual code flow is flexible, as long as the specified outputs are achieved.

## Output

The project generates three outputs:

1. CSV file: `a3-covid-simulated-timeseries.csv`:
   - Columns: `person_id`, `age_group_name`, `country`, `date`, `state`, `staying_days`, `prev_state`.
   - Example:
     ```
     person_id,age_group_name,country,date,state,staying_days,prev_state
     0,less_5,Afghanistan,2020-04-01,H,0,H
     0,less_5,Afghanistan,2020-04-02,H,0,H
     0,less_5,Afghanistan,2020-04-03,H,0,H
     ```

2. CSV file: `a3-covid-summary-timeseries.csv`:
   - Columns: `date`, `country`, `D`, `H`, `I`, `M`, `S`.
   - Example:
     ```
     date,country,D,H,I,M,S
     2021-04-01,Afghanistan,0,37,0,0,0
     2021-04-01,Japan,0,121,0,0,0
     ```

3. Chart: `a3-covid-simulation.png`. The chart will display the simulation results, including the spread of COVID-19 infection over time. Note that the results may vary due to the random nature of the simulation.
