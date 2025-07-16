import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import os

if not os.path.exists("plots"):
    os.makedirs("plots")

data = pd.read_csv("sales.csv")
data.dropna(inplace=True)

plt.figure(figsize=(8, 5))
plt.plot(data['Month'], data['Revenue'], marker='o')
plt.title("Monthly Revenue")
plt.xlabel("Month")
plt.ylabel("Revenue")
plt.grid(True)
plt.tight_layout()
plt.savefig("plots/Line_Chart.png")
plt.close()

plt.figure(figsize=(8, 5))
plt.bar(data['Product'], data['Sales'], color='skyblue')
plt.title("Product Sales")
plt.xlabel("Product")
plt.ylabel("Sales")
plt.tight_layout()
plt.savefig("plots/Bar_Chart.png")
plt.close()

plt.figure(figsize=(6, 6))
plt.pie(data['Market Share'], labels=data['Company'], autopct='%1.1f%%')
plt.title("Market Share")
plt.savefig("plots/Pie_Chart.png")
plt.close()

plt.figure(figsize=(8, 6))
sns.heatmap(data.corr(), annot=True, cmap='coolwarm')
plt.title("Correlation Heatmap")
plt.tight_layout()
plt.savefig("plots/Heatmap.png")
plt.close()

with open("plots/Summary_Report.txt", "w") as file:
    file.write("Data Visualized Successfully:\n")
    file.write("1. Line Chart: Monthly Revenue\n")
    file.write("2. Bar Chart: Product Sales\n")
    file.write("3. Pie Chart: Market Share\n")
    file.write("4. Heatmap: Correlation\n")
    file.write("\nThank you, ProSensia Internship Day 14 ✅")

print("All charts saved in 'plots' folder.")

