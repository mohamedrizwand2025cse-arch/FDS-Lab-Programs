EXP NO:1.a Analyze the trend of data science job postings over the last decade.

DESCRIPTION: Use web scraping (e.g., BeautifulSoup) or APIs (e.g., LinkedIn API) to gather
data on the number of data science job postings each year. Use pandas for data manipulation
and matplotlib/seaborn for visualization.

CODE:

import pandas as pd
import matplotlib.pyplot as plt
data = {'Year': list(range(2010, 2021)),
'Job Postings': [150, 300, 450, 600, 800, 1200, 1600, 2100, 2700, 3400, 4200]}
df = pd.DataFrame(data)
plt.plot(df['Year'], df['Job Postings'], marker='o')
plt.title('Trend of Data Science Job Postings')
plt.xlabel('Year')
plt.ylabel('Number ofJob Postings')
plt.show()
----------------------------------------------------------------------------------------------------------
EXP NO:1.b Analyze and visualize the distribution of various data science roles (Data
Analyst, Data Engineer, Data Scientist, etc.) from a dataset.

DESCRIPTION: Use a dataset of job postings and categorize them into different roles. Visualize
the distribution using pie charts or bar plots.

CODE:
roles=['Data Analyst','Data Engineer','Data Scientist','ML Engineer','Business Analyst']
counts=[300,500,450,200,150]
plt.bar(roles,counts)
plt.title('Distribution of Data Science Roles')
plt.xlabel('role')
plt.ylabel('Count')
plt.show()
-----------------------------------------------------------------------------------------------------------
EXP NO:1.c Conduct an experiment to differentiate Structured , Un-structured and Semi
structured data based on data sets given.

DESCRIPTION: Create small datasets for each type and explain their characteristics.

CODE:
structured_data = pd.DataFrame({
'ID': [1, 2, 3],
'Name': ['Alice', 'Bob', 'Charlie'],
'Age': [25, 30, 35]
})
print("Structured Data:\n", structured_data)

unstructured_data = "This is an example of unstructured data. It can be a piece of text, an image,
or a video file."
print("\nUnstructured Data:\n", unstructured_data)

semi_structured_data = {'ID': 1, 'Name': 'Alice', 'Attributes': {'Height': 165, 'Weight': 68}}
print("\nSemi-structured Data:\n", semi_structured_data)
-----------------------------------------------------------------------------------------------------------
EXP NO:1.d Conduct an experiment to encrypt and decrypt given sensitive data.

Description: Use the cryptography library to encrypt and decrypt a piece of data

CODE:
from cryptography.fernet import Fernet
key = Fernet.generate_key()
f = Fernet(key)
token = f.encrypt(b"Rajalakshmi Engineering College")
token
b'...'
f.decrypt(token)
b'Rajalakshmi Engineering College'
key = Fernet.generate_key()
cipher_suite = Fernet(key)
plain_text = b"Rajalakshmi Engineering College."
cipher_text = cipher_suite.encrypt(plain_text)

decrypted_text = cipher_suite.decrypt(cipher_text)
print("Original Data:", plain_text)
print("Encrypted Data:", cipher_text)
print("Decrypted Data:", decrypted_text)
-----------------------------------------------------------------------------------------------------------
Exp No:2 Upload and Analyze the data set given in csv format and perform data
preprocessing and visualization.

Description: Use sample data set sales-data.csv.

CODE:
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

file_path='C:\sales_data.csv'
df = pd.read_csv(file_path)

print(df.head())

print(df.isnull().sum())

df['Sales'].fillna(df['Sales'].mean(), inplace=True)
df.dropna(subset=['Product', 'Quantity', 'Region'], inplace=True)

print(df.describe())

product_summary = df.groupby('Product').agg({
'Sales': 'sum',
'Quantity': 'sum'
}).reset_index()
print(product_summary)
11

plt.figure(figsize=(10, 6))
plt.bar(product_summary['Product'], product_summary['Sales'])
plt.xlabel('Product')
plt.ylabel('Total Sales')
plt.title('Total Sales by Product')
plt.show()

