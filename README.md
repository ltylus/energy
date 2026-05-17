```markdown
# U.S. Energy Prices & Aluminum Production Analysis

Analysis of the relationship between industrial energy prices (electricity and natural gas)
and aluminum production across all U.S. states for the years 2001–2018.

## Data Sources
- **Energy prices**: U.S. Energy Information Administration (EIA) API — series ESICD, NGICD
- **Aluminum production**: EIA API — series TEICV (value in million dollars)
- **State population**: U.S. Census Bureau (2018 estimates), stored in PostgreSQL

## Key Findings
- Electricity and natural gas prices are strongly correlated across states — their trends
  move almost in parallel, suggesting shared macroeconomic drivers
- Aluminum production correlates only weakly with state population (r = 0.352) —
  Indiana stands out as a small-population state with the highest production
- The impact of electricity prices on production varies significantly by state;
  some show strong negative correlation, others show no clear relationship

## Tech Stack
- **Python**: pandas, matplotlib, seaborn, numpy, requests
- **Database**: PostgreSQL + SQLAlchemy + psycopg2
- **Data source**: EIA REST API
- **Environment**: jupyter notebook, python-dotenv

## Setup

1. Clone the repository
2. Create a `.env` file with your database credentials:
```
DB_USER=postgres
DB_PASSWORD=your_password
DB_HOST=localhost
DB_PORT=5432
DB_NAME=your_database
```
3. Install dependencies:
```
pip install pandas matplotlib seaborn sqlalchemy psycopg2-binary python-dotenv requests
```
4. Run `energy.ipynb`

## Project Structure
```
├── energy.ipynb         # Main analysis notebook
├── pricesData.json      # Raw data from EIA API
├── state_plots/         # Per-state time series charts (auto-generated)
├── .env                 # Database credentials (not tracked)
└── .gitignore
```

## Notes
- Energy prices originally in $/MMBtu were converted to $/MWh (×3.412) for clarity
- Data limited to 2001–2018 due to incomplete records in 2000 and 2019
- Natural gas price data unavailable for some states (handled gracefully in plots)
```
