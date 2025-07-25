# Crunchbase Funding analysis

## Table of Contents

- [Project Overview](#project-overview)
- [Data Sources](#data-sources)
- [Tools](#tools)
- [Data Engineering](#data-engineering)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Findings](#findings)
- [Additional questions](#additional-questions-to-be-answered)

### Project Overview

This project explores global startup funding trends. The goal is twofold:

- Engineer a memory-efficient data pipeline to process 52,000 investment records, using Python and Pandas
- Conduct exploratory data analysis to explore how funding is distributed across startups, industries, investors and funding rounds

### Data Sources

The primary dataset used for this analysis is the "crunchbase-investments.csv" file, containing funding data from 1987 to 2013. This dataset has been taken directly from [crunchbase-october-2013](https://github.com/datahoarder/crunchbase-october-2013).

### Tools

- Python - Data Engineering
- SQLite - Exploratory Data Analysis

### Data Engineering

- Chunked CSV Loading
  - Efficiently processed a large dataset (50k+ rows) using `pd.read_csv(..., chunksize=5000)` to avoid memory overload.
- Memory usage analysis
  - Measured column-level memory usage using `DataFrame.memory_usage() and eliminated heavy, uninformative columns
- Missing value profiling
  - Computed and aggregated missing value counts across chunks to inform data cleaning decisions
- Data Type Optimisation
  - Converted appropriate columns to the `category` (or `float32`) data type to significantly reduce memory footprint

 ### Exploratory Data Analysis

EDA involved exploring funding data to answer key questions such as:

- What share of total capital was raised by the top 1% and 10% of companies? How does that compare to the bottom 1% and 10%?
- How does total funding vary across different industries?
- Which investors contributed the most funding overall?

### Findings

The analysis results are summarised below:

- Total funding from 1987 to 2013 amounted to $680.63bn
- Of this, the top 10% of highest-funded companies accounted for roughly **half** of total funding!
- The top 1% accounted for 20% of total funding.
- Kliener Perkins Caufield & Byers invested the most of any investor ($11.22bn).
- The Biotech industry attracted the most total funding ($110.27bn).
- Individual startups in the automotive space *on average* attracted more funding ($46.41mn) than startups in other industries
- While Angel rounds were the most popular, by number of investors, Series C attracted the most funding out of any round.

### Additional questions *(to be answered)* 

- What companies received the most funding?
- Who did Kliener Perkins Caufield & Byers invest in?
- Which companies in the Biotech industry received the most funding?
- How has funding dynamics changed over the years?
  - For example, what was the most funded company between 1987 - 2000 vs. 2000 - 2013?
  - Were there any particular dry spells in funding?
  - Has popularity in Angel changed?