df['Date'] = pd.to_datetime(df['Date'])
sales_over_time = df.groupby('Date').agg({'Sales': 'sum'}).reset_index()
plt.figure(figsize=(10, 6))
plt.plot(sales_over_time['Date'],sales_over_time['Sales'])
plt.xlabel('Date')
plt.ylabel('Total Sales')
plt.title('SalesOver Time')
plt.show()

pivot_table = df.pivot_table(values='Sales', index='Region', columns='Product',
aggfunc=np.sum, fill_value=0)
print(pivot_table)

correlation_matrix = df.corr()
print(correlation_matrix)

import seaborn as sns
plt.figure(figsize=(8, 6))
sns.heatmap(correlation_matrix, annot=True, cmap='coolwarm')
plt.title('Correlation Matrix')
plt.show()
-----------------------------------------------------------------------------------------------------------
Exp No:3.a Conduct an experiment to show data visualization using line plot.

Description: Take any sample data either through csv file or data fetched directly through code

CODE:

import matplotlib.pyplot as cricket
Overs=list(range(5,51,5))
Indian_Score=[30,55,90,129,165,200,239,270,310,350]
Srilankan_Score=[25,70,90,120,140,170,195,220,255,279]
cricket.plot(Overs,Indian_Score)
cricket.plot(Overs,Srilankan_Score)
cricket.show()
cricket.title("INDIA Vs SRILANKA")
cricket.xlabel("Overs")
cricket.ylabel("Score")
cricket.legend()
cricket.plot(Overs,Indian_Score,color="green",label="INDIA")
cricket.plot(Overs,Srilankan_Score,color="red",label="SRILANKA")
cricket.legend(loc="center right")
-----------------------------------------------------------------------------------------------------------
Exp No:3.b Conduct an experiment to show data visualization using bar chart.

Description: Take any sample data either through csv file or data fetched directly through code.
 CODE:
 import matplotlib.pyplot as hscmark
import numpy as np
Names = ['SHREE', 'DEV', 'KEERTHI', 'PRIYA', 'SHAN', 'KUMARAN']
xaxis = np.arange(len(Names))
Percentage_hsc = [96, 91, 94, 75, 45, 81]
hscmark.bar(Names, Percentage_hsc)
hscmark.xticks(xaxis, Names, rotation=45)
hscmark.xlabel("Names of Pupil")
hscmark.ylabel("Percentage")
hscmark.title("Comparison of HSC Percentage", fontsize=20, color="green")
hscmark.show()
-----------------------------------------------------------------------------------------------------------
Exp No:3.c Conduct an experiment to show data visualization using pie chart.

Description: Take any sample data either through csv file or data fetched directly through code
CODE:
import matplotlib.pyplot as election
labels = ['CANDIDATE 1', 'CANDIDATE 2', 'CANDIDATE 3', 'CANDIDATE 4']
Votes = [315, 130, 245, 210]
colors = ['green', 'yellow', 'red', 'orange']
explode = (0.2, 0, 0, 0)
election.pie(Votes, labels=labels, colors=colors, explode=explode, autopct='%0.2f%%')
election.title('Election Results')
election.show()
-----------------------------------------------------------------------------------------------------------
Exp No:4 To Count the frequency of occurrence of a word in a body of text is often
needed during text processing.

Description: Import the word_tokenize function and gutenberg.

CODE:
import nltk
from nltk.tokenize import word_tokenize
from nltk.corpus import gutenberg
nltk.download('gutenberg')
nltk.download('punkt')
nltk.download('punkt_tab')
sample = gutenberg.raw("austen-emma.txt")
token = word_tokenize(sample)
wlist = []
for i in range(50):
    wlist.append(token[i])
wordfreq = [wlist.count(w) for w in wlist]
print("Pairs\n" + str([item for item in zip(wlist, wordfreq)]))
-----------------------------------------------------------------------------------------------------------
Exp No:5 Data Collection and Initial Exploration

Objective: To collect, load, and perform initial exploration of the diabetes dataset.

