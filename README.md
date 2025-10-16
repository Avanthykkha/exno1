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
 import numpy as np
 import pandas as pd
 data=pd.read_csv("/content/SAMPLEIDS.csv")
 data
```
 # Output
 <img width="1139" height="851" alt="Screenshot 2025-10-04 135005" src="https://github.com/user-attachments/assets/d006fe53-a687-45f2-bdcf-7b0c00a90443" />
 
```
 data.head(4)
```
 # Output
 <img width="1203" height="264" alt="Screenshot 2025-10-04 135019" src="https://github.com/user-attachments/assets/cedc693e-b1e0-42dc-8447-3581f32878ba" />

 ```
 data.tail(7)
```
 # Output
 <img width="1158" height="378" alt="Screenshot 2025-10-04 135033" src="https://github.com/user-attachments/assets/8de235ee-0996-41b6-9125-7587859b6f64" />

```
data.isnull()
```
 # Output
 <img width="1025" height="839" alt="Screenshot 2025-10-04 135047" src="https://github.com/user-attachments/assets/6dc40726-e6bf-4210-b8c3-1cd07e5261af" />

```
 data.notnull()
```
 # Output
 <img width="1033" height="848" alt="Screenshot 2025-10-04 135059" src="https://github.com/user-attachments/assets/91bdf39c-5670-4c5e-b5a5-439cc363c28d" />

 ```
data.isnull().sum()
```
 # Output
 <img width="1076" height="673" alt="Screenshot 2025-10-04 135112" src="https://github.com/user-attachments/assets/3a16975c-30ce-4665-ab2a-698784bd5ad6" />

 ```
data.isnull().any()
```
 # Output
 <img width="1001" height="647" alt="Screenshot 2025-10-04 135124" src="https://github.com/user-attachments/assets/f649424d-8824-4c2d-b7cf-ea0f4a3e9200" />

 ```
data.dropna(axis=1)
```
 # Output
 <img width="1154" height="845" alt="Screenshot 2025-10-04 135137" src="https://github.com/user-attachments/assets/850765bb-cf3e-4b29-9664-118247213333" />

```
data.dropna(axis=0)
```
 # Output
 <img width="1198" height="646" alt="Screenshot 2025-10-04 135147" src="https://github.com/user-attachments/assets/ed0efabd-505d-4bfd-9667-97eafea6a328" />

 ```
data.fillna(0)
```
 # Output
 <img width="1175" height="831" alt="Screenshot 2025-10-04 135159" src="https://github.com/user-attachments/assets/eb321eab-a5e4-420c-8bdb-b0cf848acbca" />

```
 data.fillna(method="ffill")
```
 # Output
 <img width="1294" height="847" alt="Screenshot 2025-10-04 135216" src="https://github.com/user-attachments/assets/fc06dbd3-ff59-4663-bd45-5db5c4865b71" />

```
data.bfill()
```
 # Output
 <img width="1149" height="852" alt="Screenshot 2025-10-04 135231" src="https://github.com/user-attachments/assets/b2beb3b0-7244-4a24-ae0e-15db8b81a2e8" />

```
 data.fillna({'REGNO':0, 'NAME':'PRAVEEN'})
```
 # Output
 <img width="1192" height="848" alt="Screenshot 2025-10-04 135243" src="https://github.com/user-attachments/assets/fcd8d42a-6f65-4c97-86ab-494f17e7b73c" />

 ```
 ir=pd.read_csv("/content/iris.csv")
 ir
```
 # Output
<img width="940" height="602" alt="Screenshot 2025-10-04 135253" src="https://github.com/user-attachments/assets/4eb43014-7a61-4bcd-846c-81824f99d0af" />

```
ir.describe()
```
 # Output
 <img width="1069" height="440" alt="Screenshot 2025-10-04 135303" src="https://github.com/user-attachments/assets/7b48c7d5-06fb-4b42-851f-1d00c62ad0f7" />

 ```
 import seaborn as sns
 sns.boxplot(x="sepal_width",data=ir)
```
 # Output
 <img width="1059" height="667" alt="Screenshot 2025-10-04 135312" src="https://github.com/user-attachments/assets/2be419a0-2755-4981-8d99-6f7622d54a17" />

 ```
 q1=ir.sepal_width.quantile(0.25)
 q3=ir.sepal_width.quantile(0.75)
 iqr=q3-q1
 print(iqr)
```
 # Output
 <img width="1087" height="167" alt="Screenshot 2025-10-04 135324" src="https://github.com/user-attachments/assets/886ab04b-7b95-4455-ba71-0e1c1e20a93f" />

 ```
 rid=ir[((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
 rid['sepal_width']
```
 # Output
 <img width="1149" height="356" alt="Screenshot 2025-10-04 135333" src="https://github.com/user-attachments/assets/d35913de-8aac-4ebc-8eec-c776f9d6ed55" />

```
 rid=ir[~((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
 rid
```
# Output
 <img width="1067" height="586" alt="Screenshot 2025-10-04 135343" src="https://github.com/user-attachments/assets/47366ccd-077d-4000-a46b-e7455b43b1f2" />

 ```
rid=ir[((ir.sepal_width>(q1-1.5*iqr))&(ir.sepal_width<(q3+1.5*iqr)))]
rid['sepal_width']
```
 # Output
 <img width="1070" height="634" alt="Screenshot 2025-10-04 135353" src="https://github.com/user-attachments/assets/ea19e19b-55a7-4d6c-a279-18e5f9f293ea" />

 ```
 import numpy as np
 import scipy.stats as stats
 z=np.abs(stats.zscore(ir.sepal_width))
 z
```
 # Output
 <img width="1105" height="801" alt="Screenshot 2025-10-04 135406" src="https://github.com/user-attachments/assets/876185e2-4e30-407c-b198-f32fd6b7d2d1" />

# Result
 Thus the programs are executed successfully.
