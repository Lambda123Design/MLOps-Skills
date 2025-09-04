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

## Astronomer, Docker, Airflow, all are related (Astronomer is a managed platform for Apache Airflow; Airflow will be running within a Docker container) - So now I'm quite excited to start the practical implementation of Airflow. Uh, before I go ahead, you know, I really want to introduce you to this amazing platform which is called as Astronomer. And we also see it as Astro. Uh, what exactly is Astro or Astronomer? It is a managed platform for Apache Airflow. So here you can see Airflow is there. That simplifies running and scaling Airflow while providing additional enterprise features like monitoring, security and automation. Okay, so this entire platform we are going to specifically use, and the best thing will be that this platform will be running your r. So for this you definitely need to have a Docker installed or Docker installed in your, uh, laptop or your desktop. And then only you will be able to use this, okay. Because at the end of the day, when we are creating all our end to end projects, uh, specifically using Airflow, whatever task we are going to define, all these tasks, um, we are going to write it down, and we are also going to use other services which will be specifically running in Docker container. And we'll be making sure that using Docker Compose we’ll make them interact with one another.

**A) Getting Started with MLFlow Tracking Server**

**B) MLFlow with AWS**

**C) Grafana - Open Source Tool for Data Visualization and Monitoring**

**D) Getting Started with Dagshub**

**E) GitHub Action Practicals - Automate Testing Workflow With Python**

**F) Setting Up Airflow With Astro**

**G) Building Your First DAG With Airflow**

**H) Designing Mathematical Calculation DAG With Airflow**

**I) Getting Started With TaskFlow API Using Apache Airflow**

**J) End-to-End Github Action Workflow Project with DockerHub**


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


## **F) Setting Up Airflow With Astro**

So now I'm quite excited to start the practical implementation of Airflow. Uh, before I go ahead, you know, I really want to introduce you to this amazing platform which is called as Astronomer. And we also see it as Astro. Uh, what exactly is Astro or Astronomer? It is a managed platform for Apache Airflow. So here you can see Airflow is there. That simplifies running and scaling Airflow while providing additional enterprise features like monitoring, security and automation.

Okay, so this entire platform we are going to specifically use, and the best thing will be that this platform will be running your Airflow within a Docker container. So for this you definitely need to have a Docker installed or Docker installed in your, uh, laptop or your desktop. And then only you will be able to use this, okay. Because at the end of the day, when we are creating all our end to end projects, uh, specifically using Airflow, whatever task we are going to define, all these tasks, um, we are going to write it down, and we are also going to use other services which will be specifically running in Docker container. And we'll be making sure that using Docker Compose we’ll make them interact with one another.

Right. So in this video I'll be talking more about Astronomer and how we can probably go ahead and set up the Airflow with Astro. Okay. So if you just go ahead and search for astronomy documentation with Airflow, so here you also get an amazing, uh, entire documentation how you can probably get started. And trust me, you know, before I used to use Airflow independently to try I used to try to run it as a Docker container. A lot of errors and issues I used to face because there is a lot of dependencies issues. But with the help of this particular platform, it has become really, really easy.

Now let me just go ahead and talk more about this. Astro, as I said that it is a managed platform for the entire Apache Airflow and everything is basically running in a Docker container. Now to get started, what I will do, I will just go to my folder. Let me just open my folder. That is MLOps. Okay. Now inside this, I have this, uh, airflow. Astro. I've created this particular folder. You can also create the folder anywhere you want. Okay, I will copy this and I will open my command prompt. Okay. Once I open my command prompt, I will just go ahead and, uh, go to my E drive, okay. And I will say CD and I'll specifically go to this particular location that is the airflow Astro. Okay. Once I go to this particular location, then I'm going to go ahead and, uh, probably create my project inside this.

So I will go ahead and write "code ." Okay. Once I write "code ." so here you will be able to see that my VS Code has got opened. Now since we are getting started, uh, with setting up the, uh, Airflow with Astro, uh, this is the step that everybody needs to follow. And then probably we'll also see that how we can run this entire Airflow. Okay. And, uh, right now here, let me just go ahead and open my terminal. Okay. And here I'm going to open my command prompt. Or you can also work with Git Bash. Okay.

So once you go over here, the first command. See, right now I don't have any project structure. Nothing as such. Right. And I really want to go ahead and start with a project structure. 

Also probably I need to define a project structure. I need to probably create all the files and all. Now with the help of this Astro, right, it becomes very easy to probably create this entire project structure. And for the Airflow, the kind of project structure that is required automatically will be created by this. 

## Now, in order to do that, just go ahead and write this particular command "astro dev init".

So once you basically write this automatically, it will initialize an Astro project, uh, pulling the Airflow development files from Astro runtime 12.1.1 okay. And it is going to initialize an empty Astro project in this particular drive. 

### Now, if I just go ahead and open it here, you can see the entire project structure is basically created. Right. And here you have this .astro file. Here you have this DAGs folder right. DAGs folder is specifically for Airflow. Right. And if you probably see over here a Docker file is also created. So this is the Docker file that will be, uh, you know, when once we probably run this entire code, right. Once we run this entire project, this is the Docker that is basically going to run in the Docker container. And this internally also calls Airflow. And it will be running in one, one, one another port itself. Okay.

So all those things we'll see how we can actually run it. But I think you found this particular step very much easy because just by writing one line of command, the entire project structure is ready. Okay. Now we'll keep this project structure like this itself. And then we will start working in different different folders. 

### Now let me talk about one of the very important folder which is called as DAGs. And this inside this particular folder we basically create all our DAGs. So let's take this example which is called as example dag.py. And here, uh, this particular example is a default example that is given by Astro. Here they are saying that hey we have astronaut ETL example dag.

### So this is an ETL pipeline example wherein we are reading something. Okay so here is my DAGs that is basically created. Then here you can see I have defined my task. We will go step by step will try to understand it. This is hitting an API. It is bringing all the details and it is returning the list of people in the space. Okay, along with this, you'll be able to see that there is another task which is basically called a sprint. 

## So two important information why we are seeing this as ETL because one, it is trying to get all the astronauts from the API right. ETL components, if you remember from my diagram.

So if you probably see from the top diagram that we have actually discussed, right. Let me just go to that particular diagram. And then you should be able to understand what I am exactly talking about. Right. So if I go to my full screen, if you see over here in the data pipeline, right, we create an ETL pipeline itself in ETL basically means extraction, data extraction, transformation and loading. Right. 

### So similarly here also what it is doing, it is probably getting the astronauts detail from an API, which is this specific API. After getting all the information, it is returning the list of people in the space. And finally we have created another task which is printing all the names. Okay, so this two specific task has been scheduled. And whenever this API has new data, it should be able to we should be able to schedule it regularly.

So yet I have not discussed about the coding part and all. Don't worry because from the next video onwards we will go ahead and start from basics, will create projects, multiple projects and I'll run it. I'll probably write it line by line and show it to you. Okay, now, uh, let's run this entire code. As I said that there are two important modules or two important tasks in this particular DAG. So let's run this in order to run it. Just go ahead and open terminal. Okay. Now inside my command prompt, what I will do. First of all just see in Docker nothing should be running. So right now my Docker is not running any services over here.

So here I will go ahead and write Astro in order to run it. Okay. "astro dev start". Right. So as soon as we go ahead and write this particular command "astro dev start", my entire execution will basically start. So initially you can see it is going to build each and every thing over here. It is building this particular Docker file and from that it is calling this coi.io astronomer Astro runtime 12.12. And after that it is just going to run each and every thing in the Docker itself, right. So using Docker. So here you can see this is basically getting created. Now your Airflow is basically getting started up.

### Now if I open my Docker. So it will take some time to run for the first time. Here you can see my four new containers has got started. So one of the container is about the web server which is running over here. By default a Postgres is scheduled over here that is also running. So if you probably go ahead and see now see this as soon as it runs, this entire Airflow has got started. Okay. And it is running in your 8080. If this is not automatically opening what you can do, you can go to your Docker over here. You can see where the web server is running. It is running in 8080. You can also go ahead and click over here and it will say open with browser.

Now as soon as you open this is the Airflow UI right. Completely managed by Astro okay. And this entirely is running in the Docker container. Okay. So here I will go ahead and write my by default username and password will be "admin admin". Okay. So just go ahead and write "admin admin". This is also set up. I will show you where exactly it is set up and all and how you can actually see all these things, how you can change it. Also, I will go ahead and click on Sign in. Now here is my DAG. Now see this. This is my DAG that has got created that is called as example astronauts okay.

### Tasks in DAG - And right now it is disabled because we have not enabled. And if I talk about this particular DAG, if I just go inside this just double click this. So here you will be able to see that I have two important tasks. One is get astronaut and the other one is print astronaut. Okay. And if I really want to see this in the form of graph. So here is what you will be able to see. Here you have guest astronaut and here you have print astronaut okay. And this is my data set or API which we are actually focusing on. So from here my data will be picked and then this will get executed.

### Two things are - get astronauts, print astronauts

