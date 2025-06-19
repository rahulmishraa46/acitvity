Here's a well-structured activity in Markdown format for your students to create an ETL pipeline using Apache Airflow:

```markdown
# Apache Airflow ETL Pipeline Activity

## Objective
Create an Apache AirFlow DAG that performs ETL (Extract, Transform, Load) operations on a sample dataset. The pipeline should demonstrate key Airflow concepts including operators, dependencies, and task flow.

## Dataset: Sales Data
We'll use a sample sales dataset (`sales_data.csv`) available at:
[https://example.com/sales_data.csv](https://example.com/sales_data.csv) (or provide actual dataset)

Sample data:
```
order_id,customer_id,order_date,product_id,product_name,quantity,unit_price,total_amount
1001,C101,2023-01-15,P001,Laptop,1,1200,1200
1002,C102,2023-01-16,P002,Smartphone,2,800,1600
1003,C103,2023-01-17,P003,Headphones,3,150,450
...
```

## Tasks

### 1. Extract Task
- Create a PythonOperator task to download the dataset from the URL
- Save it to `/data/raw/sales_data.csv` in your Airflow environment
- Add error handling for failed downloads

### 2. Transform Tasks
Create multiple tasks to perform these transformations:

**a. Clean Data (PythonOperator)**
- Handle missing values
- Convert date strings to proper datetime objects
- Ensure numeric fields have correct data types

**b. Calculate Metrics (PythonOperator)**
- Create a new column `discounted_price` applying 10% discount to orders over $1000
- Calculate total sales by product
- Identify top 5 customers by purchase amount

### 3. Load Tasks
**a. Load to Database (PostgresOperator or PythonOperator)**
- Create a PostgreSQL table with appropriate schema
- Load the transformed data into the table

**b. Generate Report (PythonOperator)**
- Create a summary report in JSON format containing:
  - Total sales
  - Average order value
  - Number of unique customers
- Save to `/data/reports/sales_summary_{execution_date}.json`

## Requirements
1. Create a DAG named `sales_etl_pipeline`
2. Set appropriate scheduling (daily)
3. Implement proper task dependencies
4. Add error handling and email alerts on failure
5. Include documentation in your DAG file
6. Use Airflow's logging capability

## Bonus Challenges
1. Add data validation checks between tasks
2. Implement a data quality check using Airflow's `ShortCircuitOperator`
3. Create a dynamic task that processes each product category separately
4. Add a task to upload the report to an S3 bucket

## Submission
1. Your DAG file (`sales_etl.py`)
2. Screenshots of the successful run from Airflow UI
3. Sample output files (CSV and JSON)
4. A brief report explaining your implementation

## Evaluation Criteria
- Proper DAG structure and task organization
- Correct implementation of ETL operations
- Error handling and robustness
- Code quality and documentation
- Creativity in solution (for bonus points)

---

**Note to Instructor**: 
You may want to:
1. Provide the actual dataset link or include sample data
2. Adjust complexity based on student level
3. Prepare a PostgreSQL database for students or have them use SQLite
4. Provide a base DAG template for beginners
```

This activity covers all key aspects of ETL pipeline creation with Airflow while allowing flexibility for different skill levels. You can customize the dataset or requirements as needed for your specific teaching context.