Materials Needed:
 Diabetes dataset (available from sources such as UCI Machine Learning Repository
or Kaggle)
 Python with libraries: pandas, numpy, matplotlib, seaborn

CODE:
import pandas as pd
db=pd.read_csv("diabetic_data.csv")
print(db.head())
print(db.info())
print(db.describe())
import matplotlib.pyplot as plt
import seaborn as sns
db.hist(bins=50,figsize=(20,15))
plt.show()
sns.pairplot(db)
plt.show()
-----------------------------------------------------------------------------------------------------------
Experiment 6: Time Series Analysis of Website Traffic
Objective: To analyze the time series data of website traffic to identify trends, seasonality,
and anomalies.
Dataset: A dataset containing daily website traffic data with columns such as Date,
Page_Views, Unique_Visitors, and Bounce_Rate.
CODE:
import pandas as pd
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

data = pd.read_csv(
    'website_traffic.csv',
    parse_dates=['Date'],
    index_col='Date'
)

decomposition = seasonal_decompose(
    data['Page_Views'],
    model='additive'
)

decomposition.plot()
plt.show()

data['Page_Views_MA'] = data['Page_Views'].rolling(window=30).mean()

data[['Page_Views', 'Page_Views_MA']].plot()
plt.title('Page Views with Moving Average')
plt.show()

data['Page_Views_Z'] = (
    data['Page_Views'] - data['Page_Views'].mean()
) / data['Page_Views'].std()

anomalies = data[data['Page_Views_Z'].abs() > 3]

plt.plot(data.index, data['Page_Views'], label='Page Views')
plt.scatter(
    anomalies.index,
    anomalies['Page_Views'],
    color='red',
    label='Anomalies'
)

plt.legend()
plt.show()
-----------------------------------------------------------------------------------------------------------
Experiment 7:. Random Sampling and Sampling Distribution

Objective:
To explore random sampling from a population and understand the concept of sampling distribution
using Python in Jupyter Notebook.

CODE:
import numpy as np
import matplotlib.pyplot as plt

population_mean = 50
population_std = 10
population_size = 100000
population = np.random.normal(population_mean, population_std, population_size)

sample_sizes = [30, 50, 100]
num_samples = 1000

sample_means = {}

for size in sample_sizes:
  sample_means[size] = []
  for _ in range(num_samples):
    sample = np.random.choice(population, size=size, replace=False)
    sample_means[size].append(np.mean(sample))
plt.figure(figsize=(12, 8))

for i, size in enumerate(sample_sizes):
  plt.subplot(len(sample_sizes), 1, i+1)
  plt.hist(sample_means[size], bins=30, alpha=0.7, label=f'Sample Size {size}')
  plt.axvline(np.mean(population), color='red', linestyle='dashed', linewidth=1.5, label='PopulationMean')
  plt.title(f'Sampling Distribution (Sample Size {size})')
  plt.xlabel('Sample Mean')
  plt.ylabel('Frequency')
  plt.legend()

plt.tight_layout()
plt.show()
-----------------------------------------------------------------------------------------------------------
Lab Experiment 8: Conduct Z test for the Data Given using Python.
Objective:
To test whether the average weight of a species of birds differs from 150 grams. 
CODE:
import numpy as np
import scipy.stats as stats
sample_data = np.array([152, 148, 151, 149, 147, 153, 150, 148, 152, 149,151, 150, 149, 152, 151,
148, 150, 152, 149, 150,148, 153, 151, 150, 149, 152, 148, 151, 150, 153])
population_mean = 150
sample_mean = np.mean(sample_data)
sample_std = np.std(sample_data, ddof=1)
n = len(sample_data)
z_statistic = (sample_mean - population_mean) / (sample_std / np.sqrt(n))
p_value = 2 * (1 - stats.norm.cdf(np.abs(z_statistic)))
print(f"Sample Mean: {sample_mean:.2f}")
print(f"Z-Statistic: {z_statistic:.4f}")
print(f"P-Value: {p_value:.4f}")
alpha = 0.05
if p_value < alpha:
  print("Reject the null hypothesis: The average weight is significantly different from 150 grams.")
