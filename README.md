# Educational Inequality Across Pakistan
**A Statistical Analysis of Gender, Province and Urban-Rural Differences**

Probability & Statistics course project - Muhammad Kamran (Roll No. B-29197), University of South Asia.  
Data: Census-2023, Table 12 - *Literacy Rate and Out of School Population Age (5-16) by Sex and Rural/Urban*.

## What this project does
It cleans the census table, calculates descriptive statistics, draws 21 graphs and answers five research questions:
1. What is the gender education gap?
2. Which province has the highest and lowest educational indicators?
3. What is the urban-rural education gap?
4. How does gender inequality vary across provinces?
5. Which groups experience the greatest educational disadvantage?

**Libraries used in the notebook: NumPy, Pandas and Matplotlib only.**

## Folder structure
```
Educational_Inequality_Pakistan_Project/
|-- Educational_Inequality_Analysis.ipynb   <- all code, step by step
|-- README.md
|-- requirements.txt
|-- data/
|   |-- original/table_12_national.xlsx      <- original file, never changed
|   `-- cleaned/
|       |-- cleaned_indicators_by_group.csv  <- 72 rows (region x area x sex), counts + 4 rates
|       `-- cleaned_long_data.csv            <- tidy table: region, indicator, area, sex, value
|-- graphs/                                  <- 21 PNG graphs (01 ... 21)
`-- report/Educational_Inequality_Report.pdf <- final academic report
```

## How to run
1. Install Python 3.9 or newer.
2. Open a terminal in this folder and run: `pip install -r requirements.txt`
3. Start Jupyter: `jupyter notebook`
4. Open `Educational_Inequality_Analysis.ipynb` and choose **Kernel > Restart & Run All**.

Keep the notebook in the project's main folder. The code uses the paths `data/...` and `graphs/...`.  
(`openpyxl` in requirements.txt is only the engine Pandas needs to read `.xlsx`; it is not imported in the notebook.)

## Cleaned data columns
| Column | Meaning |
|---|---|
| region | Pakistan, KP (Khyber Pakhtunkhwa), Punjab, Sindh, Balochistan, ICT (Islamabad Capital Territory) |
| area | All, Rural, Urban |
| sex | Total, Male, Female, Transgender |
| pop_5plus, pop_10plus | People aged 5+ and 10+ |
| literate_10plus, literacy_pct | Literate people aged 10+ and literacy rate (%) |
| ever_attended, never_school_all | People aged 5+ who did / never attended school |
| enrol_primary ... enrol_graduation | Enrolment at five education levels |
| dropout_5_16, never_school_5_16, oosc_5_16 | Out-of-school children (age 5-16): dropouts, never enrolled, total |
| never_attended_pct | never_school_all / pop_5plus x 100 *(calculated)* |
| enrol_total, higher_enrol_pct | All enrolment, and % of it at Intermediate or above *(calculated)* |
| dropout_pct_of_oosc | Dropouts as % of out-of-school children *(calculated)* |

## Cleaning summary
- Report-style Excel table (94 x 13) reshaped into a tidy table (1,008 values; 72 groups x 14 indicators).
- Title, header and column-number rows removed; names shortened; spelling "Intermidiate" fixed; values converted to numbers.
- Missing values: 0 (empty cells were only title/header cells). Duplicates: 0. Zeros: 8, all real transgender counts, kept.
- Consistency checks (literacy % vs counts, sex/area/region totals, out-of-school = dropout + never) all passed.
- Outliers (IQR rule, 20 main groups): none. Nothing was deleted.

## Main findings (from the data)
- **Gender gap:** male literacy 68.0% vs female 52.8% (gap 15.2 pp; rural gap 19.3 pp, urban gap 8.4 pp).
- **Regions:** highest literacy ICT (84.0%), lowest Balochistan (42.0%). Balochistan has 11.6% of out-of-school children but 5.7% of the population aged 5+.
- **Urban-rural:** urban 74.1% vs rural 51.6% (gap 22.5 pp); largest gap in Sindh (34.1 pp); in ICT rural is slightly higher than urban.
- **Gender gap by region:** KP 27.4 pp (widest), Balochistan 17.7, Sindh 14.0, Punjab 11.8, ICT 9.1 (narrowest).
- **Greatest disadvantage:** rural females - Balochistan 26.6%, Sindh 27.5%, KP 33.8% literate. Transgender groups show low literacy too, but their numbers are very small, so they are described only.

## Limitations
- One census year only: no time trends, so no line graphs.
- The population aged 5-16 is not in the table, so an out-of-school *rate* cannot be calculated (shares and a burden ratio are used).
- "Never attended" includes young children who have not started school yet.
- Averages across regions are simple (not population-weighted). Correlation shows a link, not a cause.
- The Census counts everyone, so results are described directly; no sampling tests are used.

## Note on the report
The PDF report was written from the notebook's results; its numbers come from the cleaned CSV file in this project.