Now in order to run this there is something called as a trigger DAG over here okay. And here we can probably go ahead and trigger the schedule. You can see it is daily. And this is basically the time where it basically has to run. Right. So here, uh, 2020 for ten to, uh, from this particular date it has started. And at this particular time it needs to probably run this entire DAG. But if you really want to manually trigger it, just go ahead and click on this. As soon as you click on this, so here you can see this both the task is now running. Now you are getting green signal. And with respect to this everything is basically also getting displayed.

Now, if I go to the graphs here, you can see if it is showing us green signal. That basically means it is running in an amazing way, like it is running correctly. And we are also able to get the results. In order to see the results, all you have to do is that let's say I will go over here in the Get astronaut. 

## If I click over here, here you will also be able to see the event log right. So event log displays some information. Then if you want to see the code. Code also is basically getting displayed. But, uh, since I want to probably go ahead and show each and everything.

### So let me do one thing. Okay. So, uh, here what I will do, I will go to my example astronaut. So this example astronauts I'm seeing. And here you can see my code. Here there is something called as event log okay. Now in the event log all the necessary information is basically displayed. Print astronaut which all things are basically there and all are are available. All these logs are also visible to you okay. Any errors you will also be able to see that okay. Once you see this okay let me do one thing. Let me just reload. Let me go to the DAGs and open one of my DAG itself over here.

So, uh, inside this, uh, here you are able to see that. Okay, I'm able to see graph. I'm able to see, uh, Gant, uh, code event log, run duration, task duration. Right. Uh, calendar. Right. When all things this. This needs to be getting executed. Now, if I go to the graph, if I go ahead and click on Print astronaut. Okay. Print print astronaut or let me just go and click over here and see this print astronaut okay. So here, uh, if you go ahead and click on Event Logs here, all the information is basically getting displayed. And, uh, if I go and see the details here also you'll be able to see that what task or what run ID it has got executed. Uh, right now we are not printing much more details. So that is the reason you're not able to see the complete logs.

But, uh, in the upcoming videos, I will show you multiple ways to probably see this logs also, so that you'll be able to see each and everything and how it is basically getting displayed right. So this is way like how tasks are getting executed and it is getting executed in a successful way. Okay. And here are some of the details that you are able to see from left to right. Okay. All the all the all the types of graphs and all or what task is basically created when everything you'll be able to see, see, as soon as I go ahead and click on Get Astronauts, if you go ahead and see there is something called as logs, right?

So here also you can see that we are printing some information. Right. Craft is name and all how to do this and all. I will talk about it when we are discussing about it right. So every stage what is basically happening all the information is also basically getting displayed. 

### There is also a component which is called as Xcom. Xcom basically talks about like what information is basically passing from one task to the other task. Now in this particular case, you can see number of people in space is basically getting passed. If I go ahead and click away, if I go ahead and click over here, other information over here, nothing is getting passed. So that is null over here.

But if I go ahead and click over here and if I go ahead and click over here, all this information is basically getting passed to this print astronaut craft function or task. Right. So this was just a basic example to show you that how you can go ahead and set up the basic Airflow project along with the Astro. And here I did not even write a single line of code, but I hope it is able to make you understand that how to run this right now. In order to stop this, I will just go ahead and write "astro dev stop". As soon as I do this, you will be able to see my entire Docker container will get stopped and my entire application will also get stopped.

## Now in the upcoming examples, what I'm actually going to do is that I'll show you some basic examples, how you can go ahead and start your DAG project, and how you can go ahead and start writing each and everything. Okay. Uh, I will be talking about how you can create tasks, how you can probably work with logs, how you can probably work with Eskom and do multiple things. Right. All those things will basically be discussed about it. Okay. And if I also show you this project structure. The project structure looks like you have a DAGs folder. You have include folder, you have plugins folder. You have test folder right here. Obviously you need to write the test cases.

This is very much clear. So this is my test cases that is written by default. But don't worry we will modify each and every file environment variable any environment variable you want to use. You can go ahead and use it. Airflow setting by default. If you want to. Probably go ahead and write any connections over here. So here you will be able to set it up okay. We'll discuss more about it. Then you have this requirement.txt. If you want to install any libraries, um, then you can probably go ahead and write it over here. And this is my README.md file where you'll be able to see all the information.

So I hope you like this particular video. Uh, this was it. Now in the upcoming video, I'm going to probably start everything from basics, and we'll try to do the coding and we’ll create task. We'll see what that Eskom is, how to create logs, how to probably go ahead and create a new DAG. Everything will discuss about it. Right. So yes, this was it from my side. I'll see you all in the next video. Thank.

### Summary:

🔹 Components

Astronomer (Astro): A managed platform for Apache Airflow that simplifies running, scaling, monitoring, and securing Airflow.

Docker: Required since Astronomer runs Airflow within Docker containers.

Docker Compose: Used to enable multiple services (e.g., Airflow webserver, scheduler, database) to interact.

Project Structure (auto-created by astro dev init):

.astro → Astro project config.

dags/ → Folder for DAGs.

Dockerfile → Image definition for running Airflow.

include/ → For additional files.

plugins/ → For Airflow plugins.

tests/ → For test cases.

requirements.txt → For extra Python dependencies.

README.md → Project info.

Airflow UI (localhost:8080): Web interface for managing DAGs.

XCom: Mechanism for passing information between tasks.

🔹 Important Astronomer Commands

Initialize project:

astro dev init


→ Creates the Astro project structure with DAGs, Dockerfile, configs.

Start Airflow:

astro dev start


→ Builds Docker image, runs Airflow containers (webserver, scheduler, Postgres, triggerer).

Stop Airflow:

astro dev stop


→ Stops all running Airflow containers.

🔹 Example DAG (default)

example_dag.py provided in dags/.

Demonstrates an ETL workflow:

Task 1 – Get Astronauts → Fetch astronauts from API.

Task 2 – Print Astronauts → Print list of astronauts.

🔹 Steps to Set Up and Run Airflow with Astro

Install Docker (prerequisite).

Create project folder (e.g., airflow-astro).

Open terminal / VS Code and navigate to folder.

Initialize project → astro dev init.

Inspect structure → dags/, Dockerfile, .astro, etc.

Start Airflow → astro dev start.

Containers for webserver, scheduler, Postgres created.

Airflow UI accessible at http://localhost:8080.

Default credentials: admin / admin.

Check DAGs in UI → example_astronauts.

View tasks (get_astronauts, print_astronauts).

View Graph, Gantt, Logs, Code, XCom, etc.

Trigger DAG manually or let it follow its schedule.

Monitor logs & XComs for task details.

Stop Airflow → astro dev stop.

### **G) Building Your First DAG With Airflow**

So in this tutorial what we are going to do is just look at one good example. And this example is going to give you a very clear idea of how you can get started with Airflow with respect to a practical implementation. Now, in the previous part you might have already seen the example_dag.py file. I am not going to write any code in that same file. Instead, what I’ll do is go inside my dags folder and create a new Python file. Let’s say the file name will be ml_pipeline.py. This file will be my new DAG definition where I will create my DAG, my tasks, and set up the dependencies.

Now, as I said, I want to create a basic ML pipeline here. I won’t go deep into writing actual machine learning logic, because that’s not the focus right now. Instead, I want to show you the skeleton of how you can create tasks, how you can create your DAG, and how you can run it in Airflow.

So first of all, I’ll start by importing the necessary libraries.

from airflow import DAG
from airflow.operators.python import PythonOperator
from datetime import datetime


Here, from Airflow I am importing DAG, because that’s the class we need to actually define a Directed Acyclic Graph. Then I am importing PythonOperator from airflow.operators.python. Now, why do we need PythonOperator? Basically, whenever you want to create a task in Airflow that just runs a Python function, you use this operator. That’s why it’s called PythonOperator. Later, we’ll also see many other operators like BashOperator, EmailOperator, and so on, but for now let’s just stick to Python because that’s the simplest way to demonstrate. And finally, I am importing datetime because we need it for the scheduling and start date of the DAG.

Once we have the imports ready, the next step is to actually define our task functions. Because at the end of the day, when you create a DAG, it contains multiple tasks. These tasks are connected in a certain order, forming a workflow. So let’s go ahead and define three simple tasks.

def preprocess_data():
    print("Pre-processing data...")

def train_model():
    print("Training model...")

def evaluate_model():
    print("Evaluating model...")


Right now, I am not adding any complex logic inside these functions. I am just putting a print statement, because I want to demonstrate how the flow works. Later, in more advanced tutorials, we can actually put real preprocessing code, training logic, or evaluation logic here. But for now this will be enough.

Now that we have our task functions, the next step is to define the DAG. To define a DAG, we use the with DAG(...) as dag: context manager. Let’s write that out.

with DAG(
    dag_id="ml_pipeline",
    start_date=datetime(2024, 1, 1),
    schedule_interval="@weekly",
    catchup=False
) as dag:


