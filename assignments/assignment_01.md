# Reproduce an FT graph

Look at [this graph](/week01/assets/ft-liberation-day-usd-yield-2025-04-11.jpg) from Financial Times. Your task is to recreate this figure using real-world data. 

### Option A (easy)
Use AI as your assistant to find real-world data that matches or closely resembles the one used in the FT graph, and recreate the same chart using that data.

**what to submit**
* Graph: A PDF version of your recreated graph, name it: "lastname_firstname_dawai_week01_ftfigure.pdf"
* Data: A CSV file with the data used to create the graph, with the name ("lastname_firstname_dawai_week01_ftdata.pdf")

### Option B (advanced)

Use AI as your assistant to build an interactive app (dashboard) that mimics the FT graph. Try to see if you can update the app dynamically (e.g., with user inputs, date range selectors, etc.).

**what to submit**
* link to app
  * you can use tools like steamlit (Python), shinyapps (R), etc


**Hint: Where to find the data**

You can get data for both DXY (US Dollar Index) and the 10-year US Treasury Yield from public sources.

* If using code:
  * R: 
    * quantmod → getSymbols("DX-Y.NYB", src = "yahoo")
    * fredr → fredr("DGS10", observation_start = as.Date("2023-01-01"))
  * Python:
    * yfinance → yf.download("DX-Y.NYB", start="2023-01-01")
    * fredapi → fred.get_series("DGS10")
  * If downloading manually:
    * DXY: Yahoo Finance → https://www.investing.com/indices/usdollar-historical-data
    * 10-Year Yield: FRED → https://fred.stlouisfed.org/series/DGS10
