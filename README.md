# Market-Sales-Data
The Supermarket Sales Dataset provides a comprehensive overview of supermarket transactions, tracking details 
"import library"
import numpy as np
import pandas as pd 
import matplotlib.pyplot as plt
import seaborn as sns 

"import Data"
data=pd.read_csv(r"C:\Users\Elbostan\Desktop\supermarket_sales new.csv")

"data preprocessing"

data.head()

data.info()

data.describe()

data.isna().sum()

" Data Visualization"

numeric_data = data.select_dtypes(include=['number'])
correlation_matrix = numeric_data.corr()
plt.figure(figsize=(8, 6))
sns.heatmap(correlation_matrix, annot=True, cmap='coolwarm', fmt='.2f', linewidths=0.5)
plt.title("Correlation Heatmap")
plt.show()


data["Quantity"].value_counts()

# Plotting the frequency distribution
sns.barplot(x=data["Quantity"].value_counts().index, 
            y=data["Quantity"].value_counts().values)
plt.title("Frequency Distribution of Quantity")
plt.xlabel("Quantity")
plt.ylabel("Count")
plt.show()


"quantity_by_gender"
quantity_by_gender = data.groupby('Gender')['Quantity'].sum()
print(quantity_by_gender)


quantity_by_gender_df = quantity_by_gender.reset_index()

sns.barplot(data=quantity_by_gender_df, x='Gender', y='Quantity', palette='pastel')

plt.title('Total Quantity Purchased by Gender')
plt.xlabel('Gender')
plt.ylabel('Total Quantity')
plt.show()

"Quantity by ecah city"
quantity_by_city=data.groupby("City")["Quantity"].sum()
print(quantity_by_city)

quantity_by_City_df = quantity_by_city.reset_index()
sns.barplot(data=quantity_by_City_df,x="City",y="Quantity",palette='pastel')
plt.title("Quantity by each City")
plt.xlabel("City")
plt.ylabel("Total quantity")
plt.show()





