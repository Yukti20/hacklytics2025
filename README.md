# Hacklytics 2025 - without AI!!

In this project, I am looking into the **Ethereum Dataset** from Kaggle to build a fraud detection model. Steps followed in this process are: 

1. Exploratory data analysis: This involves observing the dataset for some statstics and looking for missing values, duplicates, and outliers.
   a) The given dataset contains 9841 observations for 50 features to start with (first column before 'Index' is excluded). All the columns are in the correct data format - strings as object and numeric as int or float. The columns are renamed to remove spaces in the column names. The three string columns are 'address', 'ERC20MostSentTokenType', 'ERC20MostRecTokenType'.
   
   b) We check the number of unique elements in the 'address' column because that is supposed to be the identifier variable for this dataset and observe that it has 9816 unique values and not 9841. This tells us that we need to check for duplicate rows within the dataset. Upon further inspection, we observed that 25 addresses have 2 records with all features same except 'Index' or 'ERC20MostRecTokenType' or 'ERC20MostSentTokenType'. These three columns might not add much value to the numerical models we train, so, we decide to remove these from our dataset followed by removal of duplicates records.
   
   d) Looking at the basic stats like mean, median, quantiles, min, max values for all variables helps us identify 7 variables which have all 0 or null values indicating that these columns can also be removed from the dataset.
   
   e) After removing 10 columns and 25 duplicate records from our dataset, we are left with 9816 records for 40 features including a unique identifier 'Address' and our response variable 'FRAUD'. A quick look at the response variable, we observe that 22% of the transactions are fraudulent with 78% as regular transactions, indicating towards imbalance in data.
   
   f) Moving on to correlation plot, we observe that some of the feature pairs are highly correlated with each other - for instance ERC20MinValSent, ERC20MaxValSent, and ERC20AvgValSent are very highly correlated with each other with a correlation value of 1. These variables have all zeros in the column with very few non-zero values. Many other instances can be observed from the correlation plot. This indicates that we need to correlated variables and reduce the dimensionality of the data further.
