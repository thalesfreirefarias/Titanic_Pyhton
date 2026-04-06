# 🚢 Titanic Analysis (Python Project)

![GitHub repo size](https://img.shields.io/github/repo-size/SEU_USER/SEU_REPO?style=for-the-badge)
![GitHub language count](https://img.shields.io/github/languages/count/SEU_USER/SEU_REPO?style=for-the-badge)
![GitHub forks](https://img.shields.io/github/forks/SEU_USER/SEU_REPO?style=for-the-badge)
![GitHub issues](https://img.shields.io/github/issues/SEU_USER/SEU_REPO?style=for-the-badge)

---

## 📌 Project Overview

This project explores the Titanic dataset using Python (Pandas, Matplotlib) to identify the key factors that influenced passenger survival.

The analysis focuses on variables such as:

* Gender
* Passenger class
* Age
* Embarkation port

The goal is to simulate a real-world data analysis scenario and extract meaningful insights to support data-driven decisions.

---

## 📊 Dataset Information

The dataset contains 891 passengers.

```python
total_passengers = df.shape[0]
print(total_passengers)
```

---

## 🚨 Survival Analysis

### How many passengers survived?

```python
result = df['Survived'].value_counts().sort_index()
print(result)
```

* 549 passengers did not survive
* 342 passengers survived

```python
import matplotlib.pyplot as plt

result = df['Survived'].value_counts().sort_index()

ax = result.plot(kind='bar')

total = result.sum()

for i, v in enumerate(result):
    percentage = (v / total) * 100
    ax.text(i, v, f'{v} ({percentage:.1f}%)', ha='center')

plt.title('Titanic Survival')
plt.xlabel('0 = No | 1 = Yes')
plt.ylabel('Total')
plt.xticks(rotation=0)
plt.show()
```

---

### 📈 Survival Percentage

```python
result = df['Survived'].value_counts(normalize=True) * 100
print(result)
```

* 38.38% survived
* 61.62% did not survive

---

## 👨‍👩‍👧 Gender Distribution

```python
sex_counts = df['Sex'].value_counts()
print(sex_counts)
```

---

## 🚢 Embarkation Ports

```python
embarked_counts = df['Embarked'].value_counts(dropna=False)
print(embarked_counts)
```

* C (Cherbourg): 168 passengers
* Q (Queenstown): 77 passengers
* S (Southampton): 644 passengers
* Missing: 2 passengers

---

## ⚖️ Survival by Gender

```python
survival_by_gender = df.groupby(['Sex', 'Survived']).size().unstack()
print(survival_by_gender)
```

* Approximately 74% of females survived
* Approximately 19% of males survived

---

## 🏷️ Passengers by Class

```python
class_counts = df['Pclass'].value_counts().sort_index()
print(class_counts)
```

* 1st Class: 216 passengers
* 2nd Class: 184 passengers
* 3rd Class: 491 passengers

---

## 📊 Survival by Class

```python
survival_by_class = df.groupby(['Pclass', 'Survived']).size().unstack()
print(survival_by_class)
```

* 1st Class: 136 survived
* 2nd Class: 87 survived
* 3rd Class: 119 survived

---

## 📉 Survival Rate by Class (%)

```python
survival_rate_class = df.groupby('Pclass')['Survived'].mean() * 100
print(survival_rate_class)
```

* 1st Class: ~63%
* 2nd Class: ~47%
* 3rd Class: ~24%

---

## 🎂 Age Analysis

```python
mean_age = df['Age'].mean()
max_age = df['Age'].max()
min_age = df['Age'].min()

print(mean_age, max_age, min_age)
```

---

## 🧠 Key Insights

* Survival was strongly influenced by gender and social class
* Women had a significantly higher survival rate than men
* First-class passengers had better survival chances
* Socioeconomic factors played a major role in survival

---

## ⚠️ Data Quality

* Missing values were found in:

  * Age
  * Cabin

These were handled appropriately during the analysis.

---

## 🛠️ Technologies Used

* Python
* Pandas
* Matplotlib
* Google Colab

---

## 🤝 Author

<table>
  <tr>
    <td align="center">
      <a href="https://www.linkedin.com/in/thalesfreirefarias/" target="_blank">
        <img src="grecia.jpg" width="100" alt="Thales Farias"/><br>
        <sub><b>Thales Farias</b></sub>
      </a>
    </td>
  </tr>
</table>