So here I am creating a DAG with the ID ml_pipeline. The start_date is January 1st, 2024. Then I set the schedule_interval to @weekly, which means the pipeline will run once a week. You could also use values like @daily, @hourly, or even cron expressions depending on your use case. Finally, I set catchup=False which means Airflow will not try to backfill all the runs between the start date and today. That’s a good setting when you are testing things.

Now inside this DAG block, I will define my tasks using the PythonOperator. Let’s start with the preprocessing task.
    preprocess = PythonOperator(
        task_id="preprocess_task",
        python_callable=preprocess_data
    )
    
Notice here that I gave the task an ID called preprocess_task. Task IDs should always be unique inside a DAG. Then I set the python_callable to the function we defined earlier, preprocess_data. Also notice that we do not write parentheses here — we don’t call the function directly. We just pass the function reference, because the operator will take care of calling it when the task is executed.

Now let’s define the training task.
    train = PythonOperator(
        task_id="train_task",
        python_callable=train_model
    )


Again, we give it a unique task ID train_task and point the python_callable to the train_model function.

And finally, the evaluation task.
    evaluate = PythonOperator(
        task_id="evaluate_task",
        python_callable=evaluate_model
    )


So now we have three tasks defined — preprocess, train, and evaluate.

The next important thing is to define the dependencies. This is how we tell Airflow in which order these tasks should run. For our ML pipeline, the natural order is preprocessing → training → evaluation. And in Airflow, we can write that very simply like this:
    preprocess >> train >> evaluate


This means first the preprocess task will run, then the train task will run, and finally the evaluate task will run. If any task fails, the downstream ones won’t run until the issue is fixed.

At this point, we have a complete DAG defined. Let me show you the full code in one place.

from airflow import DAG
from airflow.operators.python import PythonOperator
from datetime import datetime

def preprocess_data():
    print("Pre-processing data...")

def train_model():
    print("Training model...")

def evaluate_model():
    print("Evaluating model...")

with DAG(
    dag_id="ml_pipeline",
    start_date=datetime(2024, 1, 1),
    schedule_interval="@weekly",
    catchup=False
) as dag:
    preprocess = PythonOperator(
        task_id="preprocess_task",
        python_callable=preprocess_data
    )
    train = PythonOperator(
        task_id="train_task",
        python_callable=train_model
    )
    evaluate = PythonOperator(
        task_id="evaluate_task",
        python_callable=evaluate_model
    )
    preprocess >> train >> evaluate


Now once you have written this file, save it inside your dags folder. The moment Airflow starts up, it will automatically detect this DAG. To actually run Airflow, you can go to your terminal and simply start it with:

astro dev start


This will bring up your Docker containers and Airflow webserver. Once everything is running, you can open your browser and go to localhost:8080. That’s your Airflow UI. Log in with admin and admin if you are using the default Astro setup. And there you will see two DAGs: the default example_dag and the new ml_pipeline that we just created.

If you click on the ml_pipeline DAG, you will see three tasks: preprocess_task, train_task, and evaluate_task. If you go to the graph view, you will notice the arrows show the exact order — first preprocessing, then training, and then evaluation.

Now if you trigger the DAG manually, you can actually see each task getting executed. For example, after running the preprocess_task, you can click on it and view the logs. In the logs you will see the message “Pre-processing data...” printed. Similarly, when the train_task runs, you will see “Training model...” in the logs. And for evaluate_task, you will see “Evaluating model...”.

This confirms that our Python functions were indeed executed by Airflow. The graph will also turn green for successful tasks, so visually you can track the progress.

And just to mention — if at any point you want to stop your Airflow containers, you can go back to the terminal and type:

astro dev stop


This will stop all the containers. If you want to restart them after making code changes, you can use:

astro dev restart


That way Airflow will reload and pick up your changes.

So this was a very basic example of creating an ML pipeline DAG. In the next tutorials, we’ll start putting more logic inside these functions, explore passing data between tasks using XComs, and even integrate with external systems like databases. But this foundation — defining a DAG, creating tasks with PythonOperator, and setting dependencies — is the core of how every workflow in Airflow is built.


#### Summary:

Components Used

DAG (Directed Acyclic Graph) → Defines the workflow.

PythonOperator → Runs Python functions as tasks.

datetime → Used for scheduling (start date).

Tasks Defined:

preprocess_data() → Pre-processing step.

train_model() → Training step.

evaluate_model() → Evaluation step.

🔹 DAG Definition
with DAG(
    dag_id="ml_pipeline",
    start_date=datetime(2024, 1, 1),
    schedule_interval="@weekly",
    catchup=False
) as dag:


dag_id = "ml_pipeline"

start_date = 2024-01-01

schedule_interval = "@weekly" (runs once a week).

catchup=False → Prevents backfilling past runs.

🔹 Tasks Setup (PythonOperator)
preprocess = PythonOperator(
    task_id="preprocess_task",
    python_callable=preprocess_data
)

train = PythonOperator(
    task_id="train_task",
    python_callable=train_model
)

evaluate = PythonOperator(
    task_id="evaluate_task",
    python_callable=evaluate_model
)


Each task has a unique task_id.

python_callable points to the defined Python function.

🔹 Dependencies
preprocess >> train >> evaluate


Execution order: Preprocessing → Training → Evaluation.

If one task fails, downstream tasks won’t run.

🔹 Full DAG File → dags/ml_pipeline.py

Contains imports, task functions, DAG definition, operators, and dependencies.

Saved in dags/ folder so Airflow can auto-detect it.

🔹 Running the Pipeline

Start Airflow:

astro dev start


→ Brings up Docker containers (Airflow webserver, scheduler, Postgres).

Access UI:

Open: http://localhost:8080

Login: admin / admin (default).

View DAGs:

example_dag (default).

ml_pipeline (new DAG).

Inside ml_pipeline DAG → see tasks:

preprocess_task → Logs: “Pre-processing data...”

train_task → Logs: “Training model...”

evaluate_task → Logs: “Evaluating model...”

Graph view shows arrows → Preprocess → Train → Evaluate.

Successful runs show green tasks in UI.

🔹 Managing Airflow

Stop containers:

astro dev stop


Restart (reload code changes):

astro dev restart

## **H) Designing Mathematical Calculation DAG With Airflow**

So now let us continue our discussion with respect to Airflow. In this example, I am going to show you how we can build a DAG that performs a sequence of mathematical operations, where each operation is dependent on the previous one. Along the way, I’ll also introduce you to a very important concept in Airflow called XComs. Now, what exactly is XCom? XCom stands for “Cross Communication.” It is the mechanism provided by Airflow to allow one task to share data with another task. You will see how that becomes very handy when tasks are chained together like in our case.

So let’s get started. Inside my dags folder, I will go ahead and create a new Python file called maths_operation.py. This will be our DAG file. Now in this file, I want to define a very simple workflow — but it’s a good example to show you how data can move between tasks. Let me just outline what we are going to do.

We will start with an initial number, let’s say 10. Then we will add 5 to the number. After that, we will multiply the result by 2. Next, we will subtract 3 from the result. And finally, we will compute the square of the number. Of course, this example looks very simple — you might be thinking why should we even create a DAG for this. But trust me, this is just to demonstrate the mechanics of Airflow: how we define multiple tasks, how they depend on each other, and how they pass values using XComs. Later, when we move to bigger projects, you’ll see these same concepts apply to things like data ingestion, preprocessing, training ML models, etc.

Alright, so let’s go ahead and start coding. First, we will import the necessary libraries.

from airflow import DAG
from airflow.operators.python import PythonOperator
from datetime import datetime


Just like in the previous tutorial, we are importing DAG to create our workflow, PythonOperator because all our tasks will be simple Python functions, and datetime to set the start date for the DAG.

Now let’s define our task functions one by one. The first task is to start with the number 10. So I’ll create a function like this:

def start_number(**context):
    value = 10
    context['ti'].xcom_push(key='current_value', value=value)
    print(f"Starting number is {value}")


Here, you’ll notice a couple of things. First, I am accepting a parameter called context. When you set provide_context=True in a PythonOperator, Airflow automatically provides information about the task execution, and one of the most useful things inside context is ti, which stands for Task Instance. Using ti.xcom_push(), I can push data into XCom. So in this case, I am pushing a key called current_value with the value 10. This means that any downstream task can later pull this value.

Now the next task is to add 5 to this number. Let’s define that.

def add_five(**context):
    current_value = context['ti'].xcom_pull(key='current_value', task_ids='start_task')
    new_value = current_value + 5
    context['ti'].xcom_push(key='current_value', value=new_value)
    print(f"{current_value} + 5 = {new_value}")


So here I am pulling the value that was pushed by the start_task. Notice the task_ids='start_task' — that is the ID of the previous task. Once I pull the current value, I add 5 to it, push the updated value back to XCom with the same key, and also print the result.

Next, we’ll multiply the result by 2.

def multiply_by_two(**context):
    current_value = context['ti'].xcom_pull(key='current_value', task_ids='add_five_task')
    new_value = current_value * 2
    context['ti'].xcom_push(key='current_value', value=new_value)
    print(f"{current_value} * 2 = {new_value}")


