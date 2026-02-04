# Retail Sales Analysis

This README was auto-generated from the Jupyter Notebook `Retail_Sales.ipynb`.

## Overview

This project explores a retail sales dataset using Python and common data science libraries. It includes data loading, cleaning, exploratory data analysis (EDA), and basic visualizations.

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
#fmt: When annot is True, fmt determines the string formatting code for annotating the data. For example, ' d ' for integers and '.2f ' for floating-point numbers with two decimals.

def main():
    df = None

    while True:
        print("\n--- Data Analysis Program ---")
        print("1. Load Data")
        print("2. Explore Data (Head/Tail)")
        print("3. Check for Missing Data")
        print("4. Summary Statistics (Describe)")
        print("5. Specific Column Statistics")
        print("6. Data Visualisation")
        print("7. Exit")

        choice = input("Select (1-7): ")

        if choice == '1':
            file = input("Enter file name (e.g., data.csv): ")
            try:
                df = pd.read_csv('retail_sales.csv')
                print(f"Successfully loaded {file}")
            except Exception as e:
                print(f"Error loading file: {e}")

        elif choice == '2':
            if df is not None:
                print("\n--- Head ---")
                print(df.head())
                print("\n--- Tail ---")
                print(df.tail())
            else:
                print("Load data first!")

        elif choice == '3':
            if df is not None:
                print("Rows with missing values:")
                print(df[df.isnull().any(axis=1)])
            else:
                print("Load data first!")

        elif choice == '4':
            if df is not None:
                print(df.describe())
                print("\n--- Info ---")
                df.info()
            else:
                print("Load data first!")

        elif choice == '5':
            if df is not None:
                col = input("Enter Column Name: ")
                if col in df.columns:
                    print(f"--- Stats for {col} ---")
                    print("Mean:", df[col].mean())
                    print("Total Sum:", df[col].sum())
                    print("Standard Deviation:", df[col].std())
                else:
                    print("Column not found!")
            else:
                print("Load data first!")

        elif choice == '6':
            if df is not None:
                print("1. Bar Chart")
                print("2. Line Chart")
                print("3. Heatmap")

                t = input("Choose chart type (1-3): ")

                if t in ['1', '2']:
                    x = input("Enter column for X axis: ")
                    y = input("Enter column for Y axis: ")

                    if t == '1':
                        plt.bar(df[x], df[y])
                    elif t == '2':
                        plt.plot(df[x], df[y])

                    plt.xlabel(x)
                    plt.ylabel(y)
                    plt.show()

                elif t == '3':
                    corr = df.corr() 
                    sns.heatmap(corr, annot=True)
                    plt.show()


                elif t == '3':
                    numeric_df = df.select_dtypes(include=np.number)
                    corr = numeric_df.corr()
                    plt.figure(figsize=(10, 6))
                    sns.heatmap(corr, annot=True, fmt=".2f", cmap="coolwarm")
                    plt.title("Correlation Heatmap")
                    plt.show()
                else:
                    print("Invalid chart option!")
            else:
                print("Load data first!")

        elif choice == '7':
            print("Exiting program. Goodbye!")
            break

        else:
            print("Invalid choice, please try again.")


if __name__ == "__main__":
    main()
```

* In this Bar chart shows that in x columns shows Total Sales and y cloumn shows product Category it shows the data that total sales are majority equal of column name accessories and product category are equal majority level of T
* In this Line chart shows that in x columns shows category and y cloumn shows price it shows the data that price and category are equal majority level
