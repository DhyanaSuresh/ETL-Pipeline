# ETL Pipeline with AWS Glue: A Step-by-Step Guide 📊🔧

This guide walks you through the process of building a seamless **ETL (Extract, Transform, Load) pipeline** using **AWS Glue** and related services. From sourcing data in S3, transforming it with AWS Glue, and querying the results with Amazon Athena, this project ensures a robust data processing workflow. 🚀

---

## Step 1: Create S3 Buckets 🗂️  
1. **Create Source Bucket**  
   Click "Create bucket" and follow the prompts to create a new S3 bucket. This will hold your source data (CSV files).  
   
2. **Create Target Bucket**  
   Create another S3 bucket to store your transformed data.  
   
3. **Create Athena Bucket**  
   Set up an additional S3 bucket to store the results for querying with Athena.

---

## Step 2: Create IAM Role for AWS Glue 🔑  
1. **Choose Use Case**  
   Select **"Glue"** for the role use case.  
   
2. **Attach Permissions Policies**  
   - Attach **AmazonS3FullAccess** policy for S3 access.  
   - Attach **AWSGlueServiceRole** policy for Glue service access.

---

## Step 3: Upload CSV Files to Source Bucket 📥  
Upload your CSV files to the **source S3 bucket**.  
> **Tip:** Create a folder inside the bucket and upload your files into that folder. This avoids issues where Athena might return zero records when running queries.

---

## Step 4: Set Up AWS Glue Crawler 🕵️‍♂️  
1. **Create a Crawler**  
   - Go to the AWS Glue Console > Crawlers > Create Crawler.  
   - Specify a name, select **S3** as the data store, and provide the path to your source bucket.  
   - Complete the wizard to create the crawler.  
   
2. **Crawl the Data**  
   Once the crawler is set up, check the database, and you’ll see your tables generated automatically.

---

## Step 5: Create an ETL Job in AWS Glue ⚙️  
1. **Add a Job**  
   - Go to AWS Glue Console > Jobs > Add job.  
   - Specify the source and target connections, and define transformation logic with the Glue ETL script.  
   
2. **Run the ETL Job**  
   - Select the source bucket (Amazon S3) with the customer data catalog table.  
   - Choose the target and transformation buckets (also in S3).  
   - Set job details (name, IAM role), and then save and run the job.  
   
3. **Verify Job Status**  
   Go to **Runs** and check for the **"Succeeded"** status.

---

## Step 6: Check Transformed Data in Target Bucket 📂  
After the job runs successfully, verify that the transformed data is loaded into the target S3 bucket. The files will be automatically added to the designated target folder.

---

## Step 7: Set Up Amazon Athena 🔍  
1. **Enable Athena Queries**  
   Go to **Settings > Manage**, browse to select the **Athena Bucket**, and save the configuration.  
   
2. **Run SQL Queries**  
   Use the Athena query editor to run SQL queries on your cataloged tables and analyze the transformed data.  
> Tip: Provide your custom queries to see the processed data in action.

---

## Step 8: Run Queries in Athena 💻  
Leverage the full power of Athena to run queries on your cataloged tables. Analyze and gain insights from the transformed data with SQL queries tailored to your needs.

---

## Conclusion 🎉  
By following this guide, you’ve successfully set up a complete **ETL pipeline** using AWS Glue, from data extraction through transformation to querying. This powerful, automated workflow allows for seamless data processing, ready for deeper analysis. With your new pipeline in place, you're equipped to scale your data operations and unlock new insights in your data-driven projects. 🌐🚀

Happy coding! 👩‍💻👨‍💻
