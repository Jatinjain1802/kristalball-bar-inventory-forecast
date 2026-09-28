# Video walkthrough outline (3-5 minutes)

Use your own words and show the notebook, not just these notes.

**0:00-0:40 | Problem.** Each bar needs enough stock for popular drinks without storing too much slow-moving inventory. The decision here is per bar and brand, in millilitres. Show the first notebook heading and raw data.

**0:40-1:25 | Data check.** There are 6,575 records from six bars and 16 brands, Jan 2023 through Jan 1, 2024. Logs are irregular, about 3.9 days apart at the median. Point to the interval plot. I treat each recorded consumed quantity as usage *since the previous record* and divide by elapsed days. Explain that this is an assumption to check with the hotel, not a proven fact. There are 86 rows with accounting differences over 1 ml.

**1:25-2:20 | Forecast.** Show chronological train/validation/test and the model comparison. I compared lifetime, recent-six and shrunk recent-six historical daily rates, choosing lifetime on validation MAE. No future rows are used for each prediction. Test MAE is about 248 ml per logged interval and WAPE about 83% on 852 intervals, so don't oversell accuracy. Stockouts can hide unmet demand.

**2:20-3:15 | Par and simulation.** Show recommendations table and example: predicted daily ml x 3 days of cover x 1.2 buffer, rounded to 100 ml. The three days assume two days delivery and one day review. Explain that order quantity subtracts the last known stock and would also subtract open orders in production. Show the seven-day simulation with daily demand, arrivals, orders, unmet demand and ending stock. It is made-up demand used to demonstrate the logic, not measured hotel savings.

**3:15-4:10 | Hotel use and next steps.** POS and stock count feed fresh demand and on-hand stock every day; staff verify delivery times and purchase orders; a manager reviews suggestions before ordering. Monitor error, stockout days, stale logs, shrinkage and slow-moving stock. Ask for real stockout and supplier data to improve the forecast and set a tested service buffer. End with one limitation you think matters most.

Check the numbers in the notebook just before recording. Record and submit the video yourself as the form requires.
