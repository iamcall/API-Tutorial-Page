# How to Call an API in Python: Fetching Weather Data  

Have you ever wondered how `APIs` work? This will be a short demo on how to use them by fetching weather data. 

In this tutorial, we’ll learn how to:  
1. Understand what an API is.  
2. Use the `requests` library to call a free weather API.  
3. Inspect the JSON response.  
4. Load the data into a pandas DataFrame.  
5. (Optional) Plot the results with matplotlib.  


---

## Step 1: What’s an API (in Plain English)?  

Think of an API like a **vending machine**  (the service you want to talk to).
- You want a snack → you want some information  
- You press B2 → you send a request
- The machine gives you a snack → the service sends back a response

Most modern APIs return data in **JSON format** (JavaScript Object Notation), which looks like nested Python dictionaries.  

---

## Step 2: Call for a free weather API

We’ll fetch the **current temperature** for London using the [Open-Meteo API](https://open-meteo.com/).  

```python
import requests

# Define the API endpoint
url = "https://api.open-meteo.com/v1/forecast"

# Define query parameters
params = {
    "latitude": 51.5072,   # London
    "longitude": -0.1276,
    "current_weather": True
}

# Send GET request
response = requests.get(url, params=params)

# Convert the response to JSON
data = response.json()

# Print it nicely
print(data)
```


---
## Step 3: Inspect the JSON response
The response we got back is in **JSON format**. This is basically a big nested dictionary.  
We can look inside and grab just the `current_weather` data:  

```python
# Look at the keys in the JSON
print(data.keys())

# Extract just the "current_weather" section
current = data["current_weather"]
print(current)

# Access specific values, like temperature
temperature = current["temperature"]
print(f"Current temperature in London: {temperature}°C")

```

---

## Step 4: Load the data into a pandas DataFrame

Working with raw JSON is fine, but pandas makes it way easier to explore data in a **table-like format**.  

We’ll take the `current_weather` dictionary and turn it into a one-row DataFrame:  

```python
import pandas as pd

# Convert the "current_weather" dictionary into a DataFrame
df = pd.DataFrame([current])

print(df)
```


---
## Step 5: (optional) Plot


Now that the data is in a DataFrame, we can easily make a quick plot.  

In this case, we only fetched one row of weather data, so the plot will look a bit boring — but if you query **hourly forecasts** instead, you can visualize trends (like temperature over time).  

Here’s a simple example using the single data point:  

```python
import matplotlib.pyplot as plt

# Plot temperature as a bar chart
df.plot(kind="bar", y="temperature", legend=False)
plt.title("Current Temperature in London")
plt.ylabel("°C")
plt.xticks([])  # hide x-axis labels since it's just one point
plt.show()

```


---


## Call to Action

Now that you have the data loaded in, it's your turn to try! Find APIs you can play around with and analyze your data.

_Happy Coding !_