Again, the logic is exactly the same: pull the value from the previous task (add_five_task), perform the multiplication, push the updated value, and print it.

Then we’ll subtract 3.

def subtract_three(**context):
    current_value = context['ti'].xcom_pull(key='current_value', task_ids='multiply_by_two_task')
    new_value = current_value - 3
    context['ti'].xcom_push(key='current_value', value=new_value)
    print(f"{current_value} - 3 = {new_value}")


And finally, we will compute the square of the result.

def square_number(**context):
    current_value = context['ti'].xcom_pull(key='current_value', task_ids='subtract_three_task')
    new_value = current_value ** 2
    print(f"{current_value}^2 = {new_value}")


Here, I didn’t push the final result back into XCom, but you could if you want. For now, printing is enough to verify the output.

Okay, now that we have defined all the task functions, let us define the DAG.

with DAG(
    dag_id="maths_sequence_dag",
    start_date=datetime(2023, 1, 1),
    schedule_interval="@once",
    catchup=False
) as dag:


So I gave the DAG an ID called maths_sequence_dag. The start date is January 1st, 2023. The schedule interval is @once, which means this DAG will run only when I trigger it manually. And catchup is set to False.

Inside this DAG block, we now define each of our tasks using PythonOperator.
    start_task = PythonOperator(
        task_id="start_task",
        python_callable=start_number,
        provide_context=True
    )
    add_five_task = PythonOperator(
        task_id="add_five_task",
        python_callable=add_five,
        provide_context=True
    )
    multiply_by_two_task = PythonOperator(
        task_id="multiply_by_two_task",
        python_callable=multiply_by_two,
        provide_context=True
    )
    subtract_three_task = PythonOperator(
        task_id="subtract_three_task",
        python_callable=subtract_three,
        provide_context=True
    )
    square_task = PythonOperator(
        task_id="square_task",
        python_callable=square_number,
        provide_context=True
    )


Notice that in each operator I am setting provide_context=True. That is what allows the function to receive the context dictionary we used to push and pull XCom values.

Now finally, we define the dependencies.
    start_task >> add_five_task >> multiply_by_two_task >> subtract_three_task >> square_task


So the order is very clear: start → add five → multiply by two → subtract three → square.

At this point, our DAG is ready. Save the file inside the dags folder. Now to run it, go to your terminal and start Airflow with:

astro dev start


This will start up your containers. Once the scheduler and webserver are running, open your browser and go to localhost:8080. Log in with the default credentials. You will see the new DAG maths_sequence_dag listed there.

Now when you trigger the DAG and go to the graph view, you’ll see the exact pipeline we created. Each task is a node, connected in order. When the DAG runs, you can click on each task and view the logs. For example, in the start_task logs, you’ll see the starting number is 10. In the add_five_task, you’ll see 10 + 5 = 15. In the multiply_by_two_task, you’ll see 15 * 2 = 30. Then in the subtract_three_task, you’ll see 30 - 3 = 27. And finally in the square_task, you’ll see 27^2 = 729.

If you check the XCom tab for each task, you’ll also notice how the values were being passed along. First XCom had 10, then 15, then 30, then 27. So you can see clearly how Airflow lets tasks communicate and pass data step by step.

And that is the complete example. A very simple mathematical workflow, but it introduced you to XComs and how to use them in your DAGs. In the next part, I’ll show you a newer and easier way to define tasks using the TaskFlow API with decorators like @task. But for now, try running this DAG, explore the logs and XCom values, and get comfortable with how data flows between tasks in Airflow.

#### Summary:

Key Concept: XCom (Cross Communication)

Mechanism for tasks to share data in Airflow.

Uses:

xcom_push(key, value) → Push value into XCom.

xcom_pull(key, task_ids) → Retrieve value from another task.

Enables data flow between tasks.

🔹 DAG File → dags/maths_operation.py
Imports
from airflow import DAG
from airflow.operators.python import PythonOperator
from datetime import datetime

🔹 Task Functions

Start with 10

def start_number(**context):
    value = 10
    context['ti'].xcom_push(key='current_value', value=value)
    print(f"Starting number is {value}")


Add 5

def add_five(**context):
    current_value = context['ti'].xcom_pull(key='current_value', task_ids='start_task')
    new_value = current_value + 5
    context['ti'].xcom_push(key='current_value', value=new_value)
    print(f"{current_value} + 5 = {new_value}")


Multiply by 2

def multiply_by_two(**context):
    current_value = context['ti'].xcom_pull(key='current_value', task_ids='add_five_task')
    new_value = current_value * 2
    context['ti'].xcom_push(key='current_value', value=new_value)
    print(f"{current_value} * 2 = {new_value}")


Subtract 3

def subtract_three(**context):
    current_value = context['ti'].xcom_pull(key='current_value', task_ids='multiply_by_two_task')
    new_value = current_value - 3
    context['ti'].xcom_push(key='current_value', value=new_value)
    print(f"{current_value} - 3 = {new_value}")


Square the number

def square_number(**context):
    current_value = context['ti'].xcom_pull(key='current_value', task_ids='subtract_three_task')
    new_value = current_value ** 2
    print(f"{current_value}^2 = {new_value}")

🔹 DAG Definition
with DAG(
    dag_id="maths_sequence_dag",
    start_date=datetime(2023, 1, 1),
    schedule_interval="@once",
    catchup=False
) as dag:


dag_id = "maths_sequence_dag"

start_date = 2023-01-01

schedule_interval = "@once" → Runs only when manually triggered.

catchup=False → No backfilling.

🔹 Tasks Setup (with XCom context)
start_task = PythonOperator(
    task_id="start_task",
    python_callable=start_number,
    provide_context=True
)
# Similar for add_five_task, multiply_by_two_task, subtract_three_task, square_task


Each task has provide_context=True → makes context available for XCom push/pull.

🔹 Dependencies
start_task >> add_five_task >> multiply_by_two_task >> subtract_three_task >> square_task


Execution order:
Start (10) → Add Five (15) → Multiply (30) → Subtract (27) → Square (729)

🔹 Running the DAG

Start Airflow:

astro dev start


Open UI: http://localhost:8080 → login admin/admin.

See new DAG → maths_sequence_dag.

Trigger DAG manually.

🔹 Monitoring Results

Graph view → tasks connected in sequence.

Logs:

Start: Starting number is 10

Add: 10 + 5 = 15

Multiply: 15 * 2 = 30

Subtract: 30 - 3 = 27

Square: 27^2 = 729

XCom tab → shows values passed: 10 → 15 → 30 → 27.

This example introduces XComs for passing data between tasks.

Next step: TaskFlow API (with @task decorator) → makes this simpler without manually handling xcom_push / xcom_pull.

**I) Getting Started With TaskFlow API Using Apache Airflow**

So let us continue our discussion on Airflow. In the last example, we learned how to build a DAG using the traditional method with the PythonOperator, where each task was defined as a function and we had to use XComs to pass values between them. That worked fine, but it required a bit of boilerplate — we had to explicitly push and pull values with XCom, define operators for each task, and then set up dependencies.

Now, Airflow provides us with something much cleaner and more intuitive: the TaskFlow API. This feature was introduced in Airflow 2.0, and it allows us to define tasks simply by using Python decorators. The best part is that you don’t need to manually manage XComs anymore. When you use TaskFlow, values that are returned from one task are automatically available to the next task — no explicit push and pull needed.

Let’s see how this works in practice.

Step 1: Create a new DAG file

Inside your dags folder, go ahead and create a new Python file:

taskflow_api.py


This is where we’ll define our DAG using the TaskFlow API.

Step 2: Import required libraries

We’ll start by importing the necessary modules.

from airflow import DAG
from airflow.decorators import task
from datetime import datetime


Notice the difference here: instead of importing PythonOperator, we are importing task from airflow.decorators. This decorator is the key to using the TaskFlow API.

Step 3: Define the DAG

We’ll create a DAG very similar to our earlier math sequence example, but this time using TaskFlow.

with DAG(
    dag_id="maths_sequence_taskflow",
    start_date=datetime(2023, 1, 1),
    schedule_interval="@once",
    catchup=False
) as dag:


This DAG will run once when triggered manually. We’ve given it the ID maths_sequence_taskflow.

Step 4: Define tasks with TaskFlow API

Now instead of writing functions outside and then wrapping them with PythonOperator, we can directly define tasks inside the DAG using the @task decorator.

Let’s start with the first task, which initializes the number:
    @task
    def start_number():
        initial_value = 10
        print(f"Starting number is {initial_value}")
        return initial_value


Notice how simple this is. We just write a Python function, decorate it with @task, and return a value. That return value will automatically be available to the next task.

Next, let’s add 5 to the number:
    @task
    def add_five(number):
        new_value = number + 5
        print(f"{number} + 5 = {new_value}")
        return new_value


Here, the function takes number as an input. That will be provided by the output of the previous task. No need for manual XCom pulls.

