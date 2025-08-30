# MLOps-Skills

### Boto3 is an important Library when we want to work with AWS S3; Experiments will get saved in S3 Bucket and MLFlow server will pick it up from there

### Refer to - AWS Cloud EC2,IAM,S3 Bucket Set Up - 79th Video for AWS Setup

### Python Faker Library used to create syntentic data - To generate synthetic real-time transactions, I will use the Python library Faker. [Used in Grafana Project]

## "psycopg2" – It is used to connect Python with PostgreSQL.

## In Grafana Project - Used AWS, PostgreSQL, Grafana

## DVC includes versioning of not only data but also models and other artifacts

### DVC - The key difference between GitHub and DAGsHub lies in the additional features DAGsHub provides. In DAGsHub, three main functionalities are supported. First, it allows uploading data to DAGsHub, enabling the tracking of data using DVC. This includes versioning of not only data but also models and other artifacts. Second, it allows leveraging Git versioning for code. Third, it provides the ability to log experiments using MLflow; In contrast, GitHub primarily supports version control for code, while DAGsHub extends this by also offering support for data versioning, model versioning, and experiment logging. DAGsHub provides up to 10 GB of free remote repository storage for uploading data, using an S3 bucket in the backend. It supports data, models, notebooks, DVC, and Git, all in one integrated environment. Additionally, it supports running MLflow tracking servers directly in DAGsHub, similar to how MLflow servers are run locally; 

## DVC also has options to configure storage with S3 or Google Drive for additional capacity. The platform provides options to upload and version data using Git and DVC. In the next step, DVC will be used to demonstrate how to version data within the same repository.Other functionalities available in DAGsHub include Experiments, Models, and Collaboration. Collaborators can be invited to work together on the same repository. Annotation capabilities are also provided, which are especially useful for computer vision projects, where data sources can be annotated directly in the platform.

## First Dagshub Project - At first stage, the repository has been created in DAGsHub. To start coding, the repository must first be initialized with Git. The first example to be implemented will focus on uploading data to DAGsHub and ensuring that the data is versioned using DVC. Later steps will include tracking code and logging experiments with MLflow.

### Pytest library is used for unit testing. It is capable of executing Python unit test cases.

### Now the workflow for automated testing using GitHub Actions will be created. Inside the repository, create a folder named .github. Inside this, create another folder named workflows. Within workflows, create a YAML file named unit-test.yml. The GitHub Action configuration is always defined in YAML files. A GitHub Actions extension can be installed in VS Code for convenience. After installing, sign in to GitHub if required. Now open the unit-test.yml file and define the workflow. A GitHub Action workflow is defined using key-value pairs. [Refer to "GitHub Action Practicals - Automate Testing Workflow With Python" Project for more information

## GitHub Actions expects few things like key-value pair, the first key is name, which specifies the workflow name. In this example: name: Python CI; the next key is on, which specifies the events that will trigger the workflow. Workflows can be triggered on events like push, pull request, merge, or delete. Here, the workflow will trigger on push and pull request events on the main branch:

**A) Getting Started with MLFlow Tracking Server**

**B) MLFlow with AWS**

**C) Grafana - Open Source Tool for Data Visualization and Monitoring**

**D) Getting Started with Dagshub**

**E) GitHub Action Practicals - Automate Testing Workflow With Python**



**A) Getting Started with MLFlow Tracking Server**

1. Type "mlflow ui: in command prompt and it provides mlflow tracking URL; Once if we abort this, we won't be tracking anything

2. mlflow.set_tracking_uri("http://127.0.0.1:5000") **Providing Tracking URI using Python code**

3. **Just a Sample test of MLFlow Tracking Server** - mlflow.set_experiment("Check Local Host Connection")

with mlflow.start_run():
    mlflow.log_metric("Test",1)
    mlflow.log_metric("Ashwath",2)

**We will have a folder called mlruns in VS Code, and in that we have meta.yaml; It have some details**

**We have some id thing it and it corresponds to Experiment in MLFlow**


##### **In Between Started NLP Project**

**A) End to End ML Project with HuggingFace and Transformers:**

**HuggingFace provides models for NLP, Computer Vision,etc..**

**We will use a Existing Model and FineTune it; We will also use Dataset from HuggingFace**

**All models in Hugging Face, Transformer library's usage will be generic for tokenizer, checkpoint,etc..**






**B) MLFlow with AWS**

### In this Project, we won't host the entire application on AWS Cloud, but store experiments; Later on we will do end-to-end projects, where we will host application in Cloud

**1. MLFlow Project Setup with Installation**

We are going to build a very simple data science project and use MLflow hosted on an AWS EC2 instance to track experiments. The idea is not to host the full data science application yet, but only to set up MLflow tracking so that all experiment logs are stored in AWS. Later, in more advanced modules, we will extend this setup to include full deployment of a project.

The first step is setting up the project structure. You can start by creating a new folder, for example mlops or rds_project. It doesn’t matter where the folder is created; there are no restrictions. Once the folder is ready, open it in a terminal. You can do this by copying the path and opening it in Command Prompt, or by simply typing cmd in the folder’s address bar. From the terminal, launch VS Code by typing code . which will open the folder in the editor where we will write our code.

Inside VS Code, we first need a virtual environment. Using conda, we can create an isolated Python environment with the command:
conda create -p venv python==3.10 -y. The -p flag ensures that the venv folder is created within the project folder itself. The -y option allows the installation to proceed without asking for confirmation. Once this process completes, you’ll see the venv folder appear in your project.

Next, we add a requirements.txt file that lists all the libraries we need. For this project, we will use mlflow for experiment tracking, scikit-learn for model building and metrics, and boto3 to interact with AWS S3 buckets. S3 is important because MLflow will save all experiment metadata and artifacts to a bucket, and the MLflow server will read from there to display results. Installing these requirements can be done with the command: pip install -r requirements.txt.

