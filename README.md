# EXPERIMENT 3: LOG TRANSFORMATION OF INTERNATIONAL AIRLINE PASSENGER DATA
# NAME : MONISHA 
# REG NO :2305001019

##  Aim
To apply logarithmic transformation to the International Airline Passenger time series and compare the original and transformed data.

##  Software Required
- Python 3
- Google Colab or Jupyter Notebook
- Pandas
- NumPy
- Matplotlib

##  Procedure
1. Import the required libraries.
2. Load the AirPassengers dataset.
3. Plot the original time series.
4. Apply logarithmic transformation using `np.log()`.
5. Plot the transformed series.
6. Compare the original and transformed data.

##  Program
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# Load AirPassengers dataset
url = "https://raw.githubusercontent.com/jbrownlee/Datasets/master/airline-passengers.csv"
df = pd.read_csv(url)

# Rename columns and convert Month to datetime
df.columns = ["Month", "Passengers"]
df["Month"] = pd.to_datetime(df["Month"])
df.set_index("Month", inplace=True)

print("Original Data:")
print(df.head())

# Plot original time series
plt.figure(figsize=(12, 5))
plt.plot(df.index, df["Passengers"], marker="o")
plt.title("International Airline Passengers")
plt.xlabel("Year")
plt.ylabel("Passengers (Thousands)")
plt.grid(True)
plt.show()

# Apply log transformation
df["Log_Passengers"] = np.log(df["Passengers"])

print("\nLog Transformed Data:")
print(df.head())

# Plot log-transformed series
plt.figure(figsize=(12, 5))
plt.plot(df.index, df["Log_Passengers"], marker="o")
plt.title("Log-Transformed Airline Passenger Data")
plt.xlabel("Year")
plt.ylabel("Log(Passengers)")
plt.grid(True)
plt.show()

# Compare original and transformed series
fig, axes = plt.subplots(2, 1, figsize=(12, 8))

axes[0].plot(df.index, df["Passengers"])
axes[0].set_title("Original Airline Passenger Series")
axes[0].set_ylabel("Passengers")
axes[0].grid(True)

axes[1].plot(df.index, df["Log_Passengers"])
axes[1].set_title("Log-Transformed Airline Passenger Series")
axes[1].set_ylabel("Log(Passengers)")
axes[1].set_xlabel("Year")
axes[1].grid(True)

plt.tight_layout()
plt.show()

# Compare variance
print("Original Variance:", df["Passengers"].var())
print("Log-Transformed Variance:", df["Log_Passengers"].var())
```

##  Expected Output
- Original airline passenger time-series graph.

<img width="841" height="395" alt="image" src="https://github.com/user-attachments/assets/47ef5fe9-c326-4210-a373-5ebaff8a419a" />

- Log-transformed airline passenger graph.

 <img width="812" height="362" alt="image" src="https://github.com/user-attachments/assets/d805032b-f6bf-461c-8e1f-27ed10d9c9db" />

- Comparison plots of original and transformed data.

  <img width="822" height="542" alt="image" src="https://github.com/user-attachments/assets/d9a71555-ce78-48ed-8763-ee798e006fcf" />

- Original and log-transformed variance values.

 <img width="822" height="611" alt="image" src="https://github.com/user-attachments/assets/c82ca888-7a36-4575-a07d-54584e0f1420" />


## Observation
Before log transformation, the passenger series shows an increasing trend and larger fluctuations as passenger numbers increase.

After log transformation, larger values are compressed more strongly than smaller values. This can reduce changing variability and make the series easier to model.

##  Result
Thus, logarithmic transformation was applied successfully to the International Airline Passenger time series, and the original and transformed data were visualized and compared.