Now, let’s multiply the result by 2:
    @task
    def multiply_by_two(number):
        new_value = number * 2
        print(f"{number} * 2 = {new_value}")
        return new_value


Then subtract 3:
    @task
    def subtract_three(number):
        new_value = number - 3
        print(f"{number} - 3 = {new_value}")
        return new_value


And finally, compute the square:
    @task
    def square_number(number):
        new_value = number ** 2
        print(f"{number}^2 = {new_value}")
        return new_value

Step 5: Set up task dependencies

In the traditional method, we had to chain tasks with >>. But with TaskFlow, dependencies are handled by simply calling functions in sequence and passing their outputs to the next task.
    start_val = start_number()
    added_val = add_five(start_val)
    multiplied_val = multiply_by_two(added_val)
    subtracted_val = subtract_three(multiplied_val)
    squared_val = square_number(subtracted_val)


This code looks just like normal Python function calls. But behind the scenes, Airflow converts these into tasks, builds the DAG structure, and automatically passes data between them using XCom.

Step 6: Run the DAG

Now save the file and start Airflow as usual with:

astro dev start


Once the containers are up, open your browser at http://localhost:8080. Log in, and you should see the new DAG named maths_sequence_taskflow.

Trigger the DAG. When you check the Graph view, you will see all five tasks connected in sequence:

start_number

add_five

multiply_by_two

subtract_three

square_number

When the DAG runs successfully, each task will show up in green. You can click on each task to see its logs. For example:

start_number will show the value 10.

add_five will show 10 + 5 = 15.

multiply_by_two will show 15 * 2 = 30.

subtract_three will show 30 - 3 = 27.

square_number will show 27^2 = 729.

If you check the XCom tab, you’ll also notice that each function’s return value is automatically stored in XCom without us writing a single push or pull statement. That is the magic of TaskFlow API.

Conclusion

So that’s how you create DAGs using the TaskFlow API in Airflow. Compared to the old method with PythonOperator, this is much cleaner and more Pythonic. You just define functions with @task, call them in sequence, and Airflow handles the rest — including task creation, dependencies, and even XComs automatically.

In the next step, we’ll look at additional parameters and features of TaskFlow API, but for now, this simple math sequence example should give you a solid understanding of how it works.

### Summary:

Key Concept: TaskFlow API (introduced in Airflow 2.0)

Lets you define tasks with @task decorator.

Return values from tasks are automatically stored in XCom.

No need to write xcom_push / xcom_pull.

Task dependencies look like normal Python function calls.

Makes DAGs cleaner, simpler, and more Pythonic.

🔹 DAG File → dags/taskflow_api.py
Imports
from airflow import DAG
from airflow.decorators import task
from datetime import datetime

🔹 DAG Definition
with DAG(
    dag_id="maths_sequence_taskflow",
    start_date=datetime(2023, 1, 1),
    schedule_interval="@once",
    catchup=False
) as dag:


dag_id = "maths_sequence_taskflow"

schedule_interval = "@once" → run only when triggered manually.

catchup=False → no backfilling.

🔹 Task Functions with @task

Start with 10

@task
def start_number():
    initial_value = 10
    print(f"Starting number is {initial_value}")
    return initial_value


Add 5

@task
def add_five(number):
    new_value = number + 5
    print(f"{number} + 5 = {new_value}")
    return new_value


Multiply by 2

@task
def multiply_by_two(number):
    new_value = number * 2
    print(f"{number} * 2 = {new_value}")
    return new_value


Subtract 3

@task
def subtract_three(number):
    new_value = number - 3
    print(f"{number} - 3 = {new_value}")
    return new_value


Square

@task
def square_number(number):
    new_value = number ** 2
    print(f"{number}^2 = {new_value}")
    return new_value

🔹 Task Dependencies (looks like normal Python calls)
start_val = start_number()
added_val = add_five(start_val)
multiplied_val = multiply_by_two(added_val)
subtracted_val = subtract_three(multiplied_val)
squared_val = square_number(subtracted_val)


Behind the scenes → Airflow builds DAG structure.

Dependencies:
start → add_five → multiply → subtract → square

🔹 Running the DAG

Start Airflow:

astro dev start


Open Airflow UI → http://localhost:8080

Trigger maths_sequence_taskflow DAG.

🔹 Monitoring Results

Graph View → tasks connected in sequence.

Logs:

start_number: Starting number is 10

add_five: 10 + 5 = 15

multiply_by_two: 15 * 2 = 30

subtract_three: 30 - 3 = 27

square_number: 27^2 = 729

XCom tab: return values (10 → 15 → 30 → 27 → 729) are auto-stored.

**Conclusion**

Compared to PythonOperator + manual XComs, TaskFlow API:

Is cleaner and requires less boilerplate.

Automatically handles XComs & dependencies.

Feels like writing normal Python code, but produces a DAG.

Next, we can dive into advanced TaskFlow features (like retries, retries with exponential backoff, custom XCom backends, branching).

## **J) End-to-End Github Action Workflow Project with DockerHub**

**1. Github Action Workflow Project with DockerHub**

So we are going to continue our discussion with respect to "GitHub actions". And in this video we are going to see a new workflow, which we are going to implement it as a complete end to end project. And the best thing will be that in this project we will be having both "CI, CD pipeline", a kind of "CI CD pipeline", because we really want to start from the basic things. So this example would be an amazing example altogether.

So what we are basically going to do in this example, it is very simple. First of all we are going to create a "flask app" okay. So "continuous integration" whenever we say whenever we say continuous integration that basically means let's imagine that we are developing a data science project which requires to develop a flask app right in the flask app. Usually many people work. Many developers work. Now with respect to any stories that I create in flask app, I am going to create a unit test cases. And once we probably commit the code, we once we push push the code into the main branch. My unit test cases should run and it should also build, right?

So after this is done, we go to the next step wherein we build the entire artifact. And again we do this unit testing as we go ahead. Right. So in our "GitHub action workflow" the first step is nothing but "build and test". Here we are basically going to implement our continuous integration. After we do the build and test, what we really need to do is that in this build and test we also will be creating our "Docker image". Right. So the Docker image will be created for this entire application right. This will be the most amazing thing. An entire Docker image will be created in a container specifically uh, considering uh, Linux. Uh, again, it depends like what kind of OS you really want to use as a container for building this entire Docker image. I will specifically take a Linux version once.

I probably create a Docker image. Once I validate this Docker image, once everything is working fine, then the next step we specifically go with deployment. And that is where your "continuous deployment" will work. Now where we really need to deploy this. See this Docker image usually specifically deployed in "Docker Hub". Right. So Docker Hub is a public repository for the Docker image. Once you deploy in this Docker Hub, then anybody can pull that particular Docker image and can probably execute in the local machine, uh, if they have Docker installed. Right. So this entire process will be doing it.

And the best thing over here is that whenever we are doing the deployment here, we also need to create some secret keys. Okay. Some of the secret keys. In this example we will be specifically using like "Docker username", docker username. And the second one that we will be specifically using is "Docker password". Right. So Docker password is nothing. But we will try to generate a token from the Docker Hub itself. So I will be showing you each and every step as we go ahead.

And this will be a perfect example of implementing a developer workflow, because here we are just not implementing continuous integration. We are also focusing on the deployment part, wherein we take the entire image and we deploy it directly into the Docker Hub, and we'll automate this entire process. No manual activity will be there. Here. The additional things that we are going to use, tools that we are going to use are nothing but "git". Second one is "GitHub" right GitHub repository. The third one that we are specifically going to use over here is "Dockers". Right. Dockers. And we'll also be using "Pytest" for our unit testing. Along with this we will be using "flask" to develop our application.

So we will be starting from completely basics and we'll create the repository. We will commit the code. Each and everything will be do doing as we go ahead. So let's go ahead and check out this amazing project.

**2. Setting Project Structure With Github Repo**

So finally we are going to go ahead and implement this entire workflow what we have specifically discussed. So step by step we will be going ahead you know. So let me just go ahead and minimize this.

Uh, first of all this is the folder location that I'm going to work with. So here is something called as Docker image. I will just go ahead and open my VS code. You can either open it from here or you can open it from terminal okay. So once we specifically open this entire terminal, uh, the first thing is that I will go ahead and create my requirements dot txt file just to make sure that what all requirements I'm going to use, um, as you all know, that two important requirements that I'm actually going to use. One is I'm planning to create a flask app. So flask will be there. Along with that we also need to perform unit testing. So this Pi test will also be there okay so this is my requirement dot txt file. Let me just go ahead and write the spelling correctly okay.

Now after creating the requirement dot txt I also require my app.py file here. My flask app will be written. Along with this I will also create my unit test cases. So see, one very important thing about unit test case is that if this pi test pi test library that we have imported, right, if we really need to identify all the unit test cases, you need to probably create your file name beginning with test okay. Test underscore. So any file that you probably begin or any folder that you probably begin with test right. It is automatically going to probably consider that as a unit testing files. Right. So here I'm going to probably write test underscore app dot pi. And here I'm going to probably go ahead and create all my unit testing things that I actually require okay. So all my code related to unit testing will be developed over here okay.