After setting up the environment and installing dependencies, we create a Python file named app.py. This is where we’ll write the main code. To keep track of the work and steps, we can also add a README.md file titled MLflow on AWS. This document can be updated as we proceed through the project.

Inside app.py, we begin by importing the necessary libraries. These include os and warnings for basic operations, sys and logging for managing logs, pandas and numpy for data manipulation, and essential modules from scikit-learn such as mean_squared_error, mean_absolute_error, r2_score, train_test_split, and the ElasticNet model. We also import from urllib.parse and, importantly, MLflow modules such as mlflow, mlflow.sklearn, and mlflow.models.signature to manage model logging and signatures.

Since we will evaluate regression models, we define a helper function called evaluate_metrics that calculates Root Mean Squared Error (RMSE), Mean Absolute Error (MAE), and R² score based on actual and predicted values. These metrics provide a clear picture of model performance.

Finally, we structure the code with a main entry point using if __name__ == "__main__":. Inside this block, we will later add the logic for splitting data, training the model, and logging experiments to MLflow. This modular way of coding is closer to industry practice, moving beyond Jupyter notebooks to a more production-ready style.

This completes the foundation of the project. In the next step, we will focus on adding the training pipeline, experiment logging, and MLflow integration with AWS S3.

**2. Implementing the End-to-End Project with MLFlow**

## Readme file has very great explanation with respect to AWS Working

We have already created the function called evaluate_metrics and we have also set up the environment. Now, the next step is to divide the main code into four different parts. The very first part will be reading the dataset, which we can call data ingestion. So, data ingestion here simply means reading the dataset into our program.

The dataset that we are going to use this time is the Wine Quality dataset. The interesting part of this dataset is that it contains several features such as fixed acidity, volatile acidity, citric acid, residual sugar, chlorides, free sulfur dioxide, total sulfur dioxide, and many more. The target column, or output feature, is quality, which represents the quality of wine. Based on the input features, the task is to predict the wine quality, which can take values like 5, 6, 7, and so on. To achieve this, we will train a machine learning model on this dataset.

We will be reading the dataset directly from a CSV file hosted online. To do this, we first store the CSV file link in a variable, say csv_url. Then we use a try-except block to handle exceptions while reading the dataset. Inside the try block, we write data = pd.read_csv(csv_url, sep=";"). This ensures that if the dataset is available, it will be successfully read into a pandas DataFrame. If there is an issue with the URL, the except block will catch the error, and we will log the exception using logger.exception with a message like “Unable to download the data.” This way, we have proper exception handling in place for the data ingestion step.

After reading the dataset, the next step is splitting it into training and test sets. We will use train_test_split from scikit-learn for this. By default, this will create a 75%-25% split. Once the split is done, we can separate features and labels. The target column is quality, so for training features we will use train_x = train.drop("quality", axis=1) and similarly test_x = test.drop("quality", axis=1). For labels, we take train_y = train["quality"] and test_y = test["quality"]. This gives us the input and output sets for both training and testing.

Next, we prepare the hyperparameters required for the ElasticNet model. The ElasticNet model requires two key parameters: alpha and l1_ratio. These can be tuned to adjust the model’s performance. To make the code flexible, we will allow these parameters to be set from the command line while running the script. We do this by checking the sys.argv list. For example, alpha = float(sys.argv[1]) if len(sys.argv) > 1 else 0.5. This means if the user provides a value from the command line, it will be used; otherwise, the default value will be 0.5. Similarly, l1_ratio = float(sys.argv[2]) if len(sys.argv) > 2 else 0.5. This way, both hyperparameters can either be user-specified or default to 0.5.

Once the dataset is prepared and parameters are set, we begin the MLflow run. We write with mlflow.start_run(): to initialize the run. Inside this block, we create the ElasticNet model as lr = ElasticNet(alpha=alpha, l1_ratio=l1_ratio, random_state=42). Then we fit the model using the training data: lr.fit(train_x, train_y). After fitting, we predict on the test set using predictions = lr.predict(test_x). To evaluate performance, we call our earlier defined evaluate_metrics function, which calculates RMSE, MAE, and R² score.

We also print some details to the console for visibility. This includes the model type, alpha, l1_ratio, and the calculated metrics. However, the real benefit comes from logging these details with MLflow. We use mlflow.log_param("alpha", alpha) and mlflow.log_param("l1_ratio", l1_ratio) to log hyperparameters. For metrics, we use mlflow.log_metric("rmse", rmse), mlflow.log_metric("mae", mae), and mlflow.log_metric("r2", r2). This ensures that every experiment run stores its parameters and metrics in MLflow.

At this stage, everything is working locally, but our goal is to track experiments on a remote MLflow server hosted in AWS. For this, we need to configure the remote server URI. Right now, we keep the URI placeholder blank, since the EC2 instance has not been created yet. Later, once we launch an EC2 instance, we will set the URI to point to that server. To configure it, we will use mlflow.set_tracking_uri(remote_server_uri). This tells MLflow to log experiments to the remote AWS server instead of the local file system.

We also check the tracking store scheme. If the store type is not file, then we log the model to the MLflow Model Registry as well. This is done with:

mlflow.sklearn.log_model(lr, "model", registered_model_name="ElasticnetWineModel")


If the store is of type file, we still log the model locally using mlflow.sklearn.log_model(lr, "model"). This ensures that the model is always logged, regardless of where MLflow is tracking.

This completes the implementation of the full project code. All necessary steps—data ingestion, splitting, training, evaluation, and experiment logging—are handled. The only remaining part is the remote setup in AWS. In the next step, we will create and configure an EC2 instance, set up IAM roles and permissions, and establish the S3 bucket connection for storing artifacts. To help with this, we also document the process in the README.md file, where we outline step-by-step instructions for opening AWS EC2, creating IAM users, working with the AWS console, and executing required commands in the EC2 instance.

