
 						            
# PREDICTIVE RFM SEGMENTATION	2018
 
### PREDICTIVE RFM SEGMENTATION – WHAT IT IS
Prediction and segmentation model that separates good from the bad customers, based on transactional data. RFM stands for recency, frequency and monetary, but we provide much more: prediction of future value and future probability of purchase based on current transactions. 

### WHAT DO YOU NEED = INPUT DATA
Transactional table with *16 months of current history following attributes (columns) in csv or txt*:
Following structure, order of columns and their format are crucial for successful run of the component. **Make sure your data follow the prescription:**

* List •	Purchase ID
* List •	Customer ID
* List •	Purchase Date (in YYYYMMDD format =>e.g.  20181231)!!!
* List •	Purchase Value (Money)
* List •	Product ID

For data uploading you can use Keboola’s extractor component called CSV Import.

### HOW YOU DO IT

1.	Go to connection.keboola.com - > Storage -> Tables -> create new table to your “IN” bucket
2.	For data uploading you can use Keboola’s extractor component called “CSV Import”.
Upload file with your transaction data. Be careful to declare correct delimiter. You can check if your data were imported correctly by clicking to you imported data name and selecting “Data sample” sheet.
3.	Go to Applications -> Predictive RFM Segmentation -> New configuration
4.	Configuration:  after naming your configuration
a.	 you click on “+ New Table Input” in Table input mapping section and select your file.
b.	You omit Table Output mapping section altogether and left it unmapped.
c.	In Configuration section you fill in Key you received from DataMind. 
d.	Click on “Save”
e.	Click on Run (in upper right section)
5.	After component finish its run go to Storage -> Files : your processed file will be named output_table.csv.gz - > you can download it now.

### WHAT IS IN OUTPUT FILE + INTERPRETATION

In outpu file you will receive following columns:

* List o	**Customer ID**
* List o	**Recency** – last purchase from selected period in days
* List o	**Transactions** – number of purchases customer has made in selected period
* List o	**Unique_days** – number of different days customer has made any purchase (may differ – be smaller than Transactions)
* List o	**Unique_products** – number of unique products purchased by customer
* List o	**Monetary_sum** – total amount of money spent by customer in selected period
* List o	**Prediction_probability** – probability of specific customer purchase in next 3 months. Number 1 means 100% probability and number 0 means 0% probability.
* List o	**Prediction_probability_quantiles** - Decile of probability of purchase in the next 3 months.
* List o	**Predicted_value** – customers monetary potential in next 3 months

•	Optionaly we can prepare for you a tailor-made Interpretation (Custom service for extra fee)

### POSSIBLE ERROR MESSAGES

*"Your activation key is no longer active, please contact Data Mind"*
-	Check if you entered key correctly
-	Activation key is useable only for one successful application run

*"Number of months of data is incorrect / too low or too high / correct number of months with data would be between 17 and 100"*
-	Check if you have enough time spread in your data
-	If you have too many months = data goes way too back in time, cut your data to fit the conditions

*"Maximum database contains dates dated in the future. Please repair input data and try again"*
-	Check date in your data

*"Your database is out of date. Last transaction is more than 3 months old. Algorithm accepts maximally 3 months old database. Please try again with the newer version of your database"*
-	Last, “newest” transaction can not be more than 3 months old

*"Your database is rather small. Algorithm accepts 10.000 rows as a bare minimum."*
-	With small amount of transactions model would not have sufficient quality

*"Your database is way too large. Algorithm accepts 1.000.000 rows as a maximum for automated segmentation. Contact www.datamind.cz for custom projects"*
-	You have high amount of data. Keboola component is not made for customers with so many transactions. Please contact DataMind for custom solution.