Along with this I also require a Docker file. So let me just go ahead and create my Docker file over here so that I will be able to create the image from this docker file. Along with this I will quickly go ahead and write dot GitHub workflow. All right. So I have to probably create this particular folder that is GitHub workflows. Because here is what I will go ahead and create my YAML file. So I will go ahead and write ci CD, dot YAML file, which will be my continuous integration and continuous deployment dot YAML file. Okay, so all these files are ready. We are good to go.

Let me do one more thing. Let me quickly go ahead and create one more file which is called as dot git ignore okay. Because I don't want to commit each and every thing that will be occurring over here. Right. Uh, what you can also do over here is that once I, once you go ahead and create this file, you may also want to create your environments. Right. So whenever you are specifically working in a bigger project, we basically go ahead and create an environment. So let us go ahead into our terminal. And uh here I'm just going to open my command prompt. And let's quickly go ahead and create our environment.

So first of all I will say conda deactivate okay. For every project, it is a very good idea that we create a separate environment altogether. So I'm going to write conda create minus p v and v python with some version. Let's say the version is 3.10. Any version that you can specifically use now once this environment will be created, your V and V folder will get created over here. Right? So in this git ignore, whenever I'm committing the code, I have to make sure that I don't write. I don't take this v and v folder. Right. So I don't want this v and v folder. So I can just go ahead and write this like this. Right. So let's first of all write like this.

And because once we go ahead and initialize this entire repository and commit this code in our GitHub. Right. I don't want my v and v folder to go right. Other than this I want each and every folder like dot GitHub, every folder, every files. I basically want all these things to probably go into the GitHub repository. Right. So these are some of the basic things. Now I have also done this um, then once we go ahead and create our environment and then what we really need to do is that we need to activate the environment. So let's go ahead and activate it. So I'll write conda activate Venv. Okay.

Now after activating the environment, the next thing that I'm actually going to do is that I'm going to install my requirement dot txt okay. So we will go ahead and proceed with the requirement dot txt see directly. You can also go ahead and just put your code in the GitHub repository. Right. Everything. You can probably do it, but it is always a good way because whenever we are developing an end to end project this way, we have to probably do with all our ID, right? So perfect. I have also created my git ignore v and v is put up over here. Everything is perfect over here. Now my environment is also loaded. All I have to do is that I have to go and write my app dot pi and test dot pi code app dot pi code.

Okay, now this is done. Now in my next setup, what I really need to do is that I need to go ahead and set up my GitHub for GitHub repository. And that is what we are going to see in the next video. So yes, this was it. I will see you in the next video. Thank you.

**3. Setting Up Github Repository**

So guys, we are going to continue our discussion with respect to this particular workflow, where we are going to create our Docker image and deploy it into a Docker Hub. We are going to automate that entire process.

In our previous video we have already done this project setup. Now the next thing is that we will go ahead and create our GitHub repository. Okay, now in order to create a GitHub repository, I will go ahead and click on New New repository. Again you need to have a GitHub account. So please make sure that you create this specific account. And let's say that I'm just going to write Docker Image Hub right. So I'm just going to go ahead and write this.

Um I'll keep this as private because I don't want to probably expose it to everyone. I will not select any of the option over here. Description. Add a git, ignore everything. I'll keep it as empty because I'm going to create all these files and I'm going to start okay. So let's go ahead and create the repository over here. So once I create the repository.

So this is what I'm able to get right now. First of all let me go ahead and create my Readme file over here. So I will go to my code and create my readme file. So read me.md file. Okay, so I will say hey, uh, this project shows shows how to work with GitHub action. Okay, so something like this I'm just going to write some description. Okay, perfect. Uh, this is all good.

Now once we have all these things, I'm going to clear the screen. And first of all, you just need to follow this. Right. If I really want to make this repository where I'm actually going to commit, first of all, the command is nothing but git init. Get in. It basically means we are going to initialize the git init, uh, initialize this repository for that. Right. So this basically creates a dot git folder.

After we do this the next step is nothing. But we are going to add readme. I will not add readme. Instead I will go ahead and add each and every file. And here you can probably see with respect to git ignore this v e and v file is not considered. And this dot GitHub ci CD dot YAML all these files ci, CD, YAML file is currently empty. But I'm just going to go ahead and do the publish. But V and V file will not be folder will not come because in the git ignore I have given this v and v folder. Right.

And let's do one thing. I will just go ahead and commit it okay. So let's go ahead and write git add dot okay. And then I will go ahead and commit my entire code git commit minus m. Uh this is my first commit okay. This is my first commit. So all the files will be, uh, you know, committed in my, uh, remote repository. Okay.

Now, from this remote repository, I need to go ahead and first of all, create a branch. So here I will go ahead and write git branch minus m main. So once we do this then we are going to uh configure our remote repository to this particular origin which is probably given by this GitHub repository itself. Right. So I'm just going to go ahead and copy and paste it.

Once this is done we are into the right repository. Now we can go ahead and push all our commits inside this. So once we push it, you'll be able to see all the scores. Or sorry, all this content that I have written, all these files will automatically get added over here. So if I reload this, you'll be able to find out this entire project structure with GitHub workflows each and everything.

Now still my GitHub workflow ci CD dot YAML is completely empty. I don't have anything. I still don't have anything in my app. Dot pi or test underscore app dot pi. I just have this requirements.txt which I have over here. Okay, now step by step we will go ahead and implement in the upcoming video.

So what we are going to do is that in the next series of video, we are going to probably develop our entire project, and then we'll go ahead and create our Docker file. Along with that, we'll also go ahead and create our test underscore app dot pi file. And once we commit the folder and once we design this, once we write our entire YAML structure, right YAML structure for the GitHub action workflow. This is where we are going to design our GitHub action workflow.

**4. Implementing Project With Flask And Dockers**

So guys finally now let's go ahead and implement our app Dot Pi.

So here what I'm actually going to do is that I will go ahead and write from flask import flask. Okay. And here I'll just create a basic flask app. Okay. Just to show you an example. So here I will be having underscore underscore name underscore underscore okay. And there I'm going to basically go ahead and create my app dot route. And this app dot route will be for my homepage slash. And here I have my definition home okay. And I'm just going to say hey return something like hello World. So once I go to the home page it should return hello world. That's it. Okay, so that's it.

And here I'm going to basically go ahead and write if underscore underscore name underscore underscore double equal to underscore underscore main underscore underscore. Then we want to basically go ahead and write app dot run uh by default uh my host IP address will be nothing but, um, 0.0.0.0 and my port will be nothing, but it will be equal to 5000. Okay. So by default I'm giving the port as 5000. So this is my entire app.

If you probably want to run this app it's very simple. Just go to the terminal okay. Close this okay. And from here you can just go ahead and write Python app dot p y. So it should definitely run I will click on Allow Access and if I click on this link. So I should be able to see my application. So this application basically displays about Hello World. Perfect.

Now my aim is just not to create this particular application, but I really want to convert this into a Docker image and deploy this into the Docker Hub. But before that, I also need to make sure that I write my test cases right? So in order to write the test cases, I have already created my test_app.py file right now here. What I will do is that I will quickly go ahead and write from. App import app. Right. So we are going to import from from this particular app.py file. I'm going to import the app itself, this app. Right.

And after we import this app I will just go ahead and create one function which is like text underscore home and understand. Always remember if my Pi test library needs to find out which are the test use cases or which are the function, we really need to go ahead and write test over here. We need to start any function. We need to start any file name with test underscore okay. And then we have our test underscore home. Then I will go ahead and write response. So let's go ahead and take a response here I'm just going to write app dot test underscore client. So there is a function called as test underscore client dot get okay. And here we are just going to get from the home page.

Once we do this this app is just going to give you some kind of response. And here the major response that we need to check is by using this assert statement. So here if I go ahead and write assert dot status code is double equal to 200. Right. So this basically indicates that this is a successful request. Then again I will go ahead and write assert response dot data double equal to. Here I will just go ahead and write some message saying that hello world. Right. So this is just one type of test case that I'm actually trying to check. Okay.

So I have written my app Dot Pi. I have written my test cases over here. And this pi test will automatically find out which all are there because it will just look for this particular file name and the function name itself. Okay, now after doing this we have to probably go ahead and create our Dockers. Right. So Docker file is over here. Now what I'm actually going to do is that I'm going to use a Docker, which we have already discussed in my Docker series of videos.

So here I'm going to use the Python image from the Docker Hub, which is nothing but Python 3.9 slim. Um, then we are going to set a working directory that is slash app. Then we are going to copy from this current location to this entire slash app. Then we are going to run pip install flask along with this. Uh, what I will also do is that since this, we are planning to create a Docker file altogether, right. Uh, this flask app will be useful for running this entire code. Okay. Then we are going to expose the port 5000. And finally we are going to run this app dot Pi when the container launches. So for this we will be using a command Python app.py.

