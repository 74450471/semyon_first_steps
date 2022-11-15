# semyon first_steps
## data processing class; midterm assignment 

##part 1(troubles with reading CSV file) 

- I uploaded the zip files from zip 
- Had troubles with opening them all at once 
- I had to upload each from the zip folder separately
- I used following commands: 
```
import pandas as pd
import zipfile
zf = zipfile.ZipFile(r'C:\Users\smnsr\Downloads\justynaCase.zip')
df = pd.read_csv(zf.open('file_name.csv'))
```
##part 1.1
**question 1**

- Is there a company that has no difference between Close and Adj Close column?
- I have created the zero_difference file that substracts Adj Close from Close 
- I had to import each file separately ,e.g. ABMD.csv
```
import pandas as pd
import zipfile
zf = zipfile.ZipFile(r'C:\Users\smnsr\Downloads\justynaCase.zip')
df = pd.read_csv(zf.open('ABMD.csv'))
print(df)
```
- to find whether Close and Adj Close are different, I added a new column derived from the substraction operation on columns Close - Adj Close
```
df['zero_difference']=df['Close']-df['Adj Close']
print(df)
```
- to find which particular values were similar or different I subsetted the rows using logical condition inside t=of square brackets 
```
df[df['zero_difference'] == 0]
```
- I then setted the zero_difference column to index 
```
df_ind = df.set_index('zero_difference')
print(df_ind)
```

- Answer: the company ABMD had no difference between Close and Adj Close