So far, we have completed two major things: first, the entire project implementation locally, and second, preparing the steps required for the AWS cloud setup. In the next phase, we will move on to AWS EC2 cloud setup with MLflow to complete the remote experiment tracking workflow.

**3. AWS Cloud EC2,IAM,S3 Bucket Set Up:**

In our previous step, we successfully created the MLflow settings, implemented the complete data science project, and set up the logging of all our metrics. At this stage, our code already contains the remote server URI, which is still blank, because we have not yet set up the AWS EC2 instance. In the README file, I have also listed out the detailed steps that we need to follow for setting up MLflow on AWS. Now, in this part, we will go through those steps one by one and perform each action directly, so that by the end, our MLflow tracking will happen in the AWS EC2 instance.

The very first thing to do is to log in to the AWS Management Console. To do this, you can simply search on Google for AWS Console Login. Once you open the official link, you will be able to sign in to your AWS account. After logging in, you should see your AWS console dashboard, which gives access to all the available services. This is the starting point for all our AWS-related tasks.

The second step is to create an IAM user with administrator access. The reason we assign administrator access here is so that the user can access multiple AWS services easily, such as S3, EC2, and IAM. However, note that in real company environments, you will not usually be given full administrator access — instead, you will get only the permissions necessary for your role. To create the user, search for IAM in the AWS console, open the Users section, and then click on Create User. For this tutorial, I am naming the user MLflowUser. I will not enable console access for this user, since the main purpose is programmatic access. Instead of adding the user to a group, I will directly attach policies. Here, I select the policy AdministratorAccess. After confirming, click on Create User.

Once the user is created, you can open the user details and go to the Security Credentials tab. Under this tab, you will find the option to create Access Keys. These keys will allow programmatic access to AWS services. Select Command Line Interface (CLI) as the use case, confirm, and then create the key. You will receive an Access Key ID and a Secret Access Key. Please make sure to download the .csv file that contains these credentials, because you will not be able to view the secret key again later. This completes the IAM user creation step.

The next step is to configure the AWS CLI on your local machine. First, you need to install the AWS CLI tool. Simply search for AWS CLI Download on Google, and you will find the official installation page. The page provides installers for Linux, macOS, and Windows. On Linux, you can install using command-line instructions. On macOS, you can use the graphical installer. On Windows, the process is even easier — just download the .msi installer, double-click it, and complete the installation. Once installed, you can test by opening your terminal or command prompt and typing aws. If everything is installed correctly, you will see the help menu and available commands.

Now, to configure the CLI with your credentials, run the command aws configure. This command will prompt you for the Access Key ID, the Secret Access Key, the default region, and the default output format. Here, I enter the keys I obtained from the IAM user. For the default region, I am using us-east-1. For the output format, I select json. Once complete, your local environment will be connected to your AWS account through the CLI. This finishes the third step.

The fourth step is to create an S3 bucket. An S3 bucket is essentially a cloud storage container where we can store objects such as data, artifacts, and MLflow experiment logs. To create a bucket, search for S3 in the AWS console, open the S3 service, and click Create Bucket. For this project, I am naming my bucket mlflow-tracking-1. Remember that bucket names must be globally unique. Also, uncheck the option Block all public access so that your code will be able to access the bucket. Acknowledge the warning about public access and then click Create Bucket. After creation, if you open the bucket, you will see it is currently empty. Later, MLflow will automatically create folders such as mlruns here to store experiment details.

The next step is to create an EC2 instance. This instance will host our MLflow tracking server. To do this, search for EC2 in the AWS console and click Launch Instance. Provide a name, for example mlflow-tracking. Then select the operating system as Ubuntu. For this project, the free tier eligible t2.micro instance type is sufficient. You also need to create or select a key pair for the instance, which generates a .pem file. Save this file because it is necessary if you want to connect to your EC2 instance later via SSH. For networking, enable both Allow HTTP traffic from the internet and Allow HTTPS traffic from the internet. The default storage size of 8GB is more than enough for our use case. Finally, launch the instance.

Once the instance is created, it will initially appear in a pending state. After a few seconds, the status will change to running. Now we need to configure the security group for the instance. Specifically, MLflow requires access on port 5000, so we must open this port. To do this, go to the instance details, click on Security, then open the security group. Edit the inbound rules, add a new rule with Custom TCP Rule, set the port number to 5000, and set the source to 0.0.0.0/0 so that it can be accessed publicly. Save the rule. Now, our EC2 instance is ready to host MLflow.

The final step in this phase is to connect to the EC2 instance. From the instance page, select the instance and click Connect. Choose EC2 Instance Connect, which opens a terminal directly in the browser. This will give you a command-line interface into your Ubuntu EC2 instance. Once the terminal loads, you can clear the screen and begin executing the setup commands. Inside the EC2 instance, we need to install essential tools such as Python3, pip, virtual environment, MLflow, AWS CLI, and boto3. After the setup is complete, we will run the MLflow server command on this instance.

At this point, we have finished all the AWS preparation steps: logging in, creating the IAM user, configuring the AWS CLI, creating the S3 bucket, launching the EC2 instance, and setting up the security group. In the next step, we will execute the actual commands inside the EC2 instance to install the dependencies and launch the MLflow tracking server. This will allow us to connect our local MLflow client to the remote server and store all experiment logs in the S3 bucket.

**4. AWS EC2 Instance- Setting MLFLOW Tracking**

We have already created the EC2 instance, and if you recall, we followed all five important steps before reaching this stage. First, we logged into the AWS Management Console. Then we created an IAM user with administrator access. After that, we configured the credentials in the AWS CLI by downloading and installing the CLI locally. Next, we created an S3 bucket to store our MLflow artifacts. Finally, we launched an EC2 instance and added the necessary security group rule to open port 5000, which is required for MLflow.