I hope everybody is familiar of creating this particular docker file, which is already covered in my series of videos with respect to Docker, and I hope you can probably see the module also. Right. So this docker file actually helps you to create a Docker image of this entire application that is nothing but app dot p y. Okay, so perfect. This is all done. Uh, here we have entirely designed our entire app. Dockerfile is ready. Test underscore app dot pi file is ready.

Now. In the next section we are going to go ahead and write our ci, CD, YAML file. Okay, now we are just going to see that how we will go ahead and write. And each and every thing we will go ahead and discuss what all things are there. Because two main things I'm going to focus on my workflow. One is build and test and one is deploy and build and test. I need to be doing the building part. I need to install the libraries and for testing I need to install pi test. Right? Both these things needs to get executed in some Linux container ubuntu latest. And then we go ahead and deploy it.

For deploying. We need to configure our Docker username and password, uh which are my secret keys. Which, which you have an option to put it in the GitHub itself. And then finally we'll go ahead and deploy in the Docker Hub. After we deploy that in the Docker Hub, we'll also pull that particular image and we'll try to see whether it is working fine or not.

So yes, this was it. Now in the next video, let's go ahead and build my YAML file. Thank you.

**5. Building the Yaml file for Dockers**

So finally we are going to now create our YAML file, which I have actually named it as ci, CD, YAML.

So let's go ahead and again if you remember what is our aim. Our aim is very simple. We really need to create a workflow which will actually help us to build and test the entire application. Along with that, we will also try to create a continuous deployment where it will try to deploy the entire application in the form of Docker image into the Docker Hub, right? So that anybody can use those specific images.

So let us go ahead. And first of all, uh, as you all know, we have to start our YAML file with a name. So here I'm going to give a name called as ci CD for Dockerized flask app. Okay. So once this is specifically done then I will go ahead and talk about on which events we really need to trigger the workflow. So here for this I will going to specifically use over here as on push of branches on main and pull request on branches of main.

Then, uh, if I probably. First of all, what? Let me do one thing and let me just go ahead and copy this entire thing over here so that your it will become easy for you all to understand. Okay. So let's talk more about this. So for this I will just open my pen. Let me do one thing. Let me clearly explain this okay. So first of all here you can actually see that we have to probably start with the name. Right. So name of the uh name of the workflow that we are specifically using. This is CI CD for Dockerized flask app, right on which events we need to trigger it.

So here I'm actually using two events. One is pull push, one is pull request on which branches main branch okay then you have jobs. Now in jobs we are going to use two specific jobs, right? One is build and test. Build and test is basically to run your unit test right unit testing. And here also we are specifically using this container that is your ubuntu latest container. In this you will be able to see the steps.

So job this is my job name. Okay. And it runs on ubuntu latest. Then we can specify steps one by one. The first step is basically to check out the code from the repository. The second step is to set up the Python repository. So here you can see sorry Python version we are going to probably use for in inside the container. So here we are going to use this action set up Python at the rate version four. In our previous example we have seen version two. Similarly version four is there, version three is there. But I would suggest go ahead and use the recent version. And here we are going to use the Python version 3.9 okay. You can also use 3.10. It is up to you. Okay. So this is the most important thing with respect to the jobs.

Now if I go ahead then if you go ahead and see okay, after this, the next steps that we have actually mentioned inside this right. The steps actually specifies about the workflow. Okay. So here we are going to install the dependencies. First we are upgrading all the Pip, then we are installing flask and we are installing Pytest instead of this. You can also go ahead and install the requirements.txt directly by mentioning flask and pytest over there. But one by one we have specifically installed and then we are going to create one more workflow step that is run test. And we are going to run pi test.

So pi test what it is basically going to do wherever there is a file with the name starting with test underscore and the function which is there which is starting as text underscore, it will consider all those as the unit test cases. Now this is one of the job okay. So this entirely one of the job which I am specifying as build and test. So if you probably see in the diagram in this build and test what all things are basically happening clearly you can probably see over here we are uh, we are first of all running it on the ubuntu latest container. Then we are checking out the code from the repository. We are setting up the Python with 3.9. We are installing all the dependencies and we are running pi test. So this in short is doing the build and running all the unit test cases.

Now in the second one we have something called as build and publish. Okay. So this is the name that you can specify. You can specify any name. Right. It is up to you. It is not need not be always same. Right. So here I'm basically saying build and publish. Publish your Docker image into the Docker Hub okay. So here you need build and test. That basically means see this need keyword is very important okay. This is basically saying that you need to first of all perform, build and test. After you perform this, then only you have to start this okay. If you remove this, both can start Parallely okay. And this also runs on ubuntu latest.

And then here you have steps name checkout code add v3. Then you are setting up Docker build x okay. And this is uh GitHub action provides you in order to set up the docker. It will provide you like how you can probably check out the code repository. Similarly there will be a action for this also. Okay. And our main aim is this. Right, we want to probably take that entire Docker image. We want to build it and then we want to push it to the Docker Hub. right? Then you have this one over here. So let me just go ahead and see this.

So this is nothing but, uh, your login to your Docker Hub for logging to a Docker Hub, we have another action which is again provided by the GitHub action. You can just Google it or see the documentation of the Docker Hub itself. You'll be able to get here. We are going to specify two important things. One is the uh secret dot Docker user underscore name okay. And then you have secrets dot docker underscore password. Now this is the most important thing from where do you get the Docker underscore username and Docker underscore password. Let me just go ahead and show it to you.

So first of all, what we are basically going to do is that I'm going to go ahead in Docker and I'm going to log in over here. Right. So let's say this is the Hub.docker.com I will just go ahead and um log in over here. And if you remember, I have already covered in my Docker series into Docker Hub. You can publish any kind of Docker image that you want and it will be accessible for everyone. Right. So here you can see I can probably see all the repositories. You have to probably log in inside this. Okay.

Now in order to get your username and password, username is nothing, but it is nothing but this same username, right? In order to get the password, you need to create a token. So I will go to Account settings. After going to the account settings you can probably see there is something called as personal access token. Okay. So you have to go ahead and click on this. And you can go ahead and generate a new token. So here I will generate a new token I'll say Docker image test okay. And please make sure that it should have this read and write and delete option. It is good so that you can directly publish it in the Docker Hub. If you want to delete it, you can directly delete it or you can write anything. So I will go ahead and click on generate okay.

So once this is generated so this is my this is my personal access token okay. Now if I have this personal access token that basically means in my Docker hub I will be able to upload all the images. And these are some of the images that I have already uploaded. Okay. And these images plays a very big role because you can directly access this image and run my entire application. So I will copy this. Then I will go to my, uh, GitHub. And here you have something called as settings. Okay.

After you have the settings, if you go down there will be something called as secret and variables. Okay. And inside the secret and variables you have something called as actions. Now here inside the actions we will go ahead and create secret keys okay. The reason why we are creating secret key because it is very simple. If you go ahead and see over here, I have to create two secret key Docker underscore username and password. And this is probably coming from this GitHub secret key itself. So I will go ahead and select this. And I will create a new secret key. I will go ahead and paste it over here. Let me go ahead and write my username. That is nothing but Krishna 06 I will go ahead and add the secret and then I will go ahead and create a new repository secret.

The new repository secret will be nothing but docker underscore password, and this time I'll paste it over here and I can take my password prompt or password access token from here I'll copy and paste it over here. Right. So this is done. So here you have this two secret keys that is readily available. And now the code that GitHub actions will be able to access this once we update the YAML file. Right. So this is the first step. So that basically means we are able to access this both Docker underscore username and password okay. Now this is with respect to the step which is called as build and publish okay. Build and publish.

Now inside this build and publish step by step workflow. This will happen. First of all we are going to check out the repository. Then we are going to build up the Docker itself. We are going to login into the docker with the secret username and password that is given over there. And after this, you will also be able to see that we are going to build and push the Docker image. So for this also a separate action is there right? So Docker build push action and v4. Similarly over here for login you have login action and v2. This is already provided by Docker itself by GitHub action itself. All these uses are there. Right.

Then we will go ahead and write with context dot Okay. And I'll say push is equal to true. And we'll assign a tag name. And I'll say, hey, we want to probably do this flask test app. We just need to use the username and we'll use slash flask test app latest and it will automatically deploy. Understand the naming convention of the Docker should be in this way where you should be getting your username over here and then whatever name you want. And it should end with latest or any version that you specifically want. Okay.

So this is a very important thing, right? We are just trying to push the Docker image into the Docker Hub. I'll show you this entire implementation. You'll be able to understand. And then finally I am just creating one more important step in this workflow, where I'm echoing some of the information that comes over here from this particular digest. Right steps dot build and publish dot output dot digest. Let's see what it displays.

So this was the entire YAML file that I've actually created. Now what I will do quickly I will open my terminal and I will push this. Okay? I'll push this entire thing. So first of all, I will just go ahead and write git add dot. Okay then git commit minus m I will go ahead and say docker or ci CD YAML file is ready okay. And I will just go ahead and commit this okay. So four files is changed 91 insertions. Uh you can see over here docker ci CD file is ready. Everything is ready over here. And we are good to go with respect to this. Then I will go ahead and write git push minus u from origin to main. Okay.