else:
  print("Fail to reject the null hypothesis: There is no significant difference in average weight from 150 grams.")
-----------------------------------------------------------------------------------------------------------
Exp No:9 Experiment to understand Matplotlib library use cases in Data Science
through visualization.
Description: Use Iris data set to understand the Matplot lib library
CODE:
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt

data = sns.load_dataset('iris')

print("--- Dataset Overview ---")
print(data.head())
print("\n--- Data Info ---")
data.info()
print("\n--- Summary Statistics ---")
print(data.describe())
print("\n--- Species Count ---")
print(data.value_counts('species'))

plt.figure(figsize=(6, 4))
sns.countplot(x='species', data=data)
plt.title('Distribution of Iris Species')
plt.xlabel('Species')
plt.ylabel('Count')
plt.show()
dummies = pd.get_dummies(data.species)
FinalDataset = pd.concat([dummies, data.iloc[:, [0, 1, 2, 3]]], axis=1)
print("\n--- One-Hot Encoded Dataset Preview ---")
print(FinalDataset.head())

plt.figure(figsize=(7, 5))
sns.scatterplot(x='sepal_length', y='sepal_width', hue='species', data=data)
plt.title('Sepal Length vs Sepal Width')
plt.show()

plt.figure(figsize=(7, 5))
sns.scatterplot(x='petal_length', y='petal_width', hue='species', data=data)
plt.title('Petal Length vs Petal Width')
plt.show()
sns.pairplot(data, hue='species', height=3)
plt.suptitle('Pairwise Feature Relationships', y=1.02)
plt.show()
g = sns.FacetGrid(data, hue='species', height=5)
g.map(sns.histplot, 'sepal_width').add_legend()
plt.title('Distribution of Sepal Width by Species')
plt.show();

sns.FacetGrid(data, hue='species', height=5).map(sns.histplot, 'petal_width').add_legend();
plt.title('Distribution of Petal Width by Species')
plt.show();

sns.FacetGrid(data, hue='species', height=5).map(sns.histplot, 'sepal_length').add_legend();
plt.title('Distribution of Sepal Length by Species')
plt.show();

sns.FacetGrid(data, hue='species', height=5).map(sns.histplot, 'sepal_width').add_legend();
plt.title('Distribution of Sepal Width by Species')
plt.show();
-----------------------------------------------------------------------------------------------------------
Exp No:10 Experiment to understand array function in Data science.

Description: Understand array function using Numpy library
CODE:
import numpy as np

array = np.random.randint(1, 100, 9)
print("Original Array:")
print(array)

print("\nSquare root of array elements:")
print(np.sqrt(array))

print("\nArray dimensions:", array.ndim)

new_array = array.reshape(3, 3)
print("\nReshaped Array (3x3):")
print(new_array)

print("\nReshaped array dimensions:", new_array.ndim)

print("\nFlattened array (ravel):")
print(new_array.ravel())

newm = new_array.reshape(3, 3)
print("\nMatrix 'newm':")
print(newm)

print("\nSlice [2, 1:3]:", newm[2, 1:3])
print("Slice [1:2, 1:3]:\n", newm[1:2, 1:3])
print("Slice [0:3, 0:0]:\n", new_array[0:3, 0:0])
print("Slice [0:2, 0:1]:\n", new_array[0:2, 0:1])
print("Slice [0:3, 0:1]:\n", new_array[0:3, 0:1])
print("Slice [1:3]:\n", new_array[1:3])
-----------------------------------------------------------------------------------------------------------
Exp No:11 Experiment to understand pandas library use cases in Data science.

Description: Understand data frame use cases using pandas library.

CODE:
import numpy as np
import pandas as pd

# Renamed 'list' to 'emp_data' to avoid shadowing python built-in list type
emp_data = [[1,'Smith',50000],[2,'Jones',60000]]

df = pd.DataFrame(emp_data)
print(df)

df.columns = ['Empd','Name','Salary']
print(df)