Now that these steps are done, the next task is to run the MLflow server on the EC2 machine. To do this, we need to execute several commands step by step in the EC2 terminal. The reason is simple: MLflow must be running inside the EC2 instance itself so that it can act as our remote tracking server.

The first command to run inside the EC2 shell is sudo apt update. This updates the package list for Ubuntu, ensuring that the latest versions of software can be installed. Once the update completes, the next command is to upgrade and install Python pip by running sudo apt install python3-pip. During the installation, the system may ask for confirmation. You should type “yes” and continue. This step may take a little time since it installs Python pip and related dependencies.

After pip is installed, the next step is to install pipenv, which is used to manage Python environments. Initially, if we try running sudo pip3 install pipenv, the system might show an error saying that this environment is externally managed and recommend using apt install instead. So, the correct way is to use sudo apt install pipenv. Similarly, if we want to install virtualenv, we can run sudo apt install virtualenv. With this, we will have both pipenv and virtual environments available.

Next, we create a directory for MLflow by running mkdir mlflow. After creating the folder, we navigate inside it with cd mlflow. Now, inside this directory, we install MLflow itself by running pipenv install mlflow. This step may take some time, since MLflow will also install its dependencies. Once it is completed, MLflow will be set up inside the EC2 instance.

Along with MLflow, we also need to install the AWS CLI library and Boto3, since MLflow uses them for communication with AWS services. We do this by running pipenv install awscli, followed by pipenv install boto3. Both commands may take a few minutes depending on the package size. Additionally, we install the shell environment using pipenv shell. When this is executed, a virtual environment shell launches, and you will notice that the terminal prompt changes to reflect that you are now inside the MLflow environment.

At this point, we configure AWS credentials within the EC2 environment by running aws configure. Just like we did locally, this will ask for the AWS Access Key ID, Secret Access Key, default region, and output format. Here, we provide the same keys we created earlier for the IAM user. For the default region, we enter us-east-1, and for output format, we can either leave it blank or set it to json. This ensures that the EC2 environment has permissions to interact with the S3 bucket we created earlier.

The next step is to launch the MLflow server itself. In the MLflow documentation, the command looks like this:

**PGSQL** - mlflow server \
--backend-store-uri sqlite:///mlflow.db \
--default-artifact-root s3://mlflow-tracking-1 \
--host 0.0.0.0 --port 5000

Here, the --default-artifact-root points to the S3 bucket we created earlier (mlflow-tracking-1), so we replace it with our own bucket name. The host is set to 0.0.0.0 so that it can accept external connections, and the port is set to 5000, which we already opened in the security group. Once this command is executed, MLflow starts running inside the EC2 instance and begins listening on port 5000.

Now, if we go back to the AWS console and copy the public IP address of our EC2 instance, we can test it by opening http://<public-ip>:5000 in a browser. This should open the MLflow UI, confirming that our remote MLflow server is up and running successfully.

At this point, the MLflow server is ready, but our experiments are still not being tracked remotely. The reason is that in our code, we must update the remote_server_uri with the actual public IP of the EC2 instance along with port 5000. In our app.py file, we replace the placeholder URI with something like:

**Python** - remote_server_uri = "http://<public-ip>:5000"
mlflow.set_tracking_uri(remote_server_uri)

After updating this, we also need to make sure the MLflow tracking URI is exported in the terminal before running the script. This can be done in two ways. One option is to set it temporarily by running:

**GitBash** - export MLFLOW_TRACKING_URI=http://<public-ip>:5000

The other option is to set it programmatically in the code itself using: "import os; os.environ["MLFLOW_TRACKING_URI"] = "http://<public-ip>:5000"

Either approach works, and it depends on whether you prefer to manage the environment variable in your terminal or directly in the Python script.

Now, when we execute the code by running python app.py, the experiments are successfully tracked on the remote MLflow server. We can confirm this by reloading the MLflow UI in the browser, where we see the experiment name, metrics like RMSE, MAE, and R², as well as the registered model and artifacts such as model.pkl and requirements.txt. At the same time, if we open the S3 bucket in the AWS console, we will also see the corresponding folders created by MLflow, containing the artifacts and models.

This confirms that our setup is working end to end — the local code is logging metrics and models, the EC2 instance is hosting the MLflow server, and S3 is storing the artifacts.

Finally, it is very important to clean up resources once we are done. In the AWS console, we should terminate the EC2 instance to avoid incurring unnecessary charges. Similarly, we can delete the IAM user that we created specifically for MLflow if it is no longer required. The S3 bucket, however, can remain since it does not generate costs unless storage usage is high.

This completes the entire project workflow: from setting up AWS IAM, S3, and EC2, to installing dependencies inside the instance, launching the MLflow server, configuring the tracking URI, and successfully tracking experiments remotely. Following the README step by step ensures that nothing is missed, and this mirrors the way such deployments are done in real industry scenarios.

### **C) Grafana - Open Source Tool for Data Visualization and Monitoring - Project: Transaction Fraud Detection using Rules**

**1. Grafana Cloud Set Up And Problem Statement**

## Project: Transaction Fraud Detection using Rules

## Target Column - Decision

We now continue our discussion with the Grafana module. In this part, I will guide you step by step on how to create an account in Grafana Labs. To begin with, go to grafana.com and click on Sign In. If you do not already have an account, you will need to register first. Registration can be done using a Google account or any other preferred account. For this demonstration, I will choose one of my accounts and create a new Grafana account so that you can clearly see the process from the beginning.

By default, once you register, Grafana will provide you with a stack URL in the format: "<username>.grafana.net"

