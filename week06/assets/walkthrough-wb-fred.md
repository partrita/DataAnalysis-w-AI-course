
# Getting GDP data

We'll show two options

## World Bank GDP per capita via WB API

**API-based, no key needed, works in both R and Python.**

#### 📈 GDP per capita (constant 2015 US\$), code: `NY.GDP.PCAP.KD`

---

#### **Python (using `wbdata` or `pandas-datareader`):**

```python
import wbdata
import pandas as pd
from datetime import datetime

# Set countries and indicator
countries = ['USA', 'HUN', 'DEU']
indicator = {'NY.GDP.PCAP.KD': 'GDP_per_capita'}

# Get data
df = wbdata.get_dataframe(indicator, country=countries, data_date=datetime(2021, 1, 1))
print(df.head())
```

---

#### **R (using `wbstats`):**

```r
install.packages("wbstats")
library(wbstats)

# Set indicator and countries
gdp_data <- wb(indicator = "NY.GDP.PCAP.KD", country = c("US", "HU", "DE"),
               startdate = 2021, enddate = 2021)

head(gdp_data)
```