df.info()
try:
    df = pd.read_csv("/content/50_Startups.csv")
    df.info()
    print(df.head())
    print(df.tail())
except FileNotFoundError:
    print("Error: '/content/50_Startups.csv' not found. Please upload the file to your Colab workspace.")

try:
    df = pd.read_csv("/content/employee.csv")
    print(df.head())
    print(df.tail())
    df.info()

    print(df.Salary)
    print(type(df.Salary))
    print(df.Salary.mean())
    print(df.Salary.median())
    print(df.Salary.mode())
    print(df.Salary.var())
    print(df.Salary.std())
    print(df.describe())
    print(df.describe(include='all'))
    empCol = df.columns
    print(empCol)
    emparray = df.values
    print(emparray)
    employee_DF = pd.DataFrame(emparray, columns=empCol)
    print(employee_DF)
except FileNotFoundError:
    print("Error: '/content/employee.csv' not found. Please upload the file to your Colab workspace.")
-----------------------------------------------------------------------------------------------------------
Exp No:12 Experiment to detect outliers in a given data set.
Description: Understand the procedure to identify the outliers in a given dataset.
CODE:
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt

array = np.random.randint(1, 100, 16)
print(array)

print(array.mean())
print(np.percentile(array, 25))
print(np.percentile(array, 50))
print(np.percentile(array, 75))
print(np.percentile(array, 100))

def outDetection(array):
    sorted(array)
    Q1, Q3 = np.percentile(array, [25, 75])
    IQR = Q3 - Q1
    lr = Q1 - (1.5 * IQR)
    ur = Q3 + (1.5 * IQR)
    return lr, ur

lr, ur = outDetection(array)
print(lr, ur)

sns.displot(array)

sns.distplot(array)

new_array = array[(array > lr) & (array < ur)]
print(new_array)

sns.displot(new_array)

lr1, ur1 = outDetection(new_array)
print(lr1, ur1)

final_array = new_array[
    (new_array > lr1) & (new_array < ur1)
]
print(final_array)

sns.distplot(final_array)
-----------------------------------------------------------------------------------------------------------
Exp No:13 Experiment to handle missing values and inappropriate data in a
given data set.
Description: Understand the procedure to handle missing and inappropriate data.
CODE:
import numpy as np
import pandas as pd

df = pd.read_csv("Hotel_Dataset.csv")

print(df)

print(df.duplicated())

df.info()

df.drop_duplicates(inplace=True)

print(df)

print(len(df))
index = np.arange(len(df))

df.set_index(index,inplace=True)

print(index)

df.drop(['Age_Group.1'],axis=1,inplace=True)

print(df)

df.CustomerID.loc[df.CustomerID<0] = np.nan

df.Bill.loc[df.Bill<0] = np.nan

df.EstimatedSalary.loc[df.EstimatedSalary<0] = np.nan

print(df)

df['NoOfPax'].loc[(df['NoOfPax']<1) | (df['NoOfPax']>20)] = np.nan

print(df)

print(df.Age_Group.unique())

print(df.Hotel.unique())

df.Hotel.replace(['Ibys'],'Ibis',inplace=True)

print(df.FoodPreference.unique())

df.FoodPreference.replace(
    ['Vegetarian','veg'],
    'Veg',
    inplace=True
)

df.FoodPreference.replace(
    ['non-Veg'],
    'Non-Veg',
    inplace=True
)

df.EstimatedSalary.fillna(
    round(df.EstimatedSalary.mean()),
    inplace=True
)

df.NoOfPax.fillna(
    round(df.NoOfPax.median()),
    inplace=True
)

df['Rating(1-5)'].fillna(
    round(df['Rating(1-5)'].median()),
    inplace=True
)

df.Bill.fillna(
    round(df.Bill.mean()),
    inplace=True
)

print(df)
-----------------------------------------------------------------------------------------------------------
Exp No:14 Experiment to understand feature scaling.
Description: Understand the importance of feature scaling.
CODE:
import numpy as np
import pandas as pd