The default region is set to US East, and after confirming the details, you simply need to click on Finish Setup. That’s it—the Grafana Labs instance will be set up. Once this is complete, we will be able to use Grafana for monitoring purposes, create dashboards, and visualize data in real time. Since the instance takes a few moments to load, let us use that time to discuss the problem statement we will be working on.

The chosen problem statement is transaction fraud detection using rules, specifically for credit card transactions. Please note that the dataset I will use here is synthetic data generated for demonstration purposes, since I cannot use real company data due to privacy concerns.

In this context, each transaction record has several fields such as unique ID, transaction type, amount, currency, account holder name, merchant category, card type, account ID, account blacklisted flag, rules triggered, and explanation. The goal is to decide whether a given transaction should be accepted or rejected based on certain rules.

In real-world banking, there are multiple transaction categories, such as acquisition transactions, credit transactions, deposits, payments, refunds, bank transfers, and chargebacks. For this demo, however, we will simplify the problem and consider only three categories:

(i) Dispute transactions – A reversal that occurs when a customer disputes a charge with their bank.

(ii) Real-time transactions – Everyday payments, such as paying at a grocery store with a credit card.

(iii) Settlements – Transactions where funds are transferred between payer and payee banks via a clearing house.

To generate synthetic real-time transactions, I will use the Python library Faker. This library helps simulate transaction details such as amounts, merchant categories, and card information. Using this, we will create a dataset that mimics actual banking transactions.

The core of the project involves creating hard-coded rules that check specific conditions to either accept or reject a transaction. For example, rules could be based on whether an account is blacklisted, whether suspicious merchant categories are involved, or if unusual transaction amounts are detected. Later, these rules can be replaced by a machine learning model for more accurate fraud detection.

Once the rules are implemented, we will integrate the results with Grafana. The idea is to push these transaction events into a data source (for example, hosted on AWS) and then use Grafana dashboards to monitor fraudulent vs. legitimate transactions in real time.

At this point, our Grafana dashboard is ready, and in the next part, we will move into the coding implementation. We will walk through the Python code used to generate synthetic data, apply fraud detection rules, and set up data sources in AWS to link everything with Grafana. Finally, we will visualize fraud detection results on interactive Grafana dashboards.

**2. Visualization Implementation With Grafana Cloud And Postgresql In AWS**

We are going to continue the discussion with respect to our Grafana project. Now let’s go ahead and do this particular project that is transaction fraud detection using rules. The main aim here is to create some fake dataset with all required fields. After that, we will write some rules. If some of the fields match a particular rule, then some information will be triggered and pushed into the data source so that all this information will be displayed in the Grafana dashboard. For this implementation, Grafana Labs is being used.

To begin, I opened my Jupyter notebook. In the requirements.txt file, I am using three libraries. The first is psycopg2, then you have faker (which is used to create fake datasets), and finally pandas. I have already created an environment called development and I have selected that environment. You should be familiar with how to create an environment, and if not, you can go ahead and create one. I have already completed the installation. To do the installation, I opened my terminal, and from the command prompt (where I was already inside my development environment), I wrote "pip install -r requirements.txt". Once this is done, some warnings may appear, but it shows that all requirements are already satisfied.

Now, the next step is writing some rules. So, I imported the required libraries. I imported random, from datetime I imported datetime, then from faker I imported the Faker library, which I will use to create my fake dataset. I also imported pandas. I defined three different rules: df_rules_triggered, df_rules_explanation, and df_decision. Initially, these values will all be None. Later, I will show what values will be assigned.

Let us say I create a function "df_run_rules". This function takes a dataframe as input. Inside this dataframe, initially all three values (rules_triggered, rules_explanation, and decision) are set to None. In the problem statement, I mentioned I will consider three categories. So that is why I am making three categories here.

Now let us talk about the rules. One rule is: if df['amount'][0] > 100 and df['account_blacklisted'][0] == False, and one more condition is if df['transaction_type'][0] == "real time transaction", then we will trigger Rule 1. For this case, rules_triggered = "Rule 1". For rules_explanation, I write “User is trying to make a transaction of more than $100”. And for decision, the transaction should be rejected. You can change this later if you want, but for now this is the condition. So I am saying: if the amount is greater than 100, the account is not blacklisted, and the transaction type is “real time transaction”, then the decision should be “Rejected”.

Similarly, I add another condition. If account_blacklisted[0] == True and transaction_type == "real time transaction", then we trigger Rule 2. The explanation will be “Blacklisted card”. Again, the decision is “Rejected”.

Finally, if transaction_type == "real time transaction", then rules_triggered = "No rules triggered", and decision = "Approved". In the else block, no rules are triggered and remaining values remain None. So in summary, Rule 1 rejects transactions above 100, Rule 2 rejects blacklisted cards, and otherwise it is approved if real time.

After this, I convert everything into a dictionary index, so that for every row we get a dictionary of values. This is my entire function "run_rules".

Now comes the important part: I need to create fake data, because based on that data the rules will run. So, I define a function using the Faker library. The number of records to generate can be defined — for example, I define 10 records. I also create a list of merchant categories for random selection. Then, the card type will be chosen randomly between Visa and MasterCard.

Ignore the host part for now — that is just to connect to PostgreSQL, because I need a data source. The plan is: create a table in PostgreSQL to hold all this data.

So, I write the SQL query: "CREATE TABLE IF NOT EXISTS banking_data (...)". This table contains all the features mentioned in my document. After creating the query, I run "cursor.execute(...)" and "connection.commit()".

Next, I define the function "generate_record". Inside this, the card type is randomly chosen. Then a unique ID is generated using "fake.uuid4()". The transaction type is chosen randomly between real time, settlement, or dispute. The amount is generated using "random.uniform(10, 1000)". The account holder name is generated using "fake.name()". Card presence is randomly selected as present or not present. Merchant category is chosen randomly from the list of merchant categories. Card type is chosen, card ID is generated using "fake.credit_card_number()", and account ID again with "fake.uuid4()". Account blacklisted is randomly True or False.

