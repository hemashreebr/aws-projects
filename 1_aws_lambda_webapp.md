# Deploy Simple Web Applications in AWS Lambda

## 1. Pre-requisites
Ensure you have an AWS account with administrative access. If you don’t have an AWS account, create a free trial account using the AWS website.

---

## 2. Create IAM Role
Create an IAM role that the AWS Lambda function will use to authorize calls to other AWS services.

### Steps:
1. Log in to the AWS Console and select **Ireland** as the region.
2. Navigate to the IAM Management Console and select **Roles** from the left menu.
3. Click on **Create role**.
4. On the next screen:
   - Select **Lambda** as the service.
   - Click **Next: Permissions**.
5. Choose **PowerUserAccess** as the policy and click **Next: Tags**.
6. Click **Next: Review**.
7. Enter `lambdarole` as the **Role name**.
8. Click **Create role**.

---

## 3. Create DynamoDB Table
Create a DynamoDB table to store data for the web application.

### Steps:
1. Navigate to the **DynamoDB Console**.
2. Select **Tables** from the left menu and click **Create table**.
3. Enter `webapptable` as the **Table name**.
4. Set `email` as the **Partition key** with **String** as the data type.
5. Keep other settings as default and click **Create table**.

---

## 4. Create Lambda Function
Create a Lambda function that hosts the business logic and UI of the web application.

### Steps:
1. Navigate to the **Lambda Console**.
2. Select **Functions** from the left menu and click **Create function**.
3. Choose **Author from scratch**.
4. Enter `webfunction` as the function name.
5. Select **Python 3.8** as the runtime.
6. Choose **Use an existing role** and select `lambdarole`.
7. Click **Create function**.
8. Upload the function code:
   - Download the zip file [`function.zip`](https://example.com/function.zip).
   - Click **Upload from**, select **.zip file**, and upload `function.zip`.
   - Click **Save**.

The function handles web requests and interacts with DynamoDB.

---

## 5. Create API Gateway
Configure API Gateway to expose the Lambda function via a REST API.

### Steps:
1. Navigate to the **API Gateway Console**.
2. Click **Build** for the **REST API**.
3. Select **New API**, enter `webapi`, and choose **Regional** for the endpoint type.
4. Click **Create API**.
5. Create the **GET** method:
   - Click **Create Method** under **Actions**.
   - Select **GET** and confirm.
   - Choose **Lambda Function** as the integration type.
   - Select **Use Lambda Proxy integration**.
   - Enter `webfunction` as the Lambda function.
   - Click **Save** and confirm API Gateway permissions.
6. Repeat the above steps to create a **POST** method.
7. Deploy the API:
   - Click **Deploy API** under **Actions**.
   - Select **[New Stage]**, enter `dev`, and click **Deploy**.
   - Note the **Invoke URL**.

---

## 6. Test Web Application
1. Open a web browser and navigate to the **Invoke URL**.
2. Fill out and submit the form on the web page.
3. Verify the data is inserted into the **DynamoDB table**.
4. Optionally, update the Lambda function to handle HTML decoding.

---

## 7. Clean Up
To avoid unnecessary costs, delete the created resources:
1. Delete `webapi` in **API Gateway**.
2. Delete `webfunction` in **Lambda**.
3. Delete `webapptable` in **DynamoDB**.
4. Delete `lambdarole` in **IAM**.