df = pd.read_csv('/content/pre-process_datasample.csv')

print(df)

print(df.head())

df.Country.fillna(df.Country.mode()[0],inplace=True)

features = df.iloc[:,:-1].values

label = df.iloc[:,-1].values

from sklearn.impute import SimpleImputer

age = SimpleImputer(
    strategy="mean",
    missing_values=np.nan
)

Salary = SimpleImputer(
    strategy="mean",
    missing_values=np.nan
)

age.fit(features[:,[1]])

Salary.fit(features[:,[2]])

features[:,[1]] = age.transform(features[:,[1]])

features[:,[2]] = Salary.transform(features[:,[2]])

print(features)

from sklearn.preprocessing import OneHotEncoder

oh = OneHotEncoder(sparse_output=False)

Country = oh.fit_transform(features[:,[0]])

print(Country)

final_set = np.concatenate(
    (Country,features[:,[1,2]]),
    axis=1
)

print(final_set)

from sklearn.preprocessing import StandardScaler

sc = StandardScaler()

sc.fit(final_set)

feat_standard_scaler = sc.transform(final_set)

print(feat_standard_scaler)

from sklearn.preprocessing import MinMaxScaler

mms = MinMaxScaler(feature_range=(0,1))

mms.fit(final_set)

feat_minmax_scaler = mms.transform(final_set)

print(feat_minmax_scaler)
-----------------------------------------------------------------------------------------------------------
Exp No:15 Experiment to understand the data preprocessing in Data
science
Description: Understand the importance of Data preprocessing in data science.
CODE:
import numpy as np
import pandas as pd

df = pd.read_csv("/content/pre-process_datasample.csv")

print(df)

df.info()

print(df.Country.mode())

print(df.Country.mode()[0])

print(type(df.Country.mode()))

df.Country.fillna(
    df.Country.mode()[0],
    inplace=True
)

df.Age.fillna(
    df.Age.median(),
    inplace=True
)

df.Salary.fillna(
    round(df.Salary.mean()),
    inplace=True
)

print(df)

print(pd.get_dummies(df.Country))

updated_dataset = pd.concat(
    [
        pd.get_dummies(df.Country),
        df.iloc[:,[1,2,3]]
    ],
    axis=1
)

print(updated_dataset)

df.info()

updated_dataset.Purchased.replace(
    ['No','Yes'],
    [0,1],
    inplace=True
)

print(updated_dataset)
-----------------------------------------------------------------------------------------------------------
Exp No:16 Experiment to understand EDA-Quantitative and
Qualitative analysis.

Description: Understand the importance of EDA-Quantitative and Qualitative analysis.
CODE:
import seaborn as sns
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
%matplotlib inline

tips=sns.load_dataset('tips')

tips.head()

sns.displot(tips.total_bill,kde=True)
plt.show()

sns.displot(tips.total_bill,kde=False)
plt.show()

sns.jointplot(x=tips.tip,y=tips.total_bill)
plt.show()

sns.jointplot(x=tips.tip,y=tips.total_bill,kind="reg")
plt.show()

sns.jointplot(x=tips.tip,y=tips.total_bill,kind="hex")
plt.show()

sns.pairplot(tips)
plt.show()

tips.time.value_counts()

sns.pairplot(tips,hue='time')
plt.show()

sns.pairplot(tips,hue='day')
plt.show()

sns.heatmap(tips.corr(numeric_only=True),annot=True)
plt.show()

sns.boxplot(tips.total_bill)
plt.show()

sns.boxplot(tips.tip)
plt.show()

sns.countplot(tips.day)
plt.show()

sns.countplot(tips.sex)
plt.show()

tips.sex.value_counts().plot(kind='pie')
plt.show()

tips.sex.value_counts().plot(kind='bar')
plt.show()

sns.countplot(tips[tips.time=='Dinner']['day'])
plt.show()
-----------------------------------------------------------------------------------------------------------
Exp No:17 Experiment to understand Linear Regression for a given
data set.

Description: Understand the Linear regression for the dataset given.
CODE:
import numpy as np
import pandas as pd

