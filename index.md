# How to Call an API in Python: Fetching Weather Data  

Have you ever wondered how apps know the weather in your city? Behind the scenes, they’re calling an **API** (Application Programming Interface) that serves live data.  

In this tutorial, we’ll learn how to:  
1. Understand what an API is.  
2. Use the `requests` library to call a free weather API.  
3. Inspect the JSON response.  
4. Load the data into a pandas DataFrame.  
5. (Optional) Plot the results with matplotlib.  

This guide is beginner-friendly and should take 5–10 minutes to follow.  

---

## What’s an API (in Plain English)?  

Think of an API like a **waiter at a restaurant**.  
- You (the client) make a request from the menu.  
- The waiter (the API) takes your order to the kitchen (the server).  
- The kitchen sends back your food (data) neatly packaged.  

Most modern APIs return data in **JSON format** (JavaScript Object Notation), which looks like nested Python dictionaries.  

---

## Step 1: Install and Import Libraries  

We’ll use two common Python packages:  

```bash
pip install requests pandas matplotlib