So once I push this the entire push is basically done. Now as soon as I go back over here, I think your action should start working. See. And your actions have started. See your actions have clearly started. I will just go ahead and Execute this. Okay. Perfect. So this is build and test. And your build and test is working fine. See check out code repository. Setting up Python install dependencies. Run test. Everything has happened. Now we are into the build and publish. Right? So with respect to the build and publish it is now checking out the code. Now see this entire installation is basically happening. Okay.

Uh, build failed. Failed to solve to read docker file. Okay. Let's say this file name. Open docker file. No such file and directory. Let's see what is the problem over here. And I will try to solve this problem okay. Okay. So one problem that I probably see over here is that I have not mentioned my Docker file name. Okay. So over here we are giving this Docker username. We are saying that hey push is equal to true. One thing I missed out. We really need to provide the docker file over here itself. And based on that only it will try to push it. So let's see what was the changes over here. So here are one more parameter I really need to give is nothing but file colon dot slash docker file. Okay I need to specify my docker file name. That's it.

If I and see I can probably see this. You can obviously you can see the login to the Docker Hub is done. Run docker build push action. This is done GitHub action runtime is done. Info. We are getting it, but we could not get the docker file itself right because the path was not mentioned in the YAML file, right? So that is the reason you can see fail to solve uh, we are not able to open the docker file. No such file file and directory okay. So if you are getting this error don't worry okay. It usually happens okay. You need to fix it okay.

So here you have slash Docker file. Now let me just go ahead and commit it again I will go ahead and write git add dot git commit minus m docker file Specified in the specified okay. And here I will go ahead and write git push minus u from origin to main. Okay. So once I do this now all this commit is done. Now it should run again. See uh, let me go up. Oh my God, I have to go up now. If I go to the action. So this is failed one time. Okay. I think before also it has failed. Okay. But it's okay now. It should work. Okay.

So build and test. This should work successfully. It is able to run all the test. Let's see how many tests it is able to run. See test underscore app dot pi. It is able to pass this entire test. Now once we are into the build push it has logged in. Now we are extracting the entire docker and just observe this okay we have flask app, right. And my uh app name was Flask test. Right. So see everything is basically happening. Let's see. Uh, We'll just minimize all these things so that you can clearly see okay. So these are the steps that is basically happening in this build and publish.

Right. So first of all we are setting up the job and the setting up the job. We are running the version this operating system this is already handled by that. We are checking out the code right by using this checkout at version three. Then we are setting up the docker build x. We are running this action completely. To build a docker within the container, we are logging into the Docker Hub, which is successful, right? Because I have provided a secret username and password. And finally we are building and pushing the docker image. See docker info. It is getting all the information. It is probably from this Docker hub. It is basically from directly into the Docker hub.

It is directly publishing and we have automated the entire process. Before it was like we had to write a lot of command, right. And here you can see the name flask test dash app pull right push. So this will basically be my app name or image name that will be available over there. Right. So this is done. Then I have my image digest will echo some information. This is what it is basically echoing. Then post build and push Docker image. So post job cleanup. So we are pushing this entirely post login to Docker Hub post job cleanup. So now we have logged out. See this is also very nice right? Uh the checkout code, the action code of Docker. And this is that after logging into Docker, after pushing it we also log out right then uh, post setup docker build x post job cleanup where we are cleaning up all the certificates.

And finally we have this post checkout code. So this entire process has been automated. Now the best thing will be that if I just go ahead and reload it, you'll be able to see my new Docker image will be available over here. Flask test app. Right? So here is my new image that is specifically available right now in order to call this image. It is very simple. I will just go ahead and open my command prompt. Okay I'll call it in my local. See this? Okay. So I will just say, hey, go ahead and execute this command. I will write docker pull Grishnackh zero six slash flask test app. Right.

So once I pull this, what is going to happen with the latest version is just going to pull it. And then we can specifically run this. Okay. So now already exist flask test. See pull complete. Everything is done right now I think you should be able to see this. You should be able to see this. Let me just in my Docker desktop. Right. So in my Docker desktop still you're not able to see. But if I go to the images you should be able to see over here flask test. Right. And just now three minutes back you can see that 136 MB.

Now if I want to run this, how do I run it, which I have already shown you in order to run it I will go ahead and write docker run minus P, the local port that I'm host port that I'm actually going to take is 5000. And since this is going to run in the container from the container port, I will expose it to 5000. Okay. And then I will write zero six slash whatever is the app name. So I will go ahead and write flask test app and latest okay. Once I execute this now here you have this. All I have to do is that just go to my localhost.

So let's open my browser over here. And I'm running this in 5000 if I execute it this is my hello world. Now this is what I'm accessing is directly from the container right. The same container which I have actually deployed over there in my Docker hub. Right. I've actually started that. And here also you can basically see now if I go ahead and see in the container this is running flask test app is running in 5000. Right. So this is the entire workflow and we have automated this entire workflow. Now any changes that specifically happens over here, it is going to build the entire Docker. And it is going to probably do each and every thing, and it is going to push that entire Docker image over there. Right.

And I hope you have just got an idea like how to specifically work like this here. We have done this build X and all we can. We also have some code where we can build it manually. But since we had this action command I thought of using this

But I'll give you an assignment. Try to just explore the page, try to explore the documentation, try to find out how do you build this directly. Okay. If I want to really build it, I can also do this build right if I really want it. Okay.

Um, let's say that I want to go ahead and do the build. I can actually create another workflow, uh, another job over here, which will just build my Docker image and see whether everything is fine. Let's do that. Okay. Let's let's do that also so that you are much more comfortable.

So what I will do over here, um, like I have built and test, I have built and publish. Let me go ahead and create one more build. Okay. So I will just go ahead and write something like this. So this will be my another job which will be looking like this. Okay.

So here let me just go ahead and write okay. So this is my job. Just a second. There is some issues. Always always remember one thing guys. Okay. Uh, whenever you are actually writing any kind of build, you have to also maintain this kind of spacings with respect to the YAML file. Okay? If it does not happen, like then it will be a problem, right?

So I will go ahead and write runs on okay. So this also I will try to run it on ubuntu ubuntu latest. And then I'm going to probably go ahead with the steps. Now inside my steps. The first step that I'm going to use is which thing it uses. Let's say I'm going to use the action action check out for version four. Okay I will just go ahead and check out the version four okay.

And after this I will give a name. Name will be just like build a Docker image okay. We can also build it. I'm also automating this entire process. Build a docker image after name. And then finally we go ahead and run this command right. So we need to run it right.

If you see over here we have also defined this kind of run okay. So inside the run command we will go ahead and write docker build dot dash dash whatever file I have. And this will be my docker file. The name of the docker file dash dash tag with some tag over here. Workflow. Workflow. Let's say workflow test. I'm just giving okay. Just to see whether it is basically building or not. Right.

And here I will also specify some date date plus percentiles okay. Thus I think this will be more than sufficient okay. And we should be able to use this. Now let's see whether this will also work or not. I just want to try it out. Um here we are also doing the docker build. So here I will write docker build.

Then we have this build and test another job and build and publish is also another job. Okay then. And always remember guys you don't need to buy hard this okay. Be smart enough. Uh when you do the Google, if you see the documentation, you'll be getting a lot of different different YAML files for different purpose.

And as we go ahead, I will also try to do the deployment in AWS cloud and all. Okay we'll see that. So now I'm going to write git add dot then I will go and write git commit minus m. So here what we are basically doing is that docker build okay docker build we are adding. So I will just go ahead and write what our uh git push u origin to mean. Okay. Done.

So now I think it should run. So let me go back to the actions now. So this is my docker build. Now three important things will learn see docker build build and test is running parallelly okay I do not I do not write any dependency. If I had written any dependency then build test would have run later on. But I am interested towards this right to see whether the docker is basically getting built or not.

So here you can see my docker is basically getting built and it is good enough, right? Nice. My entire Docker build is basically happening, happening automatically in the container itself. That is the reason why I like this GitHub actions a lot. You know, the entire process can be automated. So we are building things. We are testing things. We are automating things over here. You know, so anybody who is making a commit, if we make some changes in the Docker file and if that build is not happening, it will break it down. And then we will not be merging the code itself automatically. The error will come. Right.

That is the most amazing thing. So this is entirely done. Now if I go ahead and see. So this will basically be my Docker app okay. Anyhow I will close this. Uh, let me just go ahead and close this. So I will close it from here, my command prompt and let me just stop it. Okay. This entire Docker image. Perfect.

Uh, so I hope you were able to understand this particular video. Uh, this was about creating an amazing workflow. Now as we go ahead, we'll be seeing more different workflows. But the main thing will be that we'll try to implement all these things along with our end to end projects.

So yes, this is this was it from my side. I will see you in the next video. Thank you.
