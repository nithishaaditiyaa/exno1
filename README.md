# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
```
heights.py:

import pandas as pd
import numpy as np
from scipy import stats
import seaborn as sns
import matplotlib.pyplot as plt


df = pd.read_csv('heights.csv')
print(df.head(),"\n")

df.info()
print()

print(df.describe(),"\n")

df.isnull()
print(df.isnull().sum())
print()

df_fill_0 = df.fillna(0)
print(df_fill_0,"\n")

df_ffill = df.ffill()
print(df_ffill,"\n")

df_bfill = df.bfill()
print(df_bfill,"\n")

df['height'] = df['height'].fillna(df['height'].mean())
print(df,"\n")

df_dropna = df.dropna()
print(df_dropna,"\n")

sns.boxplot(x=df['height'])
plt.show()
print()

Q1 = df['height'].quantile(0.25)
Q3 = df['height'].quantile(0.75)
IQR = Q3 - Q1
print("IQR:", IQR,"\n")

outliers_iqr = df[
    (df['height'] < (Q1 - 1.5 * IQR)) |
    (df['height'] > (Q3 + 1.5 * IQR))
]
print(outliers_iqr,"\n")

ir_cleaned = df[
    ~((df['height'] < (Q1 - 1.5 * IQR)) |
      (df['height'] > (Q3 + 1.5 * IQR)))
]
print(ir_cleaned,"\n")

df_z = df['height']

z_scores = np.abs(stats.zscore(df_z))
print(z_scores,"\n")

threshold = 3
outliers_z = df_z[z_scores > threshold]
print("Outliers:",outliers_z,"\n")
     
df_z_cleaned = df_z[z_scores <= threshold]
print(df_z_cleaned,"\n")

<img width="785" height="1079" alt="Screenshot 2026-02-06 111839" src="https://github.com/user-attachments/assets/e615c13e-13eb-4ddb-81c0-09e715f89294" />

<img width="349" height="383" alt="Screenshot 2026-02-06 111848" src="https://github.com/user-attachments/assets/bd6d7ce8-52e0-4a57-8d95-c90b01557ee3" />

iris.py:

import pandas as pd
import numpy as np
from scipy import stats
import seaborn as sns
import matplotlib.pyplot as plt


df = pd.read_csv('iris.csv')
print(df.head(),"\n")

df.info()
print()

print(df.describe(),"\n")

df.isnull()
print(df.isnull().sum())
print()

df_fill_0 = df.fillna(0)
print(df_fill_0,"\n")

df_ffill = df.ffill()
print(df_ffill,"\n")

df_bfill = df.bfill()
print(df_bfill,"\n")

df['sepal_length'] = df['sepal_length'].fillna(df['sepal_length'].mean())
print(df,"\n")

df_dropna = df.dropna()
print(df_dropna,"\n")

sns.boxplot(x=df['sepal_width'])
plt.show()
print()

Q1 = df['sepal_width'].quantile(0.25)
Q3 = df['sepal_width'].quantile(0.75)
IQR = Q3 - Q1
print("IQR:", IQR,"\n")

outliers_iqr = df[
    (df['sepal_width'] < (Q1 - 1.5 * IQR)) |
    (df['sepal_width'] > (Q3 + 1.5 * IQR))
]
print(outliers_iqr,"\n")

ir_cleaned = df[
    ~((df['sepal_width'] < (Q1 - 1.5 * IQR)) |
      (df['sepal_width'] > (Q3 + 1.5 * IQR)))
]
print(ir_cleaned,"\n")

df_z = df['sepal_width']

z_scores = np.abs(stats.zscore(df_z))
print(z_scores,"\n")

threshold = 3
outliers_z = df_z[z_scores > threshold]
print("Outliers:",outliers_z,"\n")
     
df_z_cleaned = df_z[z_scores <= threshold]
print(df_z_cleaned,"\n")

<img width="663" height="1054" alt="Screenshot 2026-02-06 152158" src="https://github.com/user-attachments/assets/0ab775e4-cbbf-49f1-9687-c73e4801488f" />
<img width="673" height="901" alt="Screenshot 2026-02-06 152208" src="https://github.com/user-attachments/assets/9ee6b89f-16d5-407d-be15-8f454b6e728e" />

Data_set.py:

import pandas as pd
import numpy as np
from scipy import stats
import seaborn as sns
import matplotlib.pyplot as plt

df = pd.read_csv('Data_set.csv')
print(df.head(),"\n")


df.info()
print()


print(df.describe(),"\n")


df.isnull()
print(df.isnull().sum())
print()


df_fill_0 = df.fillna(0)
print(df_fill_0,"\n")


df_ffill = df.ffill()
print(df_ffill,"\n") 


df_bfill = df.bfill()
print(df_bfill,"\n")


df['rating'] = df['rating'].fillna(df['rating'].mean())
print(df,"\n")

df_dropna = df.dropna()
print(df_dropna,"\n")


sns.boxplot(x=df['rating'])
plt.show()
print()

Q1 = df['rating'].quantile(0.25)
Q3 = df['rating'].quantile(0.75)
IQR = Q3 - Q1
print("IQR:", IQR,"\n")

outliers_iqr = df[
    (df['rating'] < (Q1 - 1.5 * IQR)) |
    (df['rating'] > (Q3 + 1.5 * IQR))
]
print(outliers_iqr,"\n")

ir_cleaned = df[
    ~((df['rating'] < (Q1 - 1.5 * IQR)) |
      (df['rating'] > (Q3 + 1.5 * IQR)))
]
print(ir_cleaned,"\n")

df_z = df['rating'].dropna()

z_scores = np.abs(stats.zscore(df_z))
print(z_scores,"\n")

threshold = 3
outliers_z = df_z[z_scores > threshold]
print("Outliers:",outliers_z,"\n")
     
df_z_cleaned = df_z[z_scores <= threshold]
print(df_z_cleaned,"\n")

<img width="778" height="924" alt="Screenshot 2026-02-06 152435" src="https://github.com/user-attachments/assets/048006af-86c1-409d-8aef-538b6f4fe546" />
<img width="763" height="880" alt="Screenshot 2026-02-06 152446" src="https://github.com/user-attachments/assets/975bfb4b-d765-4d79-b112-9b307e4f244a" />
<img width="743" height="733" alt="Screenshot 2026-02-06 152452" src="https://github.com/user-attachments/assets/22c969e1-20f5-47c3-87ed-184e4f5c29f3" />

SAMPLEIDS.py:

import pandas as pd
import numpy as np
from scipy import stats
import seaborn as sns
import matplotlib.pyplot as plt


df = pd.read_csv('SAMPLEIDS.csv')
print(df.head(),"\n")

df.info()
print()

print(df.describe(),"\n")

df.isnull()
print(df.isnull().sum())
print()

df_fill_0 = df.fillna(0)
print(df_fill_0,"\n")

df_ffill = df.ffill()
print(df_ffill,"\n")

df_bfill = df.bfill()
print(df_bfill,"\n")

df['TOTAL'] = df['TOTAL'].fillna(df['TOTAL'].mean())
print(df,"\n")

df_dropna = df.dropna()
print(df_dropna,"\n")

sns.boxplot(x=df['TOTAL'])
plt.show()
print()

Q1 = df['TOTAL'].quantile(0.25)
Q3 = df['TOTAL'].quantile(0.75)
IQR = Q3 - Q1
print("IQR:", IQR,"\n")

outliers_iqr = df[
    (df['TOTAL'] < (Q1 - 1.5 * IQR)) |
    (df['TOTAL'] > (Q3 + 1.5 * IQR))
]
print(outliers_iqr,"\n")

ir_cleaned = df[
    ~((df['TOTAL'] < (Q1 - 1.5 * IQR)) |
      (df['TOTAL'] > (Q3 + 1.5 * IQR)))
]
print(ir_cleaned,"\n")

df_z = df['TOTAL'].dropna()

z_scores = np.abs(stats.zscore(df_z))
print(z_scores,"\n")

threshold = 3
outliers_z = df_z[z_scores > threshold]
print("Outliers:",outliers_z,"\n")
     
df_z_cleaned = df_z[z_scores <= threshold]
print(df_z_cleaned,"\n")

<img width="687" height="565" alt="Screenshot 2026-02-06 153133" src="https://github.com/user-attachments/assets/5f3b09f8-d8eb-47dd-9bbe-d2fe66b19b85" />
<img width="765" height="1069" alt="Screenshot 2026-02-06 153143" src="https://github.com/user-attachments/assets/15c34aad-04c0-42f2-9220-36eebc50c80a" />
<img width="671" height="671" alt="Screenshot 2026-02-06 153149" src="https://github.com/user-attachments/assets/ea779339-aa99-4220-97e8-4ac61831686b" />

Loan_Data.py:

import pandas as pd
import numpy as np
from scipy import stats
import seaborn as sns
import matplotlib.pyplot as plt


df = pd.read_csv('Loan_data.csv')
print(df.head(),"\n")

df.info()
print()

print(df.describe(),"\n")

df.isnull()
print(df.isnull().sum())
print()

df_fill_0 = df.fillna(0)
print(df_fill_0,"\n")

df_ffill = df.ffill()
print(df_ffill,"\n")

df_bfill = df.bfill()
print(df_bfill,"\n")

df['LoanAmount'] = df['LoanAmount'].fillna(df['LoanAmount'].mean())
print(df,"\n")

df_dropna = df.dropna()
print(df_dropna,"\n")

sns.boxplot(x=df['LoanAmount'])
plt.show()
print()

Q1 = df['LoanAmount'].quantile(0.25)
Q3 = df['LoanAmount'].quantile(0.75)
IQR = Q3 - Q1
print("IQR:", IQR,"\n")

outliers_iqr = df[
    (df['LoanAmount'] < (Q1 - 1.5 * IQR)) |
    (df['LoanAmount'] > (Q3 + 1.5 * IQR))
]
print(outliers_iqr,"\n")

ir_cleaned = df[
    ~((df['LoanAmount'] < (Q1 - 1.5 * IQR)) |
      (df['LoanAmount'] > (Q3 + 1.5 * IQR)))
]
print(ir_cleaned,"\n")

df_z = df['LoanAmount'].dropna()

z_scores = np.abs(stats.zscore(df_z))
print(z_scores,"\n")

threshold = 3
outliers_z = df_z[z_scores > threshold]
print("Outliers:",outliers_z,"\n")
     
df_z_cleaned = df_z[z_scores <= threshold]
print(df_z_cleaned,"\n")

<img width="685" height="1041" alt="Screenshot 2026-02-06 153432" src="https://github.com/user-attachments/assets/21e8a36b-8b51-4963-9709-908b09fc7e1b" />
<img width="673" height="852" alt="Screenshot 2026-02-06 153441" src="https://github.com/user-attachments/assets/aebf1ab5-0c66-4490-80a0-5b8ce5ebaad1" />
<img width="688" height="900" alt="Screenshot 2026-02-06 153451" src="https://github.com/user-attachments/assets/253ad889-be9e-44b8-9755-804fa6688827" />
<img width="801" height="1065" alt="Screenshot 2026-02-06 153501" src="https://github.com/user-attachments/assets/7e35c1eb-4112-4f34-8b7f-83cebb28784d" />
<img width="687" height="728" alt="Screenshot 2026-02-06 153509" src="https://github.com/user-attachments/assets/6651c6fe-bcb9-4f56-8d16-6d3176e0f3b7" />

```
# Result

The given data has been successfully read, cleaned by handling duplicates and missing values, and saved to a new file named cleaned_data.csv.