Now, while the program runs in an infinite loop (while True), we generate one record each time. We put this into a pandas dataframe. Then, we run the dataframe through the "run_rules" function. Based on the rules, we get dictionary values for decision, explanation, and rules triggered. Then we prepare the SQL insert query: "INSERT INTO banking_data (...)" with all these generated values. After that, we commit the record into the database.

Finally, the code waits for 60 seconds (or 15 seconds, depending on how you set it). So continuously, every few seconds, new records are generated and inserted into PostgreSQL. In short, the Faker library is generating real-time fake data, rules are applied, and records are inserted into PostgreSQL.

Now the next part is setting up PostgreSQL. For this, I am using AWS RDS. I search for Relational Database Service in AWS. In RDS, I create a new DB instance. I select PostgreSQL as the engine. I choose the free tier template. I set the master username as postgres and master password as postgres. Public access is enabled, because I am connecting from my local machine. Then I click Create Database.

After some time, the database is created. The important information I need is the endpoint address. This endpoint will be my host in the code. The port is 5432 (default for PostgreSQL). The database name is postgres, the username is postgres, and the password is postgres.

Now, I use these details to connect in my Python code: "psycopg2.connect(host=..., port=5432, dbname='postgres', user='postgres', password='postgres')". From this connection, I get a cursor and start inserting records.

To check if records are inserted, I open DBeaver. In DBeaver, I create a new connection with PostgreSQL. I put the endpoint, user postgres, password postgres. I test the connection — it is successful. Then I open the database. In the schema public, I can see my table banking_data. I write the query "SELECT * FROM banking_data;" and execute it. Initially, there was a connection error (localhost refused), so I disconnected and reconnected again. After testing again, the connection was successful.

Now, when I run "SELECT * FROM banking_data;", I can see the records being generated. Every 15 seconds, new records are inserted. I can see all fields including decision = Approved/Rejected.

Next, I go to Grafana. Since my database is running on AWS endpoint, I add a new data source in Grafana. I select PostgreSQL. I enter host (endpoint), port 5432, database postgres, user postgres, password postgres. The version is 9.3. I click Connect — it shows successful.

Now I create a dashboard. I click on Add Visualization. I select PostgreSQL as the data source. I can run queries to visualize. For example, I run "SELECT COUNT(*) FROM banking_data WHERE decision='Rejected';". I choose the Stat visualization type. The output shows, for example, 12 records rejected. I save the panel and name it “Rejected”.

Similarly, I create another panel with query "SELECT COUNT(*) FROM banking_data WHERE decision='Approved';". I again select Stat visualization. I save the panel and name it “Approved”.

Then I create a pie chart. I write the query "SELECT transaction_type, COUNT(*) FROM banking_data GROUP BY transaction_type LIMIT 50;". I select Pie Chart visualization. This shows counts of different transaction types. I set the panel title to “Authorization”.

Next, I create a bar chart. The query is "SELECT COUNT(id) AS blacklisted_account FROM banking_data WHERE blacklisted=TRUE GROUP BY account_id;". I select Bar Chart visualization. This shows blacklisted accounts.

I adjust the dashboard layout — move panels, resize them, etc. Finally, I save the dashboard with the name Rules Trigger Banking.

Later, I go back to the code, restart the kernel, and run it again. As new records are inserted, the Grafana dashboard updates live. For example, the count of rejected transactions goes from 12 to higher numbers as more are generated. Similarly, approved transactions, blacklisted accounts, and transaction type counts update in real time.

So the final setup is: PostgreSQL database in AWS RDS, fake data generated by Faker in Python, rules applied, records inserted, Grafana connected to Postgres, and dashboards created to visualize fraud detection rules live. (Rules applied for fraud detection, and Grafana dashboards for real-time monitoring)



**D) Getting Started with Dagshub**

**1. Creating First Remote Repo Using Dagshub**

To get started with DAGsHub, the first step is to go ahead and start for free. After clicking on Start for free, the platform will prompt for sign-up, and the available options are to sign up using GitHub or Google. Once an account is created, the user can proceed. If an account is already available, the next step is to click on Sign in. After entering the username and password, clicking on Sign in provides access to the dashboard.

DAGsHub is an amazing platform because it provides powerful remote repositories. This becomes particularly important when working in a collaborative way. After signing in, it is possible to see how many projects have been created, which may include work related to language model evaluation, MLflow, or data pipelines. The same approach can be followed to create new projects, data pipelines, and to use DVC to track data versions, along with many other functionalities.

Once logged in, a new repository can be created by clicking on Create a New Repository. To demonstrate the differences between DAGsHub and GitHub, GitHub can be opened in parallel for comparison. For example, in GitHub, a project such as network security may contain the entire codebase, with multiple commits such as pipeline is committed, trainer evaluation, and MLflow committed. DAGsHub functions similarly but offers additional integrated features.

After selecting Create a New Repository in DAGsHub, a new page is displayed with multiple options. The repository can be created as blank, from templates, or by connecting to an existing repository. DAGsHub provides options to connect to repositories from GitHub, GitLab, or Bitbucket. This enables integration with repositories already being used. For example, a GitHub repository can be directly connected to DAGsHub by simply clicking on Connect. However, instead of connecting to an existing repository or GitHub, the demonstration will proceed with creating a blank repository.

For the repository name, DVC demo data pipeline or demo DAGsHub can be chosen. Visibility can be set to public or private as preferred. Once the Create Repository button is clicked, the repository is created. The interface looks very similar to GitHub. For example, creating a new repository in GitHub, such as test DAGsHub, shows a similar page where the repository can be initialized and a Git URL is provided. In GitHub, the remote origin URL is something like github.com/.../test-DAGsHub.git, whereas in DAGsHub, the remote origin URL is under the DAGsHub domain.

