### EX4 Implementation of Cluster and Visitor Segmentation for Navigation patterns
### DATE: 4.11.2026
### NAME: S. Sri Ramsharan
### REG NO.: 212224050424


### AIM: To implement Cluster and Visitor Segmentation for Navigation patterns in Python.
### Description:
<div align= "justify">Cluster visitor segmentation refers to the process of grouping or categorizing visitors to a website, 
  application, or physical location into distinct clusters or segments based on various characteristics or behaviors they exhibit. 
  This segmentation allows businesses or organizations to better understand their audience and tailor their strategies, marketing efforts, 
  or services to meet the specific needs and preferences of each cluster.</div>
  
### Procedure:
1) Read the CSV file: Use pd.read_csv to load the CSV file into a pandas DataFrame.
2) Define Age Groups by creating a dictionary containing age group conditions using Boolean conditions.
3) Segment Visitors by iterating through the dictionary and filter the visitors into respective age groups.
4) Visualize the result using matplotlib.

### Program:
```python
import pandas as pd
import matplotlib.pyplot as plt

# Read CSV file
df = pd.read_csv(r"C:\Users\admin\Downloads\clustervisitor (1).csv")

# Assign clusters manually based on Age
def assign_cluster(age):
    if age <= 31:
        return 2
    elif age <= 41:
        return 0
    else:
        return 1

df["Cluster"] = df["Age"].apply(assign_cluster)

# ----------------------------
# Display Complete Dataset
# ----------------------------
print("\n========== COMPLETE DATASET ==========\n")
print(df)

# ----------------------------
# Display Each Cluster
# ----------------------------
for i in [0, 1, 2]:
    print(f"\n========== CLUSTER {i} ==========\n")
    print(df[df["Cluster"] == i])




```
### Output:

<img width="1101" height="862" alt="image" src="https://github.com/user-attachments/assets/d63a805e-22ce-42a0-ac70-a376e26ba474" />
<img width="1103" height="893" alt="image" src="https://github.com/user-attachments/assets/3c7267d2-e6fc-43e8-9edf-6f7785a9c259" />
<img width="1090" height="863" alt="image" src="https://github.com/user-attachments/assets/f8033ea0-13a7-43e3-a4e8-6a81f9521b43" />


### Visualization:
```python
# Create a list to store counts of visitors in each age group
visitor_counts = []

# Count visitors in each age group
age_groups = {
    "Young": df[df['Age'] <= 30],
    "Middle": df[(df['Age'] > 30) & (df['Age'] <= 50)],
    "Old": df[df['Age'] > 50]
}

for group, visitors in age_groups.items():
    visitor_counts.append(len(visitors))

# Define age group labels and plot a bar chart
age_group_labels = list(age_groups.keys())

plt.figure(figsize=(8, 6))
plt.bar(age_group_labels, visitor_counts, color='skyblue')
plt.xlabel('Age Groups')
plt.ylabel('Number of Visitors')
plt.title('Visitor Distribution Across Age Groups')
plt.show()
```
### Output:

<img width="978" height="1004" alt="image" src="https://github.com/user-attachments/assets/b81322d3-e7cf-48e0-8e2d-71f4cd913476" />

### Result:


Thus the cluster and visitor segmentation for navigation patterns was implemented successfully in python.
