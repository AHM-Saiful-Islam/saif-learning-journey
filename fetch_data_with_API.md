# 📊 Fetching Job Data with an API and Analyzing Open Positions

This example demonstrates how to fetch job data from an API and determine the number of currently open jobs for various **technologies** and **locations**. The script uses the `requests` library to fetch the data, and then processes it with Python.

---

## 🛠️ Code Walkthrough

```python
# Import required libraries
import requests
import pandas as pd
import json

# Function to fetch data from an API
def fetch_api_data(api_url):
    """
    Fetch data from an API link and return it in JSON format.

    Parameters:
    api_url (str): The API endpoint URL.

    Returns:
    dict/list: JSON data returned by the API.
    """
    try:
        response = requests.get(api_url)
        response.raise_for_status()  # Raise error if request failed
        return response.json()       # Convert response to JSON
    except requests.exceptions.RequestException as e:
        print("Error fetching data:", e)
        return None

# Example: Assume jobs_data is the JSON data returned by the API
jobs_data = [
    {"Title": "Python Developer", "Location": "Los Angeles", "Technology": "Python"},
    {"Title": "Java Engineer", "Location": "New York", "Technology": "Java"},
    {"Title": "Data Analyst", "Location": "Los Angeles", "Technology": "SQL"},
    {"Title": "Frontend Developer", "Location": "New York", "Technology": "JavaScript"},
]

# Count number of jobs for specific locations
laCount = 0
nyCount = 0

for job in jobs_data:
    if job["Location"] == "Los Angeles":
        laCount += 1
    if job["Location"] == "New York":
        nyCount += 1

print("Number of jobs in LA:", laCount)
print("Number of jobs in NY:", nyCount)
```

---

## 📍 Example Output

```
Number of jobs in LA: 2
Number of jobs in NY: 2
```

---

## 🔍 Explanation

1. **API Fetching**:

   * The `fetch_api_data()` function makes a GET request to an API endpoint.
   * If successful, it converts the response into JSON.
   * If there’s an error (e.g., invalid URL, network issue), it prints an error message.

2. **Processing Data**:

   * The jobs data is a list of dictionaries, where each dictionary represents a job with keys such as `Title`, `Location`, and `Technology`.
   * We iterate through the list and check the `Location` field.
   * If the location matches `Los Angeles` or `New York`, we increment counters accordingly.

3. **Results**:

   * The script prints the number of available jobs in each specified location.

---

## 🚀 Possible Extensions

* Count jobs by **technology** (Python, Java, SQL, etc.).
* Store results in a **Pandas DataFrame** for more detailed analysis.
* Visualize results using **Matplotlib** or **Seaborn**.
* Extend the API fetching to handle **pagination** if the API provides large datasets.

---

✅ This small project is a practical demonstration of **data fetching, processing, and analysis** using Python, which can be extended for real-world job market insights.