### The key difference between GitHub and DAGsHub lies in the additional features DAGsHub provides. In DAGsHub, three main functionalities are supported. First, it allows uploading data to DAGsHub, enabling the tracking of data using DVC. This includes versioning of not only data but also models and other artifacts. Second, it allows leveraging Git versioning for code. Third, it provides the ability to log experiments using MLflow.

### In contrast, GitHub primarily supports version control for code, while DAGsHub extends this by also offering support for data versioning, model versioning, and experiment logging. DAGsHub provides up to 10 GB of free remote repository storage for uploading data, using an S3 bucket in the backend. It supports data, models, notebooks, DVC, and Git, all in one integrated environment. Additionally, it supports running MLflow tracking servers directly in DAGsHub, similar to how MLflow servers are run locally.

### There are also options to configure storage with S3 or Google Drive for additional capacity. The platform provides options to upload and version data using Git and DVC. In the next step, DVC will be used to demonstrate how to version data within the same repository.

### Other functionalities available in DAGsHub include Experiments, Models, and Collaboration. Collaborators can be invited to work together on the same repository. Annotation capabilities are also provided, which are especially useful for computer vision projects, where data sources can be annotated directly in the platform.

At this stage, the repository has been created in DAGsHub. To start coding, the repository must first be initialized with Git. The first example to be implemented will focus on uploading data to DAGsHub and ensuring that the data is versioned using DVC. Later steps will include tracking code and logging experiments with MLflow.

**2. DVC With Dagshub Remote Repository**

The discussion continues with respect to DAGs. The focus now is to demonstrate how DVC can be used along with DAGs Hub, which provides a powerful way to version, manage, and collaborate on data science and machine learning projects. DVC integrates Git and DVC together, enabling tracking of both code and data. Git tracks code, and DVC tracks data. Additionally, MLflow can be used to track experiments.

A repository has already been created. To start, a command prompt is opened, and navigation is done to the E drive. A folder named "MLOps" is created, and inside it, a folder named "DVC" is created. This DVC folder can be created manually or directly from the command prompt. Once inside this folder, the next step is to clone the repository.

After cloning, the system may show the message: "You appear to have cloned an empty repository." A folder such as "cd demo-hub" will appear, which will serve as the project directory. From here, VS Code can be opened using "code ." and then pressing Enter. Once opened, VS Code will display the project folder.

Inside the repository, a README file is created as an initial file to commit. The terminal is opened, navigation is done to the "demo-hub" repository, and a README file is created. To stage the file, the following command is used: "git add README.md"

After staging, the first commit is performed using: "git commit -m 'first commit'"

A branch named "main" is created, and the README file is pushed to the origin main using: "git branch -M main"; "git push -u origin main"

Reloading DAGs Hub will now show the README file, confirming that Git versioning is enabled for code.

The next step involves working with data. To do this, a virtual environment is created to install DVC and DAGs Hub. In the terminal, the environment is created using: "conda create -p venv python==3.10"

The -p venv ensures that the environment folder venv is created inside the project location. Once created, a requirements.txt file is added with the following libraries: "dvc; dagshub"

A .gitignore file is also created, inside which venv/ is added so that the environment folder is not tracked by Git.

The environment is then activated. In the command prompt, the activation command is: "conda activate venv/"

In Git Bash, the activation command is: "source activate venv/"

After activation, the requirements are installed using: "pip install -r requirements.txt"

A data folder is created, and inside it, a file named data.csv is placed. This dataset is a diabetes dataset with various parameters used to predict whether a person has diabetes.

Next, DVC is initialized using: "dvc init"

This creates a .dvc folder, .gitignore, and config files inside the project. To track data with DVC, the following command is used: "dvc add data/data.csv"

This creates a .dvc file for the dataset and updates .gitignore. To track these files with Git, the following commands are executed: "git add data/.gitignore data/data.csv.dvc"; "git commit -m 'added data.csv with DVC'"

### The next step is to configure DAGs Hub remote storage for data versioning. DAGs Hub provides an S3-like bucket for storing data. The configuration is done using:

"dvc remote add origin s3://<bucket-name>"

"dvc remote modify origin endpointurl https://dagshub.com/<user>/<repo>.dvc"

"dvc remote modify origin access_key_id <your-access-key>"

"dvc remote modify origin secret_access_key <your-secret-key>"

The list of remotes can be checked using: "dvc remote list"

To pull data from the remote repository, the following command is executed: "dvc pull -r origin"

If the error "requires dvc[s3]" occurs, update requirements.txt with dvc[s3] and reinstall dependencies: "pip install -r requirements.txt"

Now, data can be pushed to the remote using: "dvc push -r origin"

Finally, the Git repository is updated with: "git push origin main"

#### Reloading DAGs Hub will now show DVC and Git enabled, along with an automatic data pipeline visualization. The dataset (data.csv) will appear as a DVC-managed file.

To test versioning, the dataset is modified (for example, three rows are removed). The updated dataset is re-added to DVC: "dvc add data/data.csv"

The .dvc file changes with a new MD5 hash. Git is updated with: "git add ."; "git commit -m 'second commit'"; "dvc push -r origin"; "git push origin main"

DAGs Hub now shows two commits in the history, allowing comparisons between versions. The history shows the previous version and the modified version, along with different SHA values.

#### This confirms that both code and data are versioned using Git and DVC with DAGs Hub as the remote repository. The pipeline visualization also updates accordingly. This simple pipeline demonstrates the integration of DVC with DAGs Hub. More complex pipelines with experiments and MLflow can be added in future projects for complete end-to-end workflows.

#### **E) GitHub Action Practicals - Automate Testing Workflow With Python**

