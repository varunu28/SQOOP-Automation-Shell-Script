# SQOOP-Automation-Shell-Script
A shell script to automate the daily/weekly workflow of data backup through SQOOP

# Business Problem

#### Tables 

Tables provided in retail_db database by cloudera in the quickstart VM. Please refer the [Exercise](https://www.cloudera.com/developers/get-started-with-hadoop-tutorial/exercise-1.html) to view the representation

- departments
- categories
- products
- order_items
- orders
- customers

#### General Requirements

- The script should take a backup every weekday at 11:00 PM with registering only the delta for that day and not completely reloading the data
- The script should take a complete backup every Sunday at 5:00 AM with wiping out the previous data and loading the latest data as registered on Saturday day end

#### Table Specific Requirements

- departments and categories to be stored in a CSV format in HDFS (Mappers = 2)
- products: Only store the product_id,product_category_id, product_name and product_price in tab separated format in HDFS (Mappers = 2)
- orders and order_items to be stored using compression in Avro format in HDFS (Mappers = 4)
- customers to be stored in tab separated format with their passwords masked in HDFS (Mappers = 2)

#### Reporting 

- The script should send a daily report of the load describing the count of new data inserted every weekday 
- The script should send a confirmation mail of replacement of complete backup on Sunday
- The script should send a mail in case of error describing the error message and details about the table