df=pd.read_csv('Salary_data.csv')

df

df.info()

df.dropna(inplace=True)

df.info()

df.describe()

features=df.iloc[:,[0]].values
label=df.iloc[:,[1]].values

from sklearn.model_selection import train_test_split

x_train,x_test,y_train,y_test=train_test_split(features,label,test_size=0.2,random_state=42)

from sklearn.linear_model import LinearRegression

model=LinearRegression()

model.fit(x_train,y_train)

model.score(x_train,y_train)

model.score(x_test,y_test)

model.coef_

model.intercept_

import pickle

pickle.dump(model,open('SalaryPred.model','wb'))

model=pickle.load(open('SalaryPred.model','rb'))

yr_of_exp=float(input("Enter Years of Experience: "))

yr_of_exp_NP=np.array([[yr_of_exp]])

Salary=model.predict(yr_of_exp_NP)

print("Estimated Salary for {} years of experience is {}: ".format(yr_of_exp,Salary))
-----------------------------------------------------------------------------------------------------------
Exp No:18 Experiment to understand KNN algorithm for a given data
set.

Description: Understand the KNN algorithm for the dataset given.
CODE:
import numpy as np
import pandas as pd

df=pd.read_csv('Iris.csv')

df.info()

print(df.variety.value_counts())

print(df.head())

features=df.iloc[:,:-1].values

label=df.iloc[:,4].values

from sklearn.model_selection import train_test_split

from sklearn.neighbors import KNeighborsClassifier

xtrain,xtest,ytrain,ytest=train_test_split(features,label,test_size=0.2,random_state=42)

model_KNN=KNeighborsClassifier(n_neighbors=5)

model_KNN.fit(xtrain,ytrain)

print(model_KNN.score(xtrain,ytrain))

print(model_KNN.score(xtest,ytest))

from sklearn.metrics import confusion_matrix

print(confusion_matrix(label,model_KNN.predict(features)))

from sklearn.metrics import classification_report

print(classification_report(label,model_KNN.predict(features)))
-----------------------------------------------------------------------------------------------------------
Exp No:19Experiment to understand Logistic Regression for a given
data set.

 Description: Understand the Logistic Regression algorithm for the dataset given.
 CODE:
 import numpy as np
import pandas as pd

df=pd.read_csv('Social_Network_Ads.csv')

df

df.head()

features=df.iloc[:,[2,3]].values

label=df.iloc[:,4].values

print(features)

print(label)

from sklearn.model_selection import train_test_split

from sklearn.linear_model import LogisticRegression

x_train,x_test,y_train,y_test=train_test_split(features,label,test_size=0.2,random_state=37)

finalModel=LogisticRegression()

finalModel.fit(x_train,y_train)

print(finalModel.score(x_train,y_train))

print(finalModel.score(x_test,y_test))

from sklearn.metrics import classification_report

print(classification_report(label,finalModel.predict(features)))
-----------------------------------------------------------------------------------------------------------
Exp No:20Experiment to understand K-means clustering algorithm for
a given data set.

Description: Understand the K-means clustering algorithm for the dataset given.
CODE:
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
%matplotlib inline

df=pd.read_csv('Mall_Customers.csv')

df.info()

print(df.head())

sns.pairplot(df)

plt.show()

features=df.iloc[:,[3,4]].values

from sklearn.cluster import KMeans

model=KMeans(n_clusters=5)

model.fit(features)

Final=df.iloc[:,[3,4]]

Final['label']=model.predict(features)

print(Final.head())

sns.set_style("whitegrid")

sns.FacetGrid(Final,hue="label",height=8).map(plt.scatter,"Annual Income (k$)","Spending Score (1-100)").add_legend()

plt.show()

features_el=df.iloc[:,[2,3,4]].values

from sklearn.cluster import KMeans

wcss=[]

for i in range(1,10):
    model=KMeans(n_clusters=i)
    model.fit(features_el)
    wcss.append(model.inertia_)

plt.plot(range(1,10),wcss)

plt.show()