In this section, we will see the first practical implementation of the GitHub Action workflow. The goal is to create a Python project, and with the help of GitHub Actions, we will enable automated testing. Automated testing will be performed using unit test cases that we write. The steps required to accomplish this will be shown step by step.

The first step is to go to github.com. A new repository must be created. Let the new repository name be test-github-action. This repository will be created for a Python app. While creating the repository, no options such as README file or license need to be selected. After clicking create, the repository will be created and will be visible in the account.

Next, open Visual Studio Code. In VS Code, open the terminal and use the command prompt. Ensure that Git is installed so that repository initialization can begin. The first file to create will be the README.md file. This file will be created with the following content: This is the Python app

After this, the repository must be initialized. This is done using the command: git init

This initializes an empty Git repository in the current folder. A .git folder will now be available inside the repository. After initialization, the next step is to add the README.md file to the staging area. This is done with: git add .

The file is now in the index. Then commit the file: git commit -m "first commit"

Now a branch must be created, named main: git branch -M main

Next, add the remote origin for the repository: git remote add origin <repository-url>

Finally, push the changes to the remote repository: git push -u origin main

At this stage, the README.md file will appear in the GitHub repository.

**Now, continue in VS Code to start writing the Python application. The first file will be requirements.txt, which lists the dependencies. For this project, the dependencies will be: pandas, pytest**

### Pytest library is used for unit testing. It is capable of executing Python unit test cases.

### Next, create a src folder that will contain the application code. Inside this folder, add an __init__.py file so that the folder is recognized as a package. Then create a file named math_operations.py. In this file, define two functions for addition and subtraction:

def add(a, b):
    return a + b

def subtract(a, b):
    return a - b

## Next, create a tests folder for unit test cases. Inside this folder, add an __init__.py file and a file named test_operations.py. In test_operations.py, import the functions from math_operations:

## from src.math_operations import add, subtract

### Now, define the test cases. For addition and subtraction: 

def test_add():
    assert add(2, 3) == 5
    assert add(-1, 1) == 0

def test_subtract():
    assert subtract(5, 3) == 2
    assert subtract(4, 3) == 1
    assert subtract(3, 3) == 0
    assert subtract(2, 3) == -1

The test folder will be automatically discovered by pytest, and the test cases will be executed.

Once the application and tests are ready, commit the changes:

git add .

git commit -m "unit test cases updated"

git push origin main

At this point, the repository on GitHub will contain both src and tests folders.

### Now the workflow for automated testing using GitHub Actions will be created. Inside the repository, create a folder named .github. Inside this, create another folder named workflows. Within workflows, create a YAML file named unit-test.yml. The GitHub Action configuration is always defined in YAML files.

### A GitHub Actions extension can be installed in VS Code for convenience. After installing, sign in to GitHub if required. Now open the unit-test.yml file and define the workflow. A GitHub Action workflow is defined using key-value pairs.

## The first key is name, which specifies the workflow name. In this example: name: Python CI

## The next key is on, which specifies the events that will trigger the workflow. Workflows can be triggered on events like push, pull request, merge, or delete. Here, the workflow will trigger on push and pull request events on the main branch:

on:
  push:
    branches: [ "main" ]
  pull_request:
    branches: [ "main" ]

The next section is jobs. Multiple jobs can be defined. Each job runs in a container. In this case, the job will run in an ubuntu-latest container:

jobs:
  test:
    runs-on: ubuntu-latest
    steps:

### Runs on Ubuntu Containers - A Linux Container; (In code, based on container we want we can specify accordingly)

## The steps define what will happen inside the job.

(i) Checkout code: This uses the pre-built GitHub Action actions/checkout@v2 to fetch code from the repository.

- name: Check out code
  uses: actions/checkout@v2

### We defined Name, Event, Jobs; Basically we checkedout and take it to run on container; Job is that is running on some container

(ii) Set up Python environment: This uses the pre-built action actions/setup-python@v2. The version of Python is specified.

We mentioned keyword and Python version we want to create

- name: Set up Python
  uses: actions/setup-python@v2
  with:
    python-version: '3.8'

(iii) Install dependencies: This step installs required libraries from requirements.txt. (To test)

- name: Install dependencies
  run: |
    python -m pip install --upgrade pip
    pip install -r requirements.txt

(iv) Run tests: Finally, pytest is executed.

- name: Run tests
  run: pytest

## As soon as Run Test is executed in the container, it will start looking for test folder, wherever it is present and go ahead and execute the test cases

## This is one example of Continuous Integration

## Once the YAML file is committed and pushed, GitHub Actions will be automatically triggered. This happens because a push event to the main branch occurred.

## As soon as, code is pasted and commited in Github ".github/workflows/python-app.yaml", entire workflow should get triggered; When commiting it means that a Pull/Push Request is basically happening; Push request is basically commit the entire changes

## As soon as committed, it gets trigged; Once we go the "Actions", it shows a brown symbol, means test got executed

## Inside the GitHub repository, go to the Actions tab. The workflow will appear as triggered. The status will show steps such as Set up job, Check out code, Install dependencies, Run pytest, and Post job cleanup. If all test cases pass, the workflow will show success.

From the logs, each step can be examined. For example, in checkout, the repository is initialized. In set up Python, the environment is created with the specified version. In install dependencies, pandas and pytest are installed. Finally, in run tests, pytest discovers the test folder and executes the test cases. If all assertions pass, the result will show the test cases have passed.

From now on, every commit or pull request will trigger this GitHub Action automatically. This ensures continuous integration. Whenever a developer pushes new code, all unit tests will run automatically, and if a failure occurs, it will be visible immediately. This prevents broken code from being merged into the main branch.

This was a complete example of an end-to-end workflow for a Python application using GitHub Actions. As projects grow, more advanced workflows can be added, such as Docker integration, deployment pipelines, or multi-environment testing.
