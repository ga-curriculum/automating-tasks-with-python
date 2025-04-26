<h1>
  <span class="headline">Automating Tasks with Python</span>
  <span class="subhead">Data Analysis and Visualization</span>
</h1>

**Learning objective:** By the end of this lesson, students will be able to automate data analysis tasks and create visualizations using Python libraries.

## Data Manipulation and Analysis with Pandas

[Pandas](https://pandas.pydata.org/) is a powerful Python library for data manipulation and analysis. It provides data structures like DataFrames and Series, allowing you to work with structured data efficiently.

With Pandas, you can load data from various sources, clean and preprocess data, perform data transformations, and apply multiple analytical operations.

Here's an example of using Pandas to perform data manipulation and analysis:

```python
import pandas as pd

# Load data from a CSV file
data = pd.read_csv("sales_data.csv")

# Explore the data
print(data.head())  # Display the first few rows
print(data.info())  # Show information about the DataFrame

# Data cleaning and preprocessing
data = data.dropna()  # Remove rows with missing values
data["Date"] = pd.to_datetime(data["Date"])  # Convert "Date" column to datetime type

# Data transformation
data["Sales"] = data["Sales"].astype(float)  # Convert "Sales" column to float type
data["Month"] = data["Date"].dt.month  # Extract month from "Date" column

# Data analysis
total_sales = data["Sales"].sum()
average_sales = data["Sales"].mean()
sales_by_month = data.groupby("Month")["Sales"].sum()

print(f"Total Sales: ${total_sales:.2f}")
print(f"Average Sales: ${average_sales:.2f}")
print("Sales by Month:")
print(sales_by_month)
```

In this example, we use Pandas to load sales data from a CSV file. We explore the data using `head()` to display the first few rows and `info()` to show information about the DataFrame.

We perform data cleaning by removing rows with missing values using `dropna()` and converting the "Date" column to datetime type using `to_datetime()`.

Next, we perform data transformations by converting the "Sales" column to float type using `astype()` and extracting the month from the "Date" column using `dt.month`.

Finally, we perform data analysis by calculating the total sales, average sales, and sales by month using Pandas functions like `sum()`, `mean()`, and `groupby()`.

Pandas provides various functions and methods for data manipulation and analysis, making it a valuable tool for automating data-related tasks.

## Creating visualizations with Matplotlib and Seaborn

Data visualization is essential to data analysis, as it helps people understand patterns, trends, and relationships within the data. Powerful Python libraries like [Matplotlib](https://matplotlib.org/) and [Seaborn](https://seaborn.pydata.org/) to create a variety of visualizations.

Matplotlib is a fundamental plotting library that provides low-level control over the creation of plots and figures. It allows you to create basic plots like line plots, scatter plots, bar plots, and more.

Here's an example of creating a line plot using Matplotlib:

```python
import matplotlib.pyplot as plt

# Data
x = [1, 2, 3, 4, 5]
y = [2, 4, 6, 8, 10]

# Create a line plot
plt.plot(x, y)

# Add labels and title
plt.xlabel("X-axis")
plt.ylabel("Y-axis")
plt.title("Line Plot")

# Display the plot
plt.show()
```

In this example, we define the data for the x-axis and y-axis. We then use `plt.plot()` to create a line plot.

We add labels for the x-axis and y-axis using `plt.xlabel()` and `plt.ylabel()`, respectively and set a title for the plot using `plt.title()`. Finally, we display the plot using `plt.show()`.

Seaborn is a statistical data visualization library built on top of Matplotlib. It provides a high-level interface for creating attractive and informative statistical graphics. Seaborn offers various plot types like scatter plots, line plots, bar plots, violin plots, heat maps, and more.

Here's an example of creating a scatter plot with a regression line using Seaborn:

``` python
import seaborn as sns

# Load the "tips" dataset
tips = sns.load_dataset("tips")

# Create a scatter plot with a regression line
sns.regplot(x="total_bill", y="tip", data=tips)

# Add labels and title
plt.xlabel("Total Bill")
plt.ylabel("Tip")
plt.title("Tip vs. Total Bill")

# Display the plot
plt.show()
```

Here, we've used Seaborn's built-in "tips" dataset. We create a scatter plot with a regression line using `sns.regplot()`, specifying the x-axis variable as `"total_bill"` and the y-axis variable as `"tip"`.

We add labels and a title using Matplotlib functions. Finally, we display the plot using `plt.show()`.

Seaborn provides a wide range of attractive default styles and color palettes, making it easy to create visually appealing and informative visualizations with minimal code.

## Scheduling and automating data analysis workflows

To fully automate data analysis tasks, you can schedule and run your Python scripts regularly or trigger them with specific events. This allows you to automate the entire workflow, from data retrieval to analysis and reporting, without manual intervention.

Here are a few ways to schedule and automate data analysis workflows:

### cron jobs (Linux/Mac)

[cron](https://en.wikipedia.org/wiki/Cron) is a time-based job scheduler in Unix-like operating systems. You can create a cron job that runs your Python script or Jupyter Notebook at specified intervals (for example, daily, weekly, or monthly).

### Task Scheduler (Windows)

Windows provides a built-in [Task Scheduler](https://learn.microsoft.com/en-us/windows/win32/taskschd/task-scheduler-start-page) that allows you to create and run tasks at specific times or intervals. You can create a task that executes your Python script or Jupyter Notebook.

### Python libraries

Python libraries like [schedule](https://schedule.readthedocs.io/en/stable/index.html) and [APScheduler](https://apscheduler.readthedocs.io/en/3.x/userguide.html) provide a way to schedule and run Python code at specific times or intervals. You can define the schedule and the code to be executed, and the library will handle the scheduling and execution.

### Workflow management tools

Various workflow management tools, such as [Apache Airflow](https://airflow.apache.org/) and [Luigi](https://luigi.readthedocs.io/en/stable/) allow you to define, schedule, and monitor complex data workflows.

These tools provide a higher-level abstraction for defining dependencies between tasks, handling failures, and managing the overall workflow execution.

## The power of automation

By automating data analysis workflows, you can ensure that your data is regularly processed, analyzed, and reported without requiring manual intervention. This saves time, reduces errors, and lets you focus on deriving insights from the data rather than repetitive tasks.

Remember to explore the extensive documentation and examples these libraries provide to unleash their full potential in automating your data analysis tasks.
