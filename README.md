# MLOps-Skills

### "python-box" - A Python Library which can be used for Exception Handling

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

**K) Getting Started With Your First End To End Data Science Project With Deployment**

**L) End To End Machine Learning Pipeline Using GIT, DVC,MLFLOW And DAGSHUB**

**M) End To End NLP Project With HuggingFace And Transformers**

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

### **K) Getting Started With Your First End To End Data Science Project With Deployment**

**1. Project Structure, Github Repo And Environment Set Up**

Hello guys! So welcome to this new amazing module about end to end projects with deployment. So till now we have discussed about MLflow. We have discussed about astronomy. We have discussed about airflow. We have discussed about data version control. We have seen how to probably go ahead and deploy in AWS. Even I've actually shown you how to deploy an astronomer cloud. And in short, we have seen the entire lifecycle of machine learning project or data science project. But this kind of projects were very, very basic and I feel that it is still, for starters, okay. But everybody should understand that how you should if you are probably going to work in one of the companies, right? How do you probably go ahead and create your end to end data science project where we flow, where we follow a complete life cycle of a data science project, you know, from data ingestion to data transformation to feature engineering, to model training, to model evaluation. So all that specific steps are. The main aim of this entire course is that to teach you about end to end projects. Along with that, how we can use specific MLOps tool, uh, to manage that entire lifecycle of a data science project. And also make sure to show you multiple deployment techniques.

So considering this now from this particular module, uh, and in the upcoming series of videos, we are going to see different, different end to end projects and what all different kind of, uh, MLOps tools I'll be specifically using. And these are all the best part of this particular projects will be that we'll try to deploy this. And for this I'm going to consider the cloud called as AWS, which is one of the most famous cloud platform right now. Many, many companies are specifically using this, okay. And even in interviews this will be very helpful for you. Uh, so in this module and in the upcoming series of video, first of all, we are going to discuss about one end to end project. We will see how in production right when we are specifically working in a company. How do you develop a project? What strategies you specifically used? How what kind of code you actually write? Uh, when we say modular programming, how that entire modular programming is there, how do we create the entire ML pipeline? You know, each and every steps. I will start showing you, okay.

Now, first of all, what I will do is that I'll go to my repositories, okay. So I will go ahead and create one simple repository. Let's say this is my repository over here. And this repository that I'm actually going to create will be my, let's say my data science project. Okay. Data science project. The prerequisite for this entire session will be that you really need to know Python programming language. You need to understand the entire life cycle of a data science project, at least some some understanding about machine learning algorithms and all. So here I'm going to keep this particular project as private just for now okay. And I will just go ahead and add a Readme file Okay. And let's choose a license. Let's say that I'm going to probably go ahead and select a general public license. Okay. So I will first of all create this specific repository. Because in this repository itself I will be writing my entire code. If you have never developed a complete end to end project, this project will be very, very handy and very, very useful for you. Because here, step by step, coding wise, each and every line of code, I will write it in front of you. Okay. So let's go ahead and create this specific repository. Now once you create this particular repository this is my entire repo.

Now the first thing that I'm actually going to do is that I'll just go ahead and clone this entire repository. Okay. So for that I will open my, uh, folder. Let's say, uh, I have actually created one, uh, location over here so that all the code will be provided at one place. Okay. So if you see this particular folder, MLOps. Okay. This is my folder in E drive. You can create it anywhere you want. Okay, so from here, what I will do, I will just go ahead and open my command prompt. Okay. Now from here, after opening your command prompt, the next thing that I'm actually going to do is that I'll go ahead and take this entire repo, and I'm just going to clone it. So let's go ahead and write "git clone <your repo URL>". Okay. So I'm cloning the entire data science project over here right. So if you probably now go ahead and see the folder here, you'll be able to see somewhere like data science projects. So this is the default clone that you have actually done. And this is coming from the repository itself. Then I will go to "cd" uh inside my data science. Let's say this is my data science project and I'm going to start my VS code. Okay. Everything from step by step we will see. And how you can basically go ahead and start with your project implementation. Okay. Now this is the basic step that we usually do in order to probably just. I've just cloned. I have my readme file. I have some license file over here. Okay, now, uh, what I will do is that I will also go ahead and create one "gitignore" file okay. " .gitignore". Okay. And in this git ignore let me just go ahead and create some of the folders like "venv". Because this will be my virtual environment which I don't want to even track it. Now this git ignore file, I will also go ahead and commit it. Okay. So I will open my terminal. I'll go to my command prompt. It's okay. You can also do it in PowerShell and all. Since I have already done the clone, I will go ahead and add all the files. I'll try to show you by committing this file. So whether the commit is working or not, then I will write "git commit -m 'git ignore is committed'". Okay so done. So here we have actually done the git commit for this particular file. Then I will go ahead and say "git push origin main". So we will see this is entirely getting pushed. So the code should be visible over here. Now if I go ahead and reload this you will be able to see my gitignore there. So the first step which is really important a GitHub repository setup is already done and we are good to go with respect to the coding.

Okay. Now let's start our main project development. Main project development. Now this is really important for you all to understand. Uh, what is the usual first step that we usually do. Okay. And that is what I'm actually going to explain you about. Right. So here let me just go ahead and write about this. So this is my end to end end to end data science project. Now inside this project we are going to add many more things okay. You will be seeing data science project. Now usually whenever you start any project, the first and the foremost important thing is that about environment. Okay. You need to go ahead and create your environment. Now why this environment is necessary. Let's say, uh, in a company, right there is a lead developer. Okay. Lead developer. Now, in this lead data science developer, what he will be doing is that let's say that he's working in multiple companies. Uh, sorry. He's working in multiple projects. So this is my project one. This is my project two. This is my project three. And this is my project four. Now, when this person is working in multiple, uh, projects. Right? And again, inside this lead developer, there will be many other data scientists who will be working. Right. And some may be in this project, some may be in this project, some may be in this project. Right. Now, one very important thing about this particular project is that each and every project has a separate Penances. When I say dependencies, it can be libraries, it can be packages, okay, it can be even different. Python version right? Let's say this particular project we are working in Python 3.8. This project we are specifically working in Python 3.9. This we may be working in Python 3.12. So different different requirements. And this project has just started. Let's say we are working in 3.11 okay. So based on this specific versions we may have different different dependencies of the libraries and all.

Now just imagine if the lead developer wants to probably set up this entire project in his or her system, then what she or he has to do first of all, to set up this particular project, they need to have a separate environment. So let's say this is environment one. For this there will be another environment that is env two. Then for this project there will be another environment. Environment three and similarly this will be environment four. The reason is very simple because he or she wants to segregate all the information related to projects separately. If they just create one specific environment and try to run all this project in the same environment, then it will not work right because there may be some conflicts that will happen because of the different different versions, right? So the first step, whenever you really want to go ahead and create a data science project, it's always a good idea that you go ahead and create your environment. Now, creating an environment obviously can be done by multiple ways, but the most efficient way. What I feel is by using conda. Okay, so what I'm actually going to do is that I will just show you how to go ahead and create your environment. Now, this time, the environment that I'm actually creating, I will create my environment folder over here. You know, so that I should be able to install all the packages inside this environment. And my environment name should be Venv. So here what I'm actually going to do, I will just go ahead and create conda command "conda create -p venv python=3.10". Okay. And then we will go ahead and click on yes. So once we do this here you will be able to see that my installation will start taking place. And this is my venv environment. Now see this is not getting tracked by the git because I have written this particular information in the git ignore.

Okay now what I will do till the installation is taking place, I will go ahead and update my "requirements.txt". Okay, so the environment that the python that we have specifically using is 3.10 okay. You can also use 3.11, 3.12. But again please do check because I have already created this entire project in 3.10. For me, everything is working. Uh, if you change the environment, there may be some issues with respect to different different packages. They may come. Okay. I also don't know okay. Because there may be updates in some of the libraries and all. Okay. Now once I have created this environment I will go ahead and activate this environment. So "conda activate venv". Okay. So once you can see over here I have activated this environment. So here you can see "conda activate venv". So inside my venv. It is basically referring to my environment to this particular venv okay. Now let's say that if I go ahead and create one file "app.py". So on the right hand side you can see 3.10 venv. Conda is basically selected by default. If you want to change this just click this. Select the different environment that you really want okay. So for right now I will not create this app.py. So this will be my "requirements.txt". Now for uh easiness. Uh, what I'm actually going to do is that I will try to write down all the requirements that I'm actually going to use. Okay. And step by step, I will also show you that what all things we will be using and all as we go ahead. Okay. So right now let me do one thing. You know, since this should be efficiently working okay. Uh, I will update all my "requirements.txt" over here. Okay, so I'm going to use "mlflow", whichever is the recent version "python-box", whichever is the recent version and "ensure". Okay, so this all libraries we will be specifically using. I will be talking about each and every libraries. "scikit-learn" is for my machine learning problem statement. If you want to do any kind of visualization it will be "matplotlib". Then I have "python-box", then I have I'll talk about what exactly is this python box, why it is useful, you know. Then we also have this something called as "ensure", right. And we'll be implementing our front end with the help of "flask" and "flask-cors". So that is the reason I have imported all these things. Okay now for the name sake. Right now let's go ahead and install all these libraries. See I will talk about it. Why I have installed import. I have used all these libraries and why I'm installing it once I develop the project. Okay. So now here I will let me clear the screen. I will go ahead and write "pip install -r requirements.txt". So once I go ahead with the installation here, you'll be able to see that my installation is taking place and we are good to go. And the best thing is that you have to be in that venv environment. So that basically means all my packages that I am probably installing. It is all getting installed in my venv environment. Right. This is the most important thing over here.

Okay, so let this installation take place and uh, quickly the installation is happening. Let's see. Okay. Uh, once this installation takes place, then we are going to go ahead with the next step. Okay. Now till the installation is basically taking place, what I am also going to do is that let's go ahead and create one more file which is called as "template.py". Okay. Now you may be thinking Krish, why did I create this specific file? It is very simple guys. See I need to have a generic project structure. Okay, there are different different libraries that are available in Python. Uh, so that by using those libraries also, you can probably go ahead and create your entire project structure. Okay. Like "cookiecutter", there are some libraries like cookie cutter and all. Okay. But again, if this is your first project, I would suggest never use that. Instead, focus on creating a generic project structure which is used in the industries and understand each and every file why you have created it. Okay. So what I will do is that I'll write an automated script over here, you know, and that automated script will actually help you to create your entire project structure. Okay. And that will be written in the with the help of Python. So till this installation is taking place, I'll just go ahead and minimize it. Now inside my "template.py" I will go ahead and "import os". Okay. Along with this I'm going to "from pathlib import Path". I'm going to specifically use this particular library, which is called as path. Then we are going to go ahead and "import logging". Then you have this "logging.basicConfig()". Okay. And we are going to set the logging some level okay. Some kind of logging. We are going to apply in this uh it is not required right now because let's go ahead and do this in the later stages, because I want to go ahead and create a generic logging for my entire project that I will try to develop in, in probably in some time. Okay. Here. Now the first thing that I'm actually going to write is "project_name = 'data_science_project'". Okay. I'll just go ahead and write data science over here. So this will basically be my project name. Now here I will go ahead and write my list of files that I really want to create. Now let's go ahead and create all my list of files. Now for the list of files, uh, the first file that I'm actually going to create, I will try to create a ".github" folder. Inside that we'll create "workflows" folder, and then inside that we'll keep this ".keep". Okay, ".keep". It's a generic file. But understand that uh over here I'm going to probably go ahead and create one of the file which will be responsible in doing the deployment. That is my GitHub actions okay. Automated deployment. So right now I'll just keep this particular file. Later on I'll update those files as we go ahead.

Now in my second file I will just go ahead and write "src/project_name". So this is very important, okay. So src will start with src, my entire project. So over here you’ll be able to see that one src folder will get created on this level. Inside that, my project name that is "data science" folder will get created. And we specifically go ahead and create one constructor "__init__.py". Now why we are specifically using "__init__.py" is so that we can convert this entire source folder into a package so that it can be imported anywhere. If I want to import any functionalities inside this, write whatever classes or functions or libraries that I write, this will be imported within the project, right? I can actually use it anywhere I like, so that is the reason inside every folder that we create, or a fresh folder that we create, we always need to create a constructor file that is "__init__.py", okay.

Then coming to the next folder, or the next folder, what I am actually going to create, I’ll just go ahead and copy and paste it. Now this time instead of writing "__init__.py", you know that inside my project, whenever I follow a life cycle of a data science project, I have techniques like data ingestion, data component—sorry, data ingestion, data transformation, model training, model evaluation. So based on that, all this should be developed in the form of pipeline. And this entire pipeline will be developed inside one common folder, and that folder I will be naming as "components", okay. So inside components I will also again go ahead and create this particular file "__init__.py". Again why I’m creating this particular file? Okay, this file will be created so that any functions, any libraries that I am or any classes that I’m calling inside this, it can be referenced anywhere, right. Because this will be considered as a package and it will get installed within the local itself right over here. So I will be able to call any libraries, any packages from here because of this particular constructor, okay.

Now coming to the next one, here I’m going to go ahead and use my f-string again, and this time let me go ahead and copy and paste it again, okay. So this time I will be using instead of "components", this time I will be using "utils", okay. Utils will be my generic functionality that I’m actually going to define. So any functionality that is generic and that is required to be used in my entire project, everything will be inside this util folder. So inside this util folder, I’ll be having my "__init__.py". Okay, coming to the next step here, I’ll again go and copy paste this, and this will be again utils. And inside utils I will create a file which is called "common.py". Now again this naming convention it is up to you whatever things you are able to understand. If you are not comfortable with this name, you can use your own name, okay. This "common.py" will be having all the functionalities that I’m going to write which are common to most of the different components that I’m actually going to define, okay.

So here is my next one. Then similarly I will go ahead and use one more folder which is called "config", okay config. And this will basically be having my "__init__.py" which is my constructor, okay. Along with this, I will also go ahead and use a "configuration.py", okay. Then similarly you can go ahead and use it for "pipeline". Pipeline "__init__.py". Similarly, this pipeline folder will be having all the information regarding what all different pipelines I want to create. One is the training pipeline, one is the prediction pipeline, right. And training pipeline, it should run all the important components that are present inside this components folder and whatever components are specifically using the functionalities from utils, that it will be accessed from here, like after importing it will be able to do it. So this is a generic folder structure that I’m actually going to use, okay.

Now after pipeline there are some more things that I really want to create, because here we are also going to have something like "entity", then entity config. Entity basically means configuration details. I will talk more about it, but right now we are still focusing on following a generic folder structure. Then we’ll be defining constants inside this "constants". If I really want to go ahead and define any constants, it will be created over here, right. And here is my constructor file. See, I can also use this particular file and define things over there. But I will show you once I probably go ahead and start the coding, okay. Now these are all folders. This is a generic folder structure that I’ve actually created.

Now what I’m actually going to do is that I’ll also go ahead and create some more files. One will be my "config.yaml", okay. This config folder along with the "config.yaml" will have all my configuration details. If any parameters are required for my machine learning training, I’ll be writing inside this particular YAML file. The reason why I’m creating the YAML file is so that I will be able to read all the configuration directly from this YAML file, okay—a very generic structure which is basically used in any project. Then this is "schema.yaml", one more file that I’m actually going to create. Then we have this "main.py" which will be my file. Along with this I’m also going to go ahead and create my "Dockerfile". Along with this Dockerfile, I also require a "requirements.txt". But this file is already created, so I don’t want to create it again. But in a generic way, if you want I can go ahead and write my "requirements.txt" here, okay. So it is up to you whether you want this. There will be one more file that I really want to create, it is "setup.py". Okay "setup.py". This setup.py I will talk about the importance of this because it actually helps you to create your entire project as a package. You know, let’s say you want to probably deploy an entire package into a PyPI environment, right? PyPI where most of the libraries we specifically download from. Then this "setup.py" file will be very, very much handy.

Along with this, I also want to create one "research" folder so that I go ahead and play with Jupyter Notebook, okay. So here I will go ahead and create "research.ipynb", okay. Done. Then you have this "templates" folder. Since I’m using Flask, I’ll be using this "index.html", okay. So almost all the folder structure is done, so I will just go ahead and close this, okay. So these are all the files that I’m going to create, folders that I’m actually going to create. So whenever I write "config/config.yaml" this becomes a folder and this becomes my file, okay.

Now the next thing is that okay, I have all this list of files. Now how do I create this? So for this I will be writing a specific code, okay. Now what will be the code that I will be writing? I will go ahead and write "for file path in list of files:". Okay, let me just go ahead and define "file_path =". So for every file we are going to take this entire, this—we are going to use this library called "path". And this path with respect to this particular project is going to create that particular path. So I’m just going to go ahead and define my file path over here. Now you know that inside my file path, if I keep on splitting, right, like this "///". If I keep on splitting it, right, so if I keep on splitting, I may get my file directory along with my file name, okay. So if I’m splitting it "os.path.split(file_path)". So just try to understand what we are specifically doing over here. I’m just trying to take out my file name along with my file path, that’s it, okay.

So here I’ll write a condition "if file directory != ''", okay. Then I will say "os.makedirs(file_dir, exist_ok=True)". So this is a generic code that can actually run in Linux, in Windows, or in Mac. So that is the reason I’m writing this specific code, right. Whether you are implementing this in your Mac machine or your Linux machine, it will work for each and everything. So here I’m going to use "os.makedirs(file_dir, exist_ok=True)". That basically means if the file exists do not make it, okay. Then, let me do one thing, let me also add a logging over here so that I should be able to see the logging. So first of all, in the case of logging—see logging, exception handling, these are something like a prerequisite for all of you, okay. So here I’m going to write "logging.basicConfig(level=logging.INFO, format='%(asctime)s - %(message)s')" and once I probably go ahead and create my directories, I’m going to go ahead and write "logging.info(f'Creating directory {file_dir} for the file {file_name}')" okay.

So this is what we are basically doing. If the file directory value is not empty, we are just going to go ahead and create the directory in short, okay. Then I’m just going to put one more condition. Okay I will go ahead and write "if not os.path.exists(file_path)". If that file path does not exist, then we’ll get the size of the file path. If the file path is equal to zero, okay, then what we are basically going to do, if the file path does not exist and if the file is not available, we will "open(file_path, 'w') as f: pass". And then we are going to create that particular file, right. We are going to probably create the file or any kind of operation that we want to do, we can do it over here. So I’ll just write "pass" because I don’t want to put any content over there, right. The reason is very simple because I don’t have any content to put, I just want to create the file itself, okay. So here you will be able to see as soon as I write "pass", after pass I will basically go ahead and write "logging.info(f'Creating empty file {file_path}')" okay.

Now in the else block I’ll go with the next step wherein I’ll be writing "logging.info(f'{file_name} already exists')" so if it does not exist, then only the upper condition will get executed. Perfect. So I have written the code for my entire "template.py", and I have automated this entire process. In the upcoming projects also you’ll be seeing that I’ll try to create manually also, so there also you’ll be getting a good understanding, but just by writing this "template.py", now I should be able to probably go ahead and create my entire project structure, okay.

Now in order to do this, I will just go ahead and open my terminal, okay. And here, in order to run this "template.py", just save this file, okay. And one more very important thing guys: just go ahead and click over here, save, okay, save. You can probably do a save over here, and just look for an option wherein whenever you write a code it should automatically save, okay. So I think it is somewhere over here, I will show you that particular option probably in the next video, but I have already kept that particular option. Save control S. You can also do a save as, okay. Save all, okay. I think there is one option, I’ll show you as we go ahead, okay.

So till here I hope everybody is clear. And now what I will do in order to execute this, I will just go ahead and write "python template.py". Now see, see the magic? Nothing is over here, I will go ahead and execute it, now my entire file should get created. See, all the folder structure is ready—my "template.py", my "setup.py", my "main.py", my "Dockerfile", "params.html", templates, source, all the components, config "__init__.py", config "configuration.py", constants, entity, pipeline, utils "common.py", everything is basically getting created, research "research.ipynb", config "config.yaml", get workflows, everything is basically getting created over here, okay. Now just by writing this one "template.py" file, I am able to create it.

Now let’s see whether it will work or not, okay. So I’ll go ahead and update one more file which is like "app.py", okay. So I want also "app.py". And now let’s go ahead and execute it. Now let’s see only the "app.py" file will get created or will everything get updated. So once I execute it, here you can see created empty file this, this, this and my entire "app.py". Also, I think I should be able to see it over here. So this is my "app.py", okay. So right now I’ll just go ahead and delete it, I don’t require it, okay. Perfect. So this is how we go ahead and create our entire folder structure just by writing some lines of code, you know, in the "template.py", and I’m able to do it.

Now I’ll go ahead and commit this "git add ." "git commit" and I will just go ahead and write a message saying that hey, my project structure is ready, "Project structure". Okay, now you may be thinking Krish, why you are using this technique. See, there are also different different extensions like source control and all, right. And you can directly use that and you can probably see this is source control, source control. I think the source control using source control also you can directly commit the code. But I don’t want to use that. I want to specifically make sure to show you how I’m committing each and everything, okay. And that is the best way to learn something, okay. So here after I have committed, I will go ahead and write "git push origin main", okay. So this is the push that is going on. And now I think it should be updated in my GitHub repo. So see this, my entire file has been updated. Perfect. So I hope you like this particular video. Now in the next tutorial I’m going to go ahead and talk more about different different files like "setup.py".

**Summary:**

**What was done in the project setup section:**

Created GitHub repository (data_science_project)

Initialized with README.md and license.

Cloned repo locally for development.

Created .gitignore file

Excluded venv/ and other unnecessary files from version control.

Set up Python environment

Created a conda environment → keeps dependencies isolated.

Installed required packages from requirements.txt.

Added requirements.txt

Listed dependencies like python-box, PyYAML, joblib etc.

Installed them with pip install -r requirements.txt.

Created template.py

Python script that auto-generates folder and file structure.

Runs os.makedirs to create directories.

Ensures consistent and clean project skeleton for all modules.

Executed template.py

Generated folders like src/, logs/, notebooks/, etc.

Verified clean folder structure.

Git workflow

Staged (git add .), committed (git commit -m), and pushed (git push origin main) the changes.

**Why each is needed:**

GitHub repo → Centralized code hosting, collaboration, and version control.

.gitignore → Prevents unnecessary/large files (e.g., venv, cache, data dumps) from cluttering the repo.

Conda environment → Isolates dependencies, ensures reproducibility across machines.

requirements.txt → One-click installation of all dependencies, standard practice for reproducibility.

template.py → Automates project scaffolding; avoids manual folder creation; ensures consistency in structure for every new project.

Logs folder (from template.py) → Placeholder for logging system, useful for monitoring runs.

Git add/commit/push → Tracks progress, keeps repo up to date with latest code changes.

In short: This section established the foundation of the project by setting up version control, environment management, dependencies, and a clean automated folder structure.

### Fully created template.py and when he ran using "python template.py" everything got created; Every folder got created automatically

**2. Custom Logging Implementation**

Hello guys. So, we are going to continue our discussion with respect to our end-to-end project. In the previous video, we already created the entire folder structure. There was one topic that I really wanted to talk about, which was related to the setup.py file. Okay, I’ll keep this topic for later. I won’t discuss it right now, but in the upcoming project, I’ll specifically be discussing why we exactly use setup.py. The reason is very simple—because this setup.py, let’s say you want to create your entire project as a package, you can probably use it. But I don’t want to dive deep into it right now, since this is your very first project. Usually, we discuss this when you really want to package your entire project and put it into PyPI. As we move ahead in upcoming projects, we will see more about setup.py. For now, I’ll just keep it empty.

Now let’s do one thing. Let’s go ahead and start working on the logging part. Inside my source folder, I have data_science, and there is an __init__.py file. I could also create a separate folder called logging, and inside that I could add an __init__.py. But instead, what I’ll do is just open the existing one, and inside this I’ll go ahead and set up my logging.

In order to set up logging, we’ll also make sure to test it. So first, I’ll import the required modules. "import os\nimport sys\nimport logging". Now, for the logging, we’ll be using a generic logging structure so that we can log every detail across all files. This way, you’ll see all the information related to the pipeline execution.

The first thing to think about is what kind of message format and file name we should create. So, I’ll create a variable called logging_str, and inside this I’ll define a format like this: "logging_str = '[%(asctime)s] %(levelname)s %(module)s - %(message)s'". This basically represents the time, the level name (whether it’s INFO, WARNING, etc.), the module name (for example, if I’m in the components folder, that module name will be shown here), and the message I want to display.

Next, I’ll create my logging directory. So, "log_dir = 'logs'". Then I’ll create a log file path: "log_file_path = os.path.join(log_dir, 'running_logs.log')". What I’m doing here is joining my logging directory with the file name running_logs.log to create the full path.

Now, in order to make this folder, I’ll write "os.makedirs(log_dir, exist_ok=True)". This ensures that the directory is created if it doesn’t already exist.

After this, I’ll configure the logging using basicConfig. So "logging.basicConfig(level=logging.INFO, format=logging_str, handlers=[logging.FileHandler(log_file_path), logging.StreamHandler(sys.stdout)])". Here, I’m setting the level as INFO, using my defined format, and adding two handlers.

The first handler is "logging.FileHandler(log_file_path)". This ensures that the logs get written to a file. The second is "logging.StreamHandler(sys.stdout)", which ensures that the logs also show up in the terminal. You might wonder why both are needed. The stream handler with sys.stdout ensures that if I run the code in the terminal, I’ll see the log messages printed there, while the file handler stores them in the log file.

Once that’s done, I’ll initialize the logger using "logger = logging.getLogger('data_science_logger')".

Now, let’s test whether everything works properly. For that, I’ll open my main.py file. Inside this file, I’ll import the logger from my data_science package: "from src.data_science import logger". Then I’ll simply call "logger.info('Welcome to our custom logging for data science')".

Next, I’ll run this code from the terminal. I need to be inside my data science project folder, and then I’ll run "python main.py". When I do that, I should be able to see the log message both in the terminal and in the log file.

For example, in the terminal, the output looks like this: the time is shown, then the level name INFO, the module name (which is main in this case), and finally the message: Welcome to our custom logging for data science.

If I check the logs folder, I’ll also find a running_logs.log file where the same information is stored.

So this was all about the logging functionality. Now, exception handling is another important concept. Yes, we also need to implement exception handling, but don’t worry about it right now. In the requirements.txt, I’ve already included a package called python-box. Many people might not know about this, but we’ll try to implement exception handling with the help of Python Box. You may be thinking—shouldn’t we implement a custom exception class? Yes, we will do that as well, but you’ll see that example in the next project. For this one, I just wanted to show you something new so you enjoy learning these concepts.

So, I hope you liked this video. This was about logging. Now, I’ll just open my terminal and quickly do a git commit. First, I’ll run "git add ." to add all the files. For now, I’ll delete the separate logging folder because I don’t want it anymore. Then I’ll commit the changes with "git commit -m 'Added logging functionality'". After that, I’ll push the changes using "git push origin main". And yes, it has been successfully pushed.

Now, if you check inside my GitHub repo under source/data_science, you’ll see that the updates are there in my __init__.py. So yeah, the code is updated.

In the next video, we’re going to look at some more things—specifically the utils part. We’ll see what common functionalities we can write inside common.py. That’s what we’ll work on next.

So yeah, this was it. Thank you, and I’ll see you in the next video.

**Summary:**

What was done in the logging section:

Created logging setup inside src/data_science/__init__.py.

Imported required modules: os, sys, logging.

Defined log message format:

Time → %(asctime)s

Log level (INFO/WARNING/ERROR) → %(levelname)s

Module name → %(module)s

Message → %(message)s
Example format: "[2025-09-06 10:30:12] INFO main - Welcome to logging".

Created logs directory (logs/) and log file path (running_logs.log).

Ensured directory creation with os.makedirs(log_dir, exist_ok=True).

Configured logging with logging.basicConfig:

FileHandler → writes logs into running_logs.log.

StreamHandler(sys.stdout) → prints logs in the terminal.

Both together ensure logs are saved and visible during execution.

Initialized custom logger: logger = logging.getLogger("data_science_logger").

Tested logging in main.py:

Imported logger → from src.data_science import logger.

Logged a test message → logger.info("Welcome to our custom logging for data science").

Verified logs appeared both in terminal output and inside logs/running_logs.log.

**Why each is needed:**

Logging format → Provides structured, detailed logs (time, level, module, message).

Logs directory & file → Keeps a persistent history of pipeline runs.

FileHandler → Saves logs for later debugging & auditing.

StreamHandler → Displays logs live in the terminal.

Custom logger → Centralized logging, reusable across the entire project.

Testing → Ensures logging works correctly before integrating into other components.

**Additional Notes:**

setup.py: Introduced briefly (for packaging projects), but postponed for later projects.

Exception handling: Mentioned as important, will explore with Python Box & custom exceptions in future projects.

Git workflow: Demonstrated git add ., git commit -m, git push origin main after implementing logging.

In short: This video set up a robust logging system to track project execution, making debugging and monitoring much easier.

#### Wrote Logging Code in "src/datascience --> __init__.py" and used that in "main.py"

**3. Common Utilities Functions Implementation**

Hello guys. So we are going to continue our discussion with respect to our end-to-end project. In the previous video, we implemented the logging functionality. Now you know how we can go ahead and create our custom logs.

In this video, I’m going to discuss the utils section, where I have a file called common.py. Some of the common functionalities that will be used across the project will be written here.

First, let me import the libraries:
"import os\nimport yaml\nimport json\nimport joblib\nfrom src.data_science import logger\nfrom ensure import ensure_annotations\nfrom box import ConfigBox\nfrom box.exceptions import BoxValueError\nfrom pathlib import Path\nfrom typing import Any"

I’m using YAML because we’ll have multiple YAML files in our project—for example, params.yaml will contain parameters, and to read them, we need this library. I’m also importing our logger that we created earlier inside __init__.py. Then I’m adding json for saving/loading data, and joblib for model serialization (saving/loading models in .joblib format).

Along with these, I’m importing ensure_annotations (a very useful decorator) and ConfigBox from the box library. ConfigBox will help us treat dictionary keys like attributes, which I’ll explain with an example. Finally, I’m importing Path and Any for type handling.

Now let’s define one common function called read_yaml. Here’s the code:
"@ensure_annotations\ndef read_yaml(path: Path) -> ConfigBox:\n try:\n with open(path) as yaml_file:\n content = yaml.safe_load(yaml_file)\n logger.info(f\"YAML file: {path} loaded successfully\")\n return ConfigBox(content)\n except BoxValueError:\n raise ValueError(\"YAML file is empty\")\n except Exception as e:\n raise e"

This function takes the path to a YAML file, reads it using yaml.safe_load, logs success, and returns the contents wrapped in a ConfigBox. If the file is empty, we raise a BoxValueError. This makes YAML handling cleaner and safer.

Now why do we need ConfigBox? Let’s say I have a dictionary:
"example = {\"key1\": \"value1\", \"key2\": \"value2\"}". Normally, to access value1, I’d write example["key1"]. But if I try example.key1, it will throw an error, since dictionaries don’t support dot notation. If I wrap it with ConfigBox like "example = ConfigBox(example)", then I can directly call example.key1 and get value1. This is super helpful when working with YAML configs, because we’ll have lots of them (schema.yaml, params.yaml, config.yaml), and dot-notation access is much cleaner.

Now let’s talk about ensure_annotations. It enforces that the function arguments and return types match the annotations. For example:
"@ensure_annotations\ndef get_product(x: int, y: int) -> int:\n return x * y"

If I call get_product(2, 4), it works fine. But if I accidentally call get_product(2, "4"), normally Python would happily multiply and return '44'. With ensure_annotations, it will raise an error because y is expected to be an int, not a string. This makes type checking strict and avoids subtle bugs in big projects.

Now, besides read_yaml, let’s add more generic functions:

create_directories
"@ensure_annotations\ndef create_directories(path_to_directories: list, verbose=True):\n for path in path_to_directories:\n os.makedirs(path, exist_ok=True)\n if verbose:\n logger.info(f\"Created directory at: {path}\")"

This function creates a list of directories.

save_json
"@ensure_annotations\ndef save_json(path: Path, data: dict):\n with open(path, \"w\") as f:\n json.dump(data, f, indent=4)\n logger.info(f\"JSON file saved at: {path}\")"

Saves any dictionary to a JSON file.

load_json
"@ensure_annotations\ndef load_json(path: Path) -> ConfigBox:\n with open(path) as f:\n content = json.load(f)\n logger.info(f\"JSON file loaded successfully from: {path}\")\n return ConfigBox(content)"

Loads JSON data and returns it as a ConfigBox so we can access keys easily.

save_bin (for models)
"@ensure_annotations\ndef save_bin(data: Any, path: Path):\n joblib.dump(value=data, filename=path)\n logger.info(f\"Binary file saved at: {path}\")"

This saves a serialized object (like a model) into a .joblib file.

load_bin
"@ensure_annotations\ndef load_bin(path: Path) -> Any:\n data = joblib.load(path)\n logger.info(f\"Binary file loaded from: {path}\")\n return data"

Loads the serialized object back.

So overall, in common.py, we now have functions for reading YAML, creating directories, saving/loading JSON, and saving/loading models. These utilities will be reused throughout the project.

That was the explanation of the utils section. We introduced the important libraries, explained ConfigBox and ensure_annotations, and added a set of generic, reusable functions. I hope this makes sense. I’ll see you all in the next video. Thank you and take care.

### From src.data science, imported Logging;  joblib - Saving Model; 

### datascience --> utils --> common.py --> read_yaml; Wrote YAML Codes

### Went to research folder, and tried about ConigBox; For dict, dict[value1] works while dict.value1 doesn't; So similar to support it, as many YAML Files has key-value pairs, we used ConfigBox; So that we can read any keys specifically 

### When int, what if we gave it as str, we raised an exception from "ensure_annotations" (We say whatever data type I am excepting, it should get it)

**Summary:**

**What was done in common.py (utils section):**

Imported essential libraries:

os → for creating directories.

yaml → to read YAML config files.

json → for saving/loading JSON files.

joblib → for saving/loading serialized models.

logger → custom logger created earlier.

ensure_annotations → to enforce type checking.

ConfigBox (from box) → to access dictionary keys with dot-notation.

Path, Any → type hinting.

Created utility functions:

read_yaml → Reads YAML safely, logs success, returns as ConfigBox.

create_directories → Creates multiple directories, logs creation.

save_json → Saves dictionary as JSON file.

load_json → Loads JSON, returns as ConfigBox.

save_bin → Saves binary objects (e.g., ML models) using joblib.

load_bin → Loads binary objects back.

Why each is needed:

YAML support → Project will use multiple YAML configs (params.yaml, schema.yaml, config.yaml).

ConfigBox → Enables dot-notation (config.key1) instead of dictionary-style (config["key1"]), making config handling cleaner.

ensure_annotations → Strict type checking, prevents silent bugs (e.g., string passed instead of int).

Logger → Standard logging for better debugging & traceability.

create_directories → Ensures required project folders exist before saving files/models.

save/load JSON → For persisting intermediate results, metadata, or configs.

save/load bin → For persisting ML models or other objects in .joblib format.

In short: common.py is the utility hub for configuration management, logging, directory handling, and saving/loading data & models — all reusable across the project.

**4. Step By Step Building Data Ingestion Pipeline - Part 1**

Hello guys.

So we are going to continue our discussion with respect to our end-to-end project. Till our previous video, we have developed all the common functionalities, and it is available in common.py file. If you remember, this particular file is available in the utils folder. Right. Then we also discussed what exactly is this config.yaml and along with that, we saw what ensure_annotation is.

Now, what we are going to do is that I will just go ahead and close all these files. Okay. And let me just go ahead and open the Readme file because here we are going to work on an end-to-end data science project. Right. We are specifically working on this, and here we are going to use extreme modular coding, you know, like how we specifically do the coding and how we build projects in the industry.

First of all, the most important thing now is about workflows. Workflows mean ML Pipeline. Now we are going to start building our ML pipeline. For all those who have some basic understanding of the life cycle of a data science project, the first step is nothing but data ingestion, right? And we have discussed this many times. Second is data transformation. Third is model trainer. Then we have model evaluation. So, let's consider these four important modules which are really important in any data science project or any end-to-end data science project that we specifically work in. All these modules need to be created in the form of a pipeline so that it runs one after the other.

The main part that I really want to teach in this video and in the upcoming videos is how we can go ahead and design each specific module in a much more modular way. See, I can just open a Jupyter notebook and write code for data ingestion, data transformation, model training, or model evaluation. It will be very simple. But what does modular coding mean here? It is about how we can specifically use classes. That is why we have actually created additional folders like components and config.

Now, let me go ahead and write some generic steps that we will follow. In every workflow, every pipeline that we build, let's say we are building data ingestion, there are some steps that we will definitely follow. The first step while designing data ingestion is to update the config.yaml file. This file is about some important configurations that we basically require. If we consider data ingestion, it basically means reading some kind of data from somewhere. It can be a database, an API, or if an ETL pipeline is created, most of the time we will fetch that particular data from a data source like MySQL or MongoDB.

Whenever we are talking about data ingestion, we definitely require some inputs, like knowing the data source input from where we will be taking the data and how we will be ingesting it. Those kinds of information are updated in the config.yaml file.

The second step is about schema.yaml. schema.yaml is not used in data ingestion. There is also a step called data validation, which can come after data ingestion. In data validation, we need to check the schema of the input that we are getting because it is really important whenever we get new test data to test our model. That schema needs to be validated, and that is what we specifically do in data validation. So schema.yaml is not required for data ingestion but may be needed for data validation.

Similarly, there is something called params.yaml which is used for specific conditions where we need to provide parameters. These are the steps we follow in every workflow. After completing the third step, we go ahead and update the entity. I will explain this when we start working on data ingestion. Then we update the configuration manager in the config source. After that, we update the components, update the pipeline, and finally update main.py. Usually, we create two types of pipelines: one is the training pipeline, and one is the batch prediction pipeline. Similarly, we update main.py.

I know I’ve just listed down the points and you may be confused about how to start. Let me do it step by step. Let's say we are going to design our data ingestion. I will open the research folder and create a file 01_data_ingestion.ipynb. I am showing you in Jupyter notebook first so you get a clear idea, and later we will convert this into modular programming.

Before writing any code, I will import os using "import os". First, let's select the environment. After importing, we check the present working directory using "!pwd" and execute it. Here, you can see the directory is data_science_project, and I am inside the research folder. One thing to do is always execute the program from the main project folder. To go back, we use "os.chdir('..')" and then check "!pwd" again. Now we are in the data_science_project folder.

Now, let's go to the config.yaml file. Inside this file, the data ingestion pipeline requires some input. First, I will create a key "data_ingestion", and within this, I will define key-value pairs. The first parameter is "root_dir", which is the folder created after data ingestion is executed. This folder is related to artifacts, so I will also create "artifacts_root": "artifacts". Then I define "source_URL" which is the dataset URL, in this case, the wine quality dataset. The next parameter is "local_data_file", which defines where the zip file downloaded from the URL will be saved. Finally, "unzip_dir" defines where the zip file will be extracted, in this case "artifacts/data_ingestion".

After updating config.yaml, next is schema.yaml. Right now, schema.yaml is not required for data ingestion.

Next, in the notebook, I will import "from dataclasses import dataclass" to create a data class, and "from pathlib import Path" for handling paths. I will define the data class "@dataclass class DataIngestionConfig" and inside, I define "root_dir: Path", "source_URL: str", "local_data_file: Path", "unzip_dir: Path". This matches exactly with the keys defined in config.yaml. The difference between a data class and a normal class is that in a normal class, we often use self, whereas in a data class, we focus on assigning values to variables without functions.

This DataIngestionConfig will be passed to the data ingestion pipeline because it contains all the values read from config.yaml. After this step, we will go to the next one, which is updating the entity.

Now, if I probably go ahead and show you what exactly an entity is, okay, entity is something I will talk about. I’ll update it when I’m doing the modular coding. Right now, I’m updating everything in my Jupyter notebook so that you understand the flow.

The next step will be, after updating the entity, to update the configuration manager in source/config. Configuration manager—what does it basically do? Let me create a class called "class ConfigurationManager". Inside this configuration manager, the first thing I will write is an init function "def __init__(self, config_file_path)". Here, the parameter is self along with config_file_path which is the path to my config YAML file. Whenever I load this configuration manager, whatever is in my config, schema, and params should be loaded already because for every pipeline that information will be available.

To make it simple, I create a constant "CONFIG_FILE_PATH". You may be thinking, where is this defined? Go to the project folder, inside source there is constants. Inside constants, I define all the paths: config path, params path, and schema path. I import "from pathlib import Path" and set "CONFIG_FILE_PATH = Path('config/config.yaml')". Similarly, I define PARAMS_FILE_PATH and SCHEMA_FILE_PATH.

Now, to call this, I import it using "from source.data_science.constants import *". By importing *, all constants like CONFIG_FILE_PATH, PARAMS_FILE_PATH, and SCHEMA_FILE_PATH are available. In the constructor, I assign "self.config = read_yaml(CONFIG_FILE_PATH)". Similarly, "self.params = read_yaml(PARAMS_FILE_PATH)" and "self.schema = read_yaml(SCHEMA_FILE_PATH)". These read YAML files are functions already defined in "source.data_science.utils.common.py" along with a function to create directories.

Once these are loaded, the first folder that needs to be created as soon as the data ingestion pipeline runs is the artifacts folder. So I call "create_directories([self.config['artifacts_root']])". This basic configuration manager ensures that whenever my data pipeline is running, like data ingestion, the artifacts folder is created first.

To initiate data ingestion, I need all configuration details of the data ingestion itself. I create another function "def get_data_ingestion_config(self) -> DataIngestionConfig". Remember, DataIngestionConfig was already defined earlier. This function returns all the field values of the data ingestion configuration, like root directory, source URL, local file path, and unzip directory. I extract the config using "config = self.config['data_ingestion']" and create directories using "create_directories([config['root_dir']])". Then I return "DataIngestionConfig(root_dir=config['root_dir'], source_URL=config['source_URL'], local_data_file=config['local_data_file'], unzip_dir=config['unzip_dir'])".

Now, this DataIngestionConfig will be passed to the data ingestion pipeline. We are reading the entire YAML file and returning all the information inside this class. This class is the data class we created.

Next, we need to update the components. The main component is the data ingestion component. I define it using "class DataIngestion" and the init function "def __init__(self, config: DataIngestionConfig)". I assign "self.config = config". Once I get the configuration details in data ingestion, I need to download the zip file from the GitHub URL. I define a function "def download_file(self)". Inside, I check "if not os.path.exists(self.config.local_data_file)", and then I use "urllib.request.urlretrieve(self.config.source_URL, self.config.local_data_file)" to download the file. I import "import urllib.request as request" for this.

Next, we define "extract_zip_file(self)". I import "import zipfile". Inside this function, I create the directory "os.makedirs(self.config.unzip_dir, exist_ok=True)", open the zip file using "with zipfile.ZipFile(self.config.local_data_file, 'r') as zip_ref:" and extract it "zip_ref.extractall(self.config.unzip_dir)". This ensures that the entire zip file is extracted to the specified path. Inside the zip, we have a CSV file with the dataset.

Now, we have implemented everything: the data ingestion config, the data ingestion component, and the functions to download and extract the zip file. To execute this, I write "config = ConfigurationManager()" to create the configuration manager. Then "data_ingestion_config = config.get_data_ingestion_config()". I create the component using "data_ingestion = DataIngestion(config=data_ingestion_config)". To run it, "data_ingestion.download_file()" and "data_ingestion.extract_zip_file()". This is wrapped in a try-except block "try: ... except Exception as e: raise e".

When executed, initially the artifacts folder is not present. After running, the YAML files are successfully loaded, directories created, the zip file is downloaded and extracted, and the data ingestion folder contains the CSV file.

Finally, in .gitignore, I include "logs" and "artifacts" to avoid committing them. This workflow successfully downloads and extracts the dataset, prepares directories, and completes the data ingestion step.

In the next video, we will convert this Jupyter notebook code into modular coding, showing exactly how to structure it across the project folders. We will also update Config.yaml, Schema.yaml, and the entity in source/entity. That’s all for this session.

**Summary:**

What Has Been Done

Common utilities (common.py) created

Functions like read_yaml, create_directories, etc. were implemented.

Needed so that repetitive operations (reading configs, creating dirs, logging) don’t get duplicated across modules.

Config system introduced

config.yaml → Stores pipeline-level configuration (artifacts root, dataset URL, file paths).

schema.yaml → Placeholder for data validation rules (column names, types).

params.yaml → Placeholder for model/training hyperparameters.

Needed because configs should be separated from code so changes don’t require code modification.

Data class created for ingestion config

@dataclass DataIngestionConfig holds values (root_dir, source_url, local_data_file, unzip_dir).

Needed because it provides a clean structure to pass configuration around instead of using loose dicts.

Configuration Manager implemented

Loads all YAML configs (config.yaml, params.yaml, schema.yaml).

Creates base artifact directories at runtime.

Provides methods like get_data_ingestion_config() to return a structured DataIngestionConfig.

Needed because each pipeline step should consistently load config and setup its required directories.

Data Ingestion Component built

download_file() → Downloads dataset (zip file) from source URL and saves locally.

extract_zip_file() → Extracts dataset into artifacts directory.

Needed because ingestion is the first step in ML lifecycle, ensuring raw data is available locally in a controlled structure.

Execution in Jupyter Notebook (research phase)

Demonstrated how configs are read.

Verified that artifacts folder is created, data.zip downloaded, and extracted.

Needed because before modularizing, you first prototype in notebook to confirm flow.

**Why This Flow is Needed (Big Picture)**

Industry-grade modular coding: Instead of messy Jupyter scripts, each part (config, entity, component, pipeline, main) is separated → easier debugging, scaling, productionization.

Reproducibility: Using YAML configs + entity classes means experiments can be re-run with same settings.

Extensibility: Adding more steps (transformation, training, evaluation) becomes systematic, as each will follow the same structure: update config → update entity → add component → wire into pipeline.

Automation: Pipelines can be triggered end-to-end (main.py) without manual notebook execution.

Industry practice: This is how real ML projects are structured for CI/CD and MLOps.

**In Short** - You have finished the foundation for Data Ingestion — configs, manager, entity, and component — and proved the workflow works by downloading + extracting the dataset.

**5. Data Ingestion Pipeline - Part 2**

We are going to continue the discussion regarding our data ingestion pipeline. In this video, whatever data ingestion we had written in the Jupyter notebook, we will now convert into modular coding, step by step.

First of all, the readme instructed us to update config.yaml. My config.yaml is already updated, as we have already seen. So, I can close all other unnecessary windows. The next step in the readme is to update the schema and params YAML. We don’t require that at the moment. The next step is to update the entity.

What does updating the entity mean? If you navigate to source/data_science/entity, there is a file called config_entity.py. Here, we need to import the data ingestion config that we initially created. This config contains the inputs for our data ingestion pipeline. Similarly, other pipelines like data transformation or additional components will have their own configs. This completes the first step: updating the entity.

The second step is updating the configuration manager in source/config. Inside config, there is a file called configuration.py. Here, we need to update the code to include the data ingestion config. To import it, we write "from src.data_science.entity.config_entity import DataIngestionConfig". We can also add additional configs later in the same import statement. This completes the second step.

Next, we update the components. The first component we create is the data ingestion pipeline. In source/components, I create a file called data_ingestion.py. Inside this file, I import the necessary libraries such as zipfile, urllib.request, and utilities from source/data_science/utils. I also import the data ingestion config using "from src.data_science.entity.config_entity import DataIngestionConfig". Once all imports are done, I define the class "class DataIngestion" with functions download_file() and extract_zip_file() to handle downloading and extracting the dataset zip file.

After creating the component, we update the pipeline. In source/pipeline, I create a file called data_ingestion_pipeline.py. First, I import the configuration manager, the data ingestion component, and the logger using statements like "from src.data_science.config.configuration import ConfigurationManager", "from src.data_science.components.data_ingestion import DataIngestion", and "from src.data_science import logger".

Inside this pipeline, I define the stage name "stage_name = 'Data Ingestion Stage'". Then I define the class "class DataIngestionPipeline". The constructor is empty for now, using pass. I also define a function "initiate_data_ingestion" where I initialize the configuration manager, get the data ingestion config, and execute the download and extraction steps. Finally, I call this pipeline using the if __name__ == "__main__": block, creating an object of the pipeline and running "obj.initiate_data_ingestion()".

To run the pipeline, I use main.py. From here, I import the data ingestion pipeline using "from src.data_science.pipeline.data_ingestion_pipeline import DataIngestionPipeline". Then I initialize and call the pipeline. Executing python main.py triggers the data ingestion stage, downloads the dataset, extracts the zip file, and creates the artifact folder containing winequality-red.csv.

In this way, we have successfully converted the Jupyter notebook implementation into modular code. The steps are now organized into entities, configuration, components, pipelines, and finally executed from main.py. The same structure will be followed for other modules such as data validation. Configuration, config_entity, and pipeline files will be updated accordingly for each new component. We can also run any specific pipeline directly, but using main.py ensures that all stages are executed sequentially.

This completes the data ingestion step. In the next video, we will explore additional pipelines and the subsequent steps for our end-to-end project.

**Summary:**

What Has Been Done
1. Updating the Entity

File: src/data_science/entity/config_entity.py

Task: Import DataIngestionConfig that holds inputs (root dir, dataset URL, local file path, unzip dir) for the data ingestion pipeline.

Purpose:
Entities act as structured containers for pipeline inputs. Each pipeline (ingestion, transformation, etc.) has its own entity. This separates configuration from implementation.

2. Updating the Configuration Manager

File: src/data_science/config/configuration.py

Task: Update ConfigurationManager to include methods to fetch DataIngestionConfig.

from src.data_science.entity.config_entity import DataIngestionConfig


Purpose:
The configuration manager centralizes loading configs from YAML files and ensures every pipeline can access its required configuration in a consistent and reusable way.

3. Updating Components

File: src/data_science/components/data_ingestion.py

Imports:

Standard libraries: zipfile, urllib.request, os

Utilities: from src/data_science/utils (e.g., read_yaml, create_directories)

Config entity: DataIngestionConfig

Class: DataIngestion

download_file(): Downloads the dataset zip file from the given URL.

extract_zip_file(): Extracts the downloaded zip file into the specified artifacts folder.

Purpose:
Components encapsulate specific tasks of a pipeline (here: downloading and extracting data), making them reusable and modular.

4. Updating the Pipeline

File: src/data_science/pipeline/data_ingestion_pipeline.py

Imports:

from src.data_science.config.configuration import ConfigurationManager
from src.data_science.components.data_ingestion import DataIngestion
from src.data_science import logger


Class: DataIngestionPipeline

Stage name: "Data Ingestion Stage"

Constructor: __init__() (empty for now, pass)

Method: initiate_data_ingestion()

Initialize configuration manager

Get data ingestion config

Execute download_file() and extract_zip_file()

Execution: Using the if __name__ == "__main__": block to run the pipeline.

Purpose:
The pipeline orchestrates multiple components in sequence, ensuring steps execute in order and can be reused in larger workflows.

5. Running the Pipeline via main.py

File: main.py

Task: Import and execute the pipeline:

from src.data_science.pipeline.data_ingestion_pipeline import DataIngestionPipeline

obj = DataIngestionPipeline()
obj.initiate_data_ingestion()


Outcome:

Downloads dataset zip

Extracts CSV into artifacts folder

Artifact folder contains winequality-red.csv

Purpose:
main.py serves as the entry point for the project, executing all stages sequentially.

**Why this structure is needed:**

Modular coding: Each part (entity, config, component, pipeline) is separated, making code maintainable and scalable.

Reusability: Components and configs can be reused across pipelines or projects.

Consistency: Pipelines follow the same structure, making onboarding and debugging easier.

Production-ready: The approach mimics industry-level end-to-end pipelines, preparing the project for CI/CD or MLOps deployment.

Flexibility: Can run specific pipelines directly or via main.py for sequential execution of all stages.

**The Jupyter notebook implementation is now fully modular, organized, and ready for extension to additional steps (data validation, transformation, training, etc.).**

**6. Complete Data Validation Pipeline Implementation**

We are going to continue the discussion with respect to our end-to-end project. In the previous tutorial, we implemented a data ingestion pipeline and saw how we could convert it into modular coding. From main.py, we are able to call each step, and based on this, we can create artifact folders. For example, the data ingestion folder is now displayed in the artifacts directory. Although I have not committed the code yet, it’s good practice to commit each module as you create it, especially in a company environment.

The next module we will focus on is data validation. Data validation is important because, once we train a model with a fixed set of input and output features, any new data for prediction should maintain the same feature names and data types. Otherwise, the model may not perform correctly. Data validation ensures that all features are consistent with a predefined schema, which we define in our YAML files.

To start, we follow similar steps as in the data ingestion module. We create a new Jupyter notebook called data_validation.ipynb in the research folder, select the appropriate kernel, and set the working directory to the main project directory using os.chdir().

Next, we update config.yaml with the necessary parameters for data validation. This includes a root directory for storing artifacts, an unzipped data directory for input datasets (from data ingestion, e.g., winequality-red.csv), and a status file (status.txt) to record whether the validation succeeded or failed.

Before creating the modular component, we read the dataset using pandas:

import pandas as pd
data = pd.read_csv("artifacts/data_ingestion/winequality-red.csv")


We then inspect the dataset using data.info() to determine the data types of each column. This helps us define the schema in schema.yaml, including the feature names, their data types, and the target column. Null values can be checked with data.isnull().sum(). Handling nulls is part of machine learning preprocessing, but for this module, we focus only on validation.

Once the schema is defined, we create the data validation config using a dataclass:

from dataclasses import dataclass
from pathlib import Path

@dataclass
class DataValidationConfig:
    root_dir: Path
    status_file: str
    unzip_data_dir: Path
    all_schema: dict


This config contains the root directory, unzip directory, status file, and the full schema dictionary. These inputs are required for the data validation component.

Next, we update the configuration manager (configuration.py) to include a function get_data_validation_config() that reads the data validation parameters from config.yaml and returns an instance of DataValidationConfig. This follows the same pattern used for data ingestion.

For logging, we import the logger:

from src.data_science import logger


We then define the data validation class. This class accepts the configuration and implements a function validate_all_columns():

Read the dataset from the unzipped directory.

Compare all dataset columns with the schema defined in all_schema.

If any column is missing, write False to status.txt.

If all columns match, write True to status.txt.

Return the validation status as a boolean.

This basic function ensures the column names match the schema. You can extend it to validate data types as an exercise.

After creating the component, we convert it into modular code by creating data_validation.py in the components folder. We import DataValidationConfig, pandas, and the logger. All functions from the notebook are now part of the Python module.

Next, we create a pipeline for data validation in data_validation_pipeline.py. Similar to the data ingestion pipeline, we import the configuration manager, logger, and data validation component. We define a class DataValidationTrainingPipeline with a function initiate_data_validation(). This function calls get_data_validation_config() and validates all columns, writing the result to status.txt.

Finally, we integrate the data validation pipeline into main.py. We import DataValidationTrainingPipeline and call initiate_data_validation(). Running python main.py executes the full pipeline: data ingestion followed by data validation. The status file in the artifact folder confirms the validation result.

Once verified, we commit the changes:

git add .
git commit -m "Data validation completed"
git push origin main


The .gitignore ensures logs are not tracked.

Following this approach, we have successfully implemented and modularized the data validation pipeline. The same methodology can now be applied to other pipelines such as data transformation, model training, and model evaluation. By following these steps, we ensure a clean, modular, and maintainable project structure focused on building machine learning projects.

**Summary:**

**What has been done:**

Purpose of Data Validation

Ensures that new input data for predictions matches the schema used during training.

Checks that:

All required feature names exist.

Data types are consistent (can be extended in future).

Avoids model failures due to schema mismatches.

Schema is defined in YAML files.

2. Creating Initial Notebook

File: research/data_validation.ipynb

Setup:

Select the appropriate kernel.

Set working directory using os.chdir().

Update config.yaml with:

root_dir (for artifacts)

unzip_data_dir (from data ingestion)

status_file (e.g., status.txt)

Read dataset:

import pandas as pd
data = pd.read_csv("artifacts/data_ingestion/winequality-red.csv")
data.info()   # Inspect columns and data types
data.isnull().sum()  # Check for nulls


Define schema in schema.yaml:

Feature names

Data types

Target column

3. Creating Data Validation Config

File: src/data_science/entity/config_entity.py

Dataclass:

from dataclasses import dataclass
from pathlib import Path

@dataclass
class DataValidationConfig:
    root_dir: Path
    status_file: str
    unzip_data_dir: Path
    all_schema: dict


Purpose: Stores inputs needed for validation, including root directory, schema dictionary, unzip directory, and status file path.

4. Updating Configuration Manager

File: src/data_science/config/configuration.py

Task: Add a method get_data_validation_config():

Reads parameters from config.yaml

Returns an instance of DataValidationConfig

Purpose: Standardized access to configuration for data validation, similar to data ingestion.

5. Creating Data Validation Component

File: src/data_science/components/data_validation.py

Imports:

DataValidationConfig, pandas, logger

Class: DataValidation

Method: validate_all_columns()

Read dataset from unzip_data_dir

Compare columns with schema in all_schema

Write True or False to status_file

Return boolean validation status

Purpose: Encapsulates the validation logic, making it modular and reusable.

6. Creating Data Validation Pipeline

File: src/data_science/pipeline/data_validation_pipeline.py

Imports: Configuration manager, logger, data validation component

Class: DataValidationTrainingPipeline

Method: initiate_data_validation()

Get DataValidationConfig via configuration manager

Call validate_all_columns()

Log and save result to status.txt

Purpose: Orchestrates validation as part of the end-to-end pipeline.

7. Integrating with main.py

Task: Add:

from src.data_science.pipeline.data_validation_pipeline import DataValidationTrainingPipeline

obj = DataValidationTrainingPipeline()
obj.initiate_data_validation()


Execution: Running python main.py:

Executes data ingestion

Executes data validation

Generates status.txt confirming validation result

8. Committing Changes

Commands:

git add .
git commit -m "Data validation completed"
git push origin main


.gitignore ensures logs and other unnecessary files are not tracked.

**Why this Structure is needed:**

Modularity: Each step has its own entity, config, component, and pipeline.

Reusability: Validation logic can be reused for other datasets or pipelines.

Consistency: Mirrors the structure used in data ingestion.

Maintainability: Easy to extend validation logic (e.g., checking data types, ranges, nulls).

Production-ready: Each pipeline can be run independently or as part of main.py.

**Result** : The Jupyter notebook implementation is now fully modular, the status file confirms validation, and the structure can be extended for further pipelines such as data transformation, model training, and evaluation.

**7. Complete Data Transformation Pipeline Implementation**

We are continuing our discussion on the end-to-end project. So far, we have implemented data ingestion and data validation. The data validation component is already created, and we have integrated the pipeline in main.py.

The next step is data transformation. In this stage, we perform tasks such as feature engineering and other data pre-processing steps. For this project, we won’t focus much on advanced feature engineering or missing value handling, as that falls under typical machine learning preprocessing tasks. Those topics will be covered in upcoming projects where we implement full end-to-end pipelines including feature engineering.

To implement data transformation, the first step is to open config.yaml and define input parameters for the data transformation configuration. Similar to data ingestion and validation, we need to provide a root directory and data path. We also need to create a data_transformation folder where the transformed data will be saved. For now, since our dataset is clean, we will simply perform a train-test split of the Wine Quality dataset and save the resulting train and test datasets.

Next, we go to the research folder and create a Jupyter notebook named 3_data_transformation.ipynb. We first import necessary libraries such as os and set the working directory to the main project folder. Then, we define the data transformation config using a dataclass similar to the one used for data validation. This config contains the root directory and data path parameters.

After defining the config, we update the configuration manager by adding a function get_data_transformation_config. This function reads the YAML file, creates required directories, initializes the data transformation config, and returns it.

With the configuration ready, we move on to the data transformation component. We import necessary libraries including pandas and train_test_split from sklearn. In the component, we define a function that reads the dataset, performs the train-test split, and saves the resulting CSV files in the configured directory. We also integrate logging to track the steps.

Once the component is ready, we integrate it into the pipeline. We create a file data_transformation_pipeline.py and follow a similar structure as other pipelines. The pipeline initializes the data transformation component, fetches the configuration, and calls the train-test split function. We also implement a try-except block to check the data validation status before running the transformation. If the status is not valid, an exception is raised, ensuring only validated data is transformed.

Finally, we update main.py to include the data transformation stage. We import the pipeline and call the function to initiate data transformation. After running main.py, the pipeline reads the validated dataset, performs train-test split, and saves the transformed data.

At this point, the data transformation folder contains train.csv and test.csv. All steps are modular, following the same structure used for data ingestion and validation. The next steps in the project will focus on model training and model evaluation, followed by deployment.

This process highlights the importance of maintaining a modular structure for reproducibility and ease of debugging. Each component—data ingestion, validation, and transformation—is clearly separated and integrated into a main pipeline, ensuring scalability for future projects.

**Summary:**

**What we have done:**

Purpose of Data Transformation

Prepares the dataset for machine learning tasks.

Includes basic preprocessing steps:

Train-test split

(Optional) Feature engineering and other preprocessing steps in future projects

Ensures clean, validated data is ready for modeling.

Only transforms data that passes the data validation stage.

2. Updating Configuration

File: config.yaml

Parameters for Data Transformation:

root_dir: Folder for storing transformation artifacts

data_path: Path to the validated dataset

transformed_data_dir: Folder where transformed train/test datasets will be saved

3. Creating Jupyter Notebook

File: research/3_data_transformation.ipynb

Setup:

Import necessary libraries (os, pandas, train_test_split)

Set working directory to the main project folder

Define data transformation config using a dataclass:

from dataclasses import dataclass
from pathlib import Path

@dataclass
class DataTransformationConfig:
    root_dir: Path
    data_path: Path
    transformed_data_dir: Path


Purpose: Stores paths and directories for data transformation outputs.

4. Updating Configuration Manager

File: src/data_science/config/configuration.py

Function: get_data_transformation_config()

Reads parameters from config.yaml

Creates necessary directories (transformed_data_dir)

Returns an instance of DataTransformationConfig

5. Creating Data Transformation Component

File: src/data_science/components/data_transformation.py

Imports: pandas, train_test_split, logger, DataTransformationConfig

Class: DataTransformation

Function: initiate_data_transformation()

Reads the validated dataset (data_path)

Performs train-test split using train_test_split

Saves train.csv and test.csv in transformed_data_dir

Logs all steps for reproducibility

6. Creating Data Transformation Pipeline

File: src/data_science/pipeline/data_transformation_pipeline.py

Imports: Configuration manager, logger, data transformation component

Class: DataTransformationPipeline

Function: initiate_data_transformation()

Checks data validation status before transformation

Raises exception if validation fails

Calls the DataTransformation component to split and save datasets

7. Integrating with main.py

Update main.py:

from src.data_science.pipeline.data_transformation_pipeline import DataTransformationPipeline

obj = DataTransformationPipeline()
obj.initiate_data_transformation()


Execution: python main.py

Reads validated dataset

Performs train-test split

Saves train.csv and test.csv in the transformation artifact folder

8. Output

Folder: artifacts/data_transformation/

Files:

train.csv

test.csv

**Why it is needed:**

Modular structure: Each component has its own config, component, and pipeline.

Reproducibility: All steps are logged and artifact paths are controlled by config.

Scalability: Easy to extend for feature engineering, scaling, or advanced preprocessing.

Validation check: Ensures only clean, validated data is transformed.

**Result:** The data transformation module is fully modular, integrated into the main pipeline, and produces separate train/test datasets ready for modeling.

**8. Model Trainer Pipeline Implementation**

We are going to continue our discussion with respect to our end-to-end project. So far, we have implemented data ingestion, data validation, and data transformation. Now, we will focus on the Model Trainer component.

The concept of the model trainer is straightforward: we are going to train our machine learning model. First, let’s create a new file named for_model_trainer.ipynb. As usual, we select the appropriate kernel. I recommend closing all other files to avoid confusion, keeping only the main.py, config.yaml, and data_transformation files open.

Next, we import os and set the working directory to the project root using os.chdir(). Confirm the working directory with os.getcwd().

Following the project structure, the first step is to update the config.yaml for the model trainer. We need to define a root directory under artifacts, along with train data path and test data path, which are outputs from the data transformation stage. Additionally, we define the model filename (e.g., model.joblib) to store the trained model. Joblib is used here as a serialization technique to save the trained model to disk. In future projects, we may also explore Pickle.

Once the configuration is updated, we define a data class for the model trainer. Using the @dataclass decorator, we create ModelTrainerConfig containing the following parameters: root_dir, train_data_path, test_data_path, model_name, alpha, l1_ratio, and target_column. Here, alpha and l1_ratio are parameters required for the Elastic Net algorithm. These parameters are specified in the params.yaml file. This approach allows us to manage algorithm hyperparameters separately from the configuration. The target_column comes from the schema.yaml.

Next, we implement the configuration manager. Here, we define the function get_model_trainer_config() which returns an instance of ModelTrainerConfig. The function reads values from config.yaml, params.yaml, and schema.yaml to initialize the configuration for model training.

With the configuration in place, we move to training the model. First, we import necessary libraries such as pandas, sklearn.linear_model.ElasticNet, joblib, and our logger. Using the model trainer config, we read the train and test datasets. Then we split the datasets into X_train, X_test, y_train, and y_test using the target column. We initialize the Elastic Net model with alpha and l1_ratio from the configuration and fit it on the training data. Finally, we save the trained model using joblib.dump() to the specified root_dir.

During initial testing, we encountered an error: “no such file or directory”. This was because the model trainer directory did not exist. We fixed it by creating the directory inside the configuration manager before training the model. After this fix, running the training script successfully created the model.joblib file under artifacts/model_trainer/.

The next step is to modularize the code. First, we update the entity by adding ModelTrainerConfig in config_entity.py. Next, we update the configuration manager to include the get_model_trainer_config() function. Then, we create the model trainer component as a separate file model_trainer.py under components. This component handles reading data, training the model, and saving it.

After updating the component, we create the model trainer pipeline in a new file model_trainer_pipeline.py under the pipeline folder. Here, we define a function initiate_model_training() that calls the configuration manager, initializes the model trainer, and triggers training. Finally, we integrate this pipeline into main.py just like previous stages (data ingestion, validation, and transformation).

Once everything is set, we test the pipeline by deleting the model_trainer folder and running python main.py. This successfully executes the data transformation stage and the model training stage, producing the trained model in artifacts/model_trainer/model.joblib.

After verifying functionality, we commit the code using Git:

git add .
git commit -m "Model trainer implementation"
git push origin main


In conclusion, the model trainer stage is now fully integrated and functional. The next step will be model evaluation, where we will use MLflow to track experiments and integrate with a remote repository like DAGsHub.

This completes the explanation of the model trainer implementation.

**Summary:**

**What we have done:**

Purpose of Model Trainer

Trains a machine learning model using the transformed dataset.

For this project:

Uses Elastic Net regression.

Saves the trained model to disk for future inference.

Ensures reproducibility and consistent model storage.

2. Updating Configuration

File: config.yaml

Parameters for Model Trainer:

root_dir: Directory under artifacts to store trained model

train_data_path: Path to train dataset from data transformation

test_data_path: Path to test dataset from data transformation

model_name: File name for the trained model (e.g., model.joblib)

File: params.yaml

Hyperparameters for Elastic Net:

alpha

l1_ratio

File: schema.yaml

Contains the target_column for model training

3. Creating Jupyter Notebook

File: research/4_model_trainer.ipynb

Setup:

Import libraries: os, pandas, ElasticNet, joblib, logger

Set working directory to project root

Confirm working directory with os.getcwd()

Define Config DataClass:

from dataclasses import dataclass
from pathlib import Path

@dataclass
class ModelTrainerConfig:
    root_dir: Path
    train_data_path: Path
    test_data_path: Path
    model_name: str
    alpha: float
    l1_ratio: float
    target_column: str

4. Updating Configuration Manager

File: src/data_science/config/configuration.py

Function: get_model_trainer_config()

Reads values from config.yaml, params.yaml, and schema.yaml

Ensures artifact directories exist (creates if missing)

Returns an instance of ModelTrainerConfig

5. Creating Model Trainer Component

File: src/data_science/components/model_trainer.py

Imports: pandas, ElasticNet, joblib, logger, ModelTrainerConfig

Class: ModelTrainer

Function: train_model()

Reads train and test datasets

Splits into X_train, X_test, y_train, y_test using target_column

Initializes Elastic Net with alpha and l1_ratio

Fits model on training data

Saves trained model to root_dir using joblib.dump()

Note: Directory must exist before saving the model (created in configuration manager).

6. Creating Model Trainer Pipeline

File: src/data_science/pipeline/model_trainer_pipeline.py

Imports: Configuration manager, logger, model trainer component

Class: ModelTrainerPipeline

Function: initiate_model_training()

Fetches ModelTrainerConfig from configuration manager

Initializes ModelTrainer component

Calls train_model()

Ensures that only validated and transformed data is used

7. Integrating with main.py

Update main.py:

from src.data_science.pipeline.model_trainer_pipeline import ModelTrainerPipeline

obj = ModelTrainerPipeline()
obj.initiate_model_training()


Execution: python main.py

Runs all prior stages: data ingestion → validation → transformation → model training

Saves trained model in: artifacts/model_trainer/model.joblib

8. Output

Folder: artifacts/model_trainer/

File: model.joblib (serialized trained Elastic Net model)

**Why it is needed:**

Modular structure: Config, component, and pipeline are separated for clarity

Reproducibility: Trained model saved with controlled paths

Scalability: Easy to swap in other models or algorithms

Integration: Works seamlessly with prior stages (data ingestion, validation, transformation)

**Result:** The Model Trainer stage is fully modular, integrated into the main pipeline, and produces a trained machine learning model ready for evaluation or deployment.

**9. Model Evaluation Pipeline Implementation**

We are going to continue our discussion regarding our end-to-end project. In the previous video, we implemented the Model Trainer. In this video, we will focus on the next pipeline: model evaluation. For model evaluation, I will use platforms such as MLflow and DAGs Hub. DAGs Hub serves as a remote repository to track everything, while MLflow will be used for experiment tracking.

The steps are similar to the model training pipeline, but this time we will focus on evaluation metrics. First, ensure that your DAGs Hub account is set up and connected properly. I will start by opening my browser and connecting DAGs Hub to my GitHub repository. I select the repository for the Data Science project, authenticate with my GitHub credentials, and connect it. Once connected, I can track experiments, version data, and version models through DAGs Hub.

Next, I need to configure my MLflow tracking URI, along with the username and secret access token from DAGs Hub. These are stored as environment variables so that all experiments are tracked on the remote repository. I then create a Jupyter notebook file called model_evaluation.ipynb and import the necessary libraries. I also verify my present working directory to ensure it points to the project folder.

I update the config.yaml file to include keys relevant to model evaluation: root_dir for storing evaluation artifacts, test_data_path for input data, model_path for loading the trained model, and metric_file to save evaluation metrics in JSON format.

After updating the configuration, I create a ModelEvaluationConfig data class containing all required parameters, including the target column from the schema and the MLflow URI. I also update the ConfigurationManager to include a get_model_evaluation_config method that reads the configuration and creates the necessary directories. This method returns a fully initialized ModelEvaluationConfig object.

The next step is implementing the model evaluation component. I create a class that calculates evaluation metrics such as RMSE, MAE, and R² score. I also include a method to log results to MLflow. The process involves reading the test data, loading the trained model, separating features and targets, computing predictions, calculating metrics, saving metrics as a JSON file, and logging parameters and metrics to MLflow. The model is optionally logged as an artifact depending on the tracking URI type.

After verifying this workflow in the notebook, we convert it into a modular component. This involves updating the entity folder with model_evaluation_config, updating the configuration manager to fetch evaluation config, creating a component file model_evaluation.py, and importing utility functions like save_json. Finally, I create the model evaluation pipeline in model_evaluation_pipeline.py, which imports the evaluation component, fetches the configuration, and executes the MLflow logging.

The main.py file is updated to include the model evaluation pipeline. The function initiate_model_evaluation is called in the main script, similar to other pipelines. Running the main script now executes the model evaluation, saves metrics as JSON, and logs all experiments to MLflow. This ensures that evaluation results are tracked remotely. Finally, I commit all changes to GitHub, ensuring sensitive keys are removed before deployment.

With this, the model evaluation pipeline is complete. In the next step, we will focus on implementing the training plus batch prediction pipeline.

**Summary:**

Purpose of Model Evaluation

Evaluate the trained machine learning model on test data.

Track experiments, parameters, and metrics using MLflow.

Use DAGsHub as a remote repository for versioning datasets, models, and experiments.

Key evaluation metrics: RMSE, MAE, R² score.

2. Setup DAGsHub and MLflow

DAGsHub:

Connects to GitHub repository

Tracks experiments, data versions, and model artifacts

Authenticate using GitHub credentials

MLflow:

Configure MLFLOW_TRACKING_URI, MLFLOW_USERNAME, MLFLOW_PASSWORD as environment variables

Tracks metrics, parameters, and artifacts remotely on DAGsHub

3. Updating Configuration

File: config.yaml

Parameters for Model Evaluation:

root_dir: Directory under artifacts for evaluation outputs

test_data_path: Path to the test dataset (from data transformation)

model_path: Path to the trained model (from model trainer)

metric_file: JSON file to save evaluation metrics

Schema: Uses target_column from schema.yaml

MLflow URI: Stored as part of the configuration

4. Creating Jupyter Notebook

File: research/5_model_evaluation.ipynb

Setup:

Import libraries: os, pandas, joblib, sklearn.metrics, mlflow, logger, json

Set working directory to project root

Define Config DataClass:

from dataclasses import dataclass
from pathlib import Path

@dataclass
class ModelEvaluationConfig:
    root_dir: Path
    test_data_path: Path
    model_path: Path
    metric_file: str
    target_column: str
    mlflow_uri: str

5. Updating Configuration Manager

File: src/data_science/config/configuration.py

Function: get_model_evaluation_config()

Reads values from config.yaml and schema.yaml

Ensures artifact directories exist

Returns a ModelEvaluationConfig object

6. Creating Model Evaluation Component

File: src/data_science/components/model_evaluation.py

Imports: pandas, joblib, sklearn.metrics, logger, json, ModelEvaluationConfig, save_json utility

Class: ModelEvaluation

Function: evaluate_model()

Load test dataset from test_data_path

Load trained model from model_path

Split features (X_test) and target (y_test) using target_column

Generate predictions

Compute metrics: RMSE, MAE, R² score

Save metrics to JSON file (metric_file)

Log parameters, metrics, and optionally model artifact to MLflow

Ensures experiment reproducibility and centralized tracking of evaluation results

7. Creating Model Evaluation Pipeline

File: src/data_science/pipeline/model_evaluation_pipeline.py

Imports: Configuration manager, logger, model evaluation component

Class: ModelEvaluationPipeline

Function: initiate_model_evaluation()

Fetch ModelEvaluationConfig from configuration manager

Initialize ModelEvaluation component

Call evaluate_model() to compute metrics and log to MLflow

8. Integrating with main.py

Update main.py:

from src.data_science.pipeline.model_evaluation_pipeline import ModelEvaluationPipeline

obj = ModelEvaluationPipeline()
obj.initiate_model_evaluation()


Execution: python main.py

Runs all prior stages: data ingestion → validation → transformation → model training → model evaluation

Saves evaluation metrics as JSON

Logs experiments to MLflow (remote tracking via DAGsHub)

9. Output

Folder: artifacts/model_evaluation/

Files:

metrics.json – Contains RMSE, MAE, and R² score

MLflow logs for experiment tracking

**Why it is needed:**

Modular structure: Follows the same entity → config → component → pipeline pattern

Experiment tracking: All metrics, parameters, and artifacts are logged via MLflow

Remote reproducibility: DAGsHub ensures versioned tracking of models and datasets

Reusability: Evaluation pipeline can be reused for new models or updated datasets

**Result:** The Model Evaluation stage is fully modular, integrated into the main pipeline, and tracks evaluation metrics remotely using MLflow and DAGsHub, ensuring reproducibility and maintainability.

**10. Training And Prediction Pipeline With Flask App**

We are going to continue the discussion regarding our end-to-end project. In the previous video, we implemented all the important modules required for this project. Alongside, we have been developing our pipeline and executing it through Main.py.

The pipeline in Main.py essentially serves as our training pipeline. It covers every step, from data ingestion to data validation, data transformation, model training, and model evaluation. Now, it’s time to create a prediction pipeline, which is crucial because our trained model is available as a model.joblib file in the artifacts folder, specifically inside the model trainer folder.

To implement this, we create prediction_pipeline.py. In this file, we first import the necessary libraries: joblib, numpy, pandas, and Path from pathlib. We then define a PredictionPipeline class, where the __init__ function loads the trained model using joblib.load. The predict function takes input data, passes it to the model’s predict method, and returns the predictions. This completes the prediction pipeline.

Next, we integrate this prediction pipeline with a Flask API to enable a front-end interface. We create app.py and import Flask modules (Flask, render_template, request) along with os, numpy, pandas, and our PredictionPipeline. We initialize the Flask app and define the home route (/) to render index.html, which will serve as our front-end form.

The index.html form is designed using Bootstrap and collects features such as fixed acidity, volatile acidity, citric acid, residual sugar, chlorides, free sulfur dioxide, total sulfur dioxide, density, pH, sulfates, and alcohol. Upon clicking the predict button, the form sends data to the /predict route.

In app.py, we define the /train route to execute main.py for training the pipeline. The /predict route handles form submissions, reads user inputs, reshapes them into the required array format, calls the prediction pipeline, and renders results.html to display the predicted output. A try-except block ensures proper error handling.

Finally, we run the Flask app with app.run(host="0.0.0.0", port=8080). Once running, we can navigate to the index page, train the model, input feature values, and view predictions. For example, based on given inputs, the predicted wine quality might be 2.82 on a scale of 0–7.

All code and logs are now ready. We can push the project to GitHub using standard Git commands (git add, git commit, git push) while excluding unnecessary folders like MLruns. This completes our end-to-end project, including both training and prediction pipelines. The next step will focus on model deployment.

This approach provides a complete hands-on understanding of creating an end-to-end data science project, integrating training, prediction, and front-end interaction.

**Summary:**

Purpose

Use the trained model (model.joblib) to make predictions on new data.

Provide a user-friendly front-end using Flask for input and output.

Separate training and prediction pipelines for modularity and reusability.

2. Prediction Pipeline

File: src/data_science/pipeline/prediction_pipeline.py

Imports:

import joblib
import numpy as np
import pandas as pd
from pathlib import Path


Class: PredictionPipeline

init():

Loads the trained model from artifacts/model_trainer/model.joblib using joblib.load()

predict(data):

Accepts input features as a DataFrame or array

Calls self.model.predict(data)

Returns predictions

Functionality: Encapsulates prediction logic and allows easy reuse in API or scripts

3. Integrating with Flask

File: app.py

Imports:

from flask import Flask, render_template, request
import os, numpy as np, pandas as pd
from src.data_science.pipeline.prediction_pipeline import PredictionPipeline


App Initialization: app = Flask(__name__)

4. Flask Routes

Home Route (/):

Renders index.html

Provides a form for user input of features:

fixed acidity, volatile acidity, citric acid, residual sugar, chlorides, free sulfur dioxide, total sulfur dioxide, density, pH, sulfates, alcohol

Train Route (/train):

Executes main.py to retrain the model pipeline

Ensures the latest model is available for prediction

Predict Route (/predict):

Handles form submissions

Reads feature values from the form

Converts inputs to a NumPy array with the correct shape

Calls PredictionPipeline.predict() to generate predictions

Renders results.html to display predicted wine quality

Includes try-except blocks for error handling

5. Front-End (Bootstrap Form)

index.html:

Collects all input features in a structured form

Submits data to /predict route

results.html:

Displays predicted output in a readable format

Example: Predicted wine quality = 2.82 (scale 0–7)

6. Running the Application

Command:

python app.py


Access: Navigate to http://localhost:8080 or server IP

Workflow:

Optionally train the model using /train

Input feature values on the form

Click Predict → view results

7. Project Structure

Training pipeline: main.py → executes all stages (ingestion → validation → transformation → training → evaluation)

Prediction pipeline: prediction_pipeline.py → called by Flask API

Front-end templates: index.html and results.html

Artifacts:

artifacts/model_trainer/model.joblib (trained model)

Logs for debugging

8. Version Control

Git commands:

git add .
git commit -m "Prediction pipeline and Flask integration"
git push origin main


.gitignore: Exclude unnecessary folders like MLruns and logs

**Why it is needed:**

Modular separation of training and prediction

User-friendly interface for interacting with the model

Can be extended for batch predictions or REST API integration

Ensures reproducibility and maintainability

**Result:** The Prediction Pipeline is now fully functional and integrated with a Flask front-end, completing the end-to-end project workflow. Users can train models, input feature data, and receive predictions in real-time, all in a modular and maintainable structure.

### **L) End To End Machine Learning Pipeline Using GIT, DVC,MLFLOW And DAGSHUB**

**1. Getting Started With Project Structure**

Hello guys.

Now in this module, I'm quite excited that we will be implementing our first end to end machine learning pipeline using DVC for data version control and even for model versioning. Along with that, we'll also be using MLflow for experiment tracking. Already in our previous video, we have seen that how we can actually work with DVC along with DAGs hub remote. But if you probably see DAGs hub right as a remote repository, it has three main important functionalities. You'll be able to track your code. You'll be able to even upload data datas to the DAGs hub, and you'll probably be able to do the versioning along with the model versioning itself. And finally, you'll also be able to log experiments with MLflow. If you have these three amazing capabilities, then obviously you can actually develop an amazing pipeline, you know, end to end machine learning pipeline where you can integrate with DVC. Along with that, you can integrate with MLflow and all, and that is what we are going to probably do in this particular project.

Now, what I will do, first of all, I will just go ahead and create a new repository. So let me just go ahead and click create a new repository. Now obviously you can also go ahead and create a repository in GitHub and probably do it. But I really want to create a repository directly over here. And I don't want to connect any repository from my GitHub itself. So first of all let's go ahead and create a blank repository. Uh so here I will be creating it. Here I will say, hey this is my machine learning pipeline okay. So I'm going to probably go ahead and create my machine learning pipeline, uh, machine machine learning pipeline or I'll just say pipeline. Okay. So this will basically be my project. So name will be this. I will just go ahead and create a repository.

Now as soon as I probably go ahead and create a repository. This is where I'm going to probably create my entire ML pipeline, which will be having data pre-processing, model training and evaluation. And based on that we will try to log experiments. We will try to also do data versioning, model versioning and many more things. Okay. So here, uh, this is what I really need to clean, uh, clone. Sorry. So if I go to my MLOps. Right. So there is a folder called as ML pipeline. Okay. So let me just go ahead and delete this okay. Because here I will just go ahead and do my git clone. So in this particular path again you can go ahead and create anywhere you really want right in whichever drives. But I have used this e I have just used this particular folder ML pipeline and this is where I'm actually going to create it okay.

So first of all, let's go ahead and open my command prompt. Inside my command prompt I'll go to my E drive. Then I'll go to CD this okay. Again if you have Linux go to your terminal. Just go to that particular path over here. And then we will just go ahead and clone this okay. So once we clone it you'll be able to see that this entire repository will be created. Right. So if I go to my folder back so this machine learning pipeline is over here okay. And you have this dot git folder because it is configured to this particular GitHub repository. Okay. Now if I go to my command prompt. So from here I will go ahead and start my project. So I will go ahead and write "code ." And this is where my VS code will open okay. So here you can see VS code is there.

Now first of all what we will do is that we will go ahead and commit at least something okay. And here we can go ahead and create my Readme file. So here what I will do I will just go over here, I will go to my machine learning folder. And let me just go ahead and create my Readme file. Now inside this Readme file, what I am actually going to do is that I'm going to provide you some information of the project that we are going to do, and we'll discuss about that particular project right now. Okay. So here is my project that we are going to perform. Okay.

So what is the project over here. So let me just go ahead and execute this and let me just see the preview open preview okay. So the project is nothing but data pipeline with DVC and MLflow for machine learning. The project demonstrates how to build an end to end machine learning pipeline using DVC. That is data version control for data and model versioning, and MLflow for experiment tracking. The pipeline focuses on training a random forest classifier on the Pima Indian Diabetes dataset, with clear stages for data pre-processing, model training, and evaluation. So in short, we are going to use DVC. We are going to use MLflow. We will train a model and we will follow this entire pipeline of data preprocessing, model training and evaluation.

The reason why I am solving this specifically in the DAGs hub, right. So here, uh, okay. First of all, uh, there was something called as data pipeline, you know, and here you can visualize the data pipeline, which is quite amazing in the DAGs repository itself. So what I will do, first of all, let me just go ahead and open my terminal. Okay. Open my command prompt. You can also work with git bash if you want. Now first of all what I will do. You know that I have added this readme file. Let me just go ahead and add this readme file and let me commit it. Then you will be able to see all the things. Okay, so let me go ahead and add it or not a GitHub repository. Why it is not because okay, just a second. I think I have opened my wrong repository.

Okay, so I will go back to my command prompt. So I'll say "CD ml pipeline". Right. So "CD machine learning pipeline". So inside this my git was there. Right. So if you see over here inside this my dot git was there. See this kind of simple issues may come. So don't worry. You need to probably go ahead and fix it. Okay. So now I'll go ahead and write "code ." open my VS code okay. Open my VS code. That is the reason I could not execute the git command. And I'm not going to edit this video because I want to see all those you I definitely want you all to see all those errors. So here I will go ahead and create my "README.md" file. Okay. And after this I will go ahead and paste this entire thing about my project. Okay. So this is the update that we are going to keep it in the Readme file. You can also go ahead and preview it okay. Open preview okay. And this is all steps we are basically going to perform.

Now let me quickly go ahead and open my terminal or let's open my command prompt. And here I will be adding "git add readme.md" file okay. And then I will say git. So after adding you know first time when we are setting up please make sure that you watch this. Okay. So after adding I need to go ahead and do the commit okay. First commit. So here I will just go ahead and write my sorry, I need to go to my VSCode and go ahead and write my first commit okay. After I probably do the first commit. Uh, then uh, I also need to probably go ahead and set this up. Okay. So here you will be able to see this. I will go ahead and set up my branch. The default branch will be "minus M main" okay. So this one. So we are going to go ahead and create a branch over here. And finally I will go ahead and push "git push minus u origin main". Okay. Like how we did in the get is almost all the steps are same.

So if you probably see this, if you have followed all these things, you will be able to see that I will be able to reload it. And it is asking me to generate an image for your project. I'll say no thank you. And here you can probably see that my readme file has got updated. And now this three main things are available over here, where you can upload the data into the DAGs of remote. You can probably log experiments with MLflow and all. Okay, now why I really want to create machine pipeline by using this, uh, remote repository because, uh, the best part about this is that there is something called as data pipeline. And this data pipeline is a complete version control data pipeline. Right. And this will be quite amazing here. You can probably track your data. You can track your code, you can track your model versions. You can even track different, different metrics using MLflow. And that is the reason I'm going to probably write this. And all the information about this project is given over here. Right. So anyhow, I will be giving you all these resources in the resource section of this particular module itself.

Okay. Now, once you have done this, the next step that we are probably going to do over here is that let's go ahead and create our new new environment. So first of all I'll write "conda create minus p v env python double equal to 3.10". And I'll say yes. Okay. Because since we are creating a complete machine learning pipeline, it is better that you have a separate environment. So that environment will be getting created over here V and V. And along with that I will have my "requirements.txt" file. Okay. Now inside this requirement dot txt file I will be making sure that I'll write all the libraries that I'm actually going to use. Okay. Uh, so all those things I'll specifically write in my requirements.txt file. Okay. So over here in the requirement dot txt file you will be seeing I will be using DVC dags hub scikit learn. MLflow. Okay, all these things will be getting added. And along with this, I also will be requiring one more library so that uh. And if you remember, in a previous project also we had imported that DVC, S3. Okay. So that will be able to upload in the DVC remote with respect to any data or models. Okay, so here we have this DVC, S3 okay. All these things is basically getting we need to install it in our environments.

Now in the next step we will be able to see that I will go ahead and first of all activate. So "conda activate Venv" okay. And from here I will go ahead and right "pip install minus r requirements.txt". So here you can see all the installations are specifically taking place. Okay. So here you can see the installation is basically taking place. That is good enough. Okay. Uh, one more file that I really want to create over here is nothing but ".gitignore". Okay? Because I don't want to track v and v folder because it is on my virtual environment. Okay. But anyhow, uh, as soon as we probably like any folder that you don't want to track, you can basically write it over here. Okay.

So once this is done, the next thing is that, uh, I will also go ahead since we need to start with our data pre-processing, we need to have some kind of data first. Right. As you will be seeing right now, I have still not spoken about ETL pipelines and how you can probably develop ETL pipelines because, uh, with the help of ETL pipelines, you will be able to probably create that data ingestion phase, you know, so that we will discuss in the later stages, because I need to probably teach you about airflow and all. So right now what I will do, I will just go ahead and create one folder data inside this folder I will go ahead and create raw data. So this is my raw data itself. And I will be taking a data set, as I said from the from the if you probably see over here in the Readme file, write preview readme, I've told you that we will be using this Pima Indian Diabetes data set. We'll talk more about this particular data set, what exactly it is and what exactly it does. Okay, so first of all, let me just go ahead and upload this particular data set. This is our data set is even available in Kaggle and all okay.

So if you see over here if I just go ahead and explore this particular data set, this data set has features like pregnancies, glucose, blood pressure, skin thickness, insulin BMI uh diabetes. Diabetes, pedigree function, age. Right. And your outcome is basically your output feature. So what you really need to do is that you need to design a model. You need to create a model which takes this input feature. And it should be able to predict the outcome. The outcome is 0 or 1, which is just saying that based on this feature, whether the person is going to have diabetes or not. Okay. Uh, that is what is the entire problem statement over here? Yeah. Uh, and based on this particular data set, what we will do is that we will create this entire pipeline. The pipeline will be created for data pre-processing, model training and then model evaluation. And within this entire pipeline, we will see that how you can use multiple MLOps tools like DVC, MLflow. You know how we can probably go ahead and use Dax hub remote, you know, to store each and everything. And when the model is created, how we can probably go ahead and do the model versioning and all right. So everything will be specifically included, uh, with respect to this okay.

So, uh, till now, I hope you have basically understood, you know, all the steps. Um, now what we are going to basically do is that now, see, I hope in the terminal. Also, if I go ahead and see the installation of the library is taking place and it is going to take some amount of time. But what we are basically going to do is in the next video is that I will go ahead and create even one source folder. Okay. Source folder. and along with the source folder, I will be creating one more file which is called as "params.yaml" file. So here I will also introduce you to this YAML file. Why? Why specifically we use this kind of YAML file. Uh and what kind of parameters we are going to specify over here. So that is the reason I'm actually creating this. And inside this source, uh, you know, I will be creating one first of all, one file which is called as "init.py". Because through this particular file, what we will be able to do is that we will be able to call it as a package. So I think the installation has been completed. So let me just go ahead and minimize this.

And inside this itself source "init.py" I will also go ahead and create my another file which is nothing but "evaluate.py". Okay. Uh evaluate dot pi is specifically for evaluation. Okay. Um, but we should always start with something called as "pre-process.py" okay. So pre-process is specifically for data pre-processing like from reading data to probably doing any kind of feature learning. Feature engineering will be probably creating in this. And then along with this I will also have my "train.py" file. Okay. So all these things are files has been created. Okay. This is the project structure. The basic project structure. Uh, to get started with this. Okay. So everything is ready now.

In the next video we will start with "pre-process.py". But before that we'll have "params.yaml". Like what all information I need to probably put up. Okay, so once I design this entire pipeline then I'll show you that how we can use DVC and MLflow for doing the model version, data version and probably the experiment tracking. Right. So yes, this was it. In this video we have done the entire project structure setup. Along with that we have created a virtual environment. We have spoken about the data. We have spoken about the project. Uh, and uh, yeah, we'll continue in the next video where we are going to probably create our entire pipeline, from data pre-processing to training to evaluation. So yes, this was it. I will see you in the next video. Thank you.

**Summary:**

**What is done:**

Project Setup in DagsHub

A new repository was created directly in DagsHub (instead of GitHub).

Initialized with Git and linked locally through cloning.

README file was added with project details.

First commit and push were made to set up version control.

Defined the Project Objective

Build an end-to-end ML pipeline using:

DVC (Data Version Control): for data & model versioning.

MLflow: for experiment tracking.

Dataset: Pima Indian Diabetes dataset (predict diabetes outcome from health features).

ML algorithm: Random Forest Classifier.

Environment & Dependencies Setup

Created a new Conda virtual environment (Python 3.10).

Added all required dependencies into requirements.txt (DVC, DagsHub, scikit-learn, MLflow, DVC-S3, etc.).

Installed dependencies.

Added .gitignore to avoid tracking virtual environment and unnecessary files.

Dataset Preparation

Created a data/raw folder.

Uploaded the Pima Indian Diabetes dataset with features like pregnancies, glucose, insulin, BMI, etc.

Project Structure Initialization

Created a src (source) folder with initial Python files:

__init__.py – package initializer.

preprocess.py – for data preprocessing & feature engineering.

train.py – for model training.

evaluate.py – for model evaluation.

Mentioned upcoming params.yaml file to store pipeline configurations (like parameters, paths, hyperparameters).

**Why it is needed:**

DVC with DagsHub: To version datasets, models, and pipeline stages, ensuring reproducibility and easy collaboration.

MLflow: To log experiments (metrics, hyperparameters, models) and compare results.

Virtual Environment: To isolate project dependencies and avoid conflicts.

Project Structure: To keep the code modular, maintainable, and ready for scaling.

Dataset Preparation: To provide raw input for the pipeline stages.

YAML Config File (params.yaml): To centralize pipeline parameters, making experiments more flexible and configurable.

**Result:** The session focused on setting up the foundation for an MLOps-driven ML project — preparing repo, environment, dependencies, dataset, and project structure — so that future steps (preprocessing, training, evaluation, versioning, and experiment tracking) can be implemented in a clean and reproducible way.

**2. Implemeting Data Preprocessing Pipeline:**

So we are going to continue the discussion with respect to our end to end ML pipeline using DVC and MLflow. Uh, already I have made this entire folder structure. Uh, in the previous video you have your data dot csv. We have also spoken about the problem statement, what we are going to solve.

Now in this entire pipeline the first important component is your data pre-processing. Uh, for that I have actually created this particular file. Then you have to train a model, and then you have to probably evaluate metrics. And during the stages in this pipeline, we will try to use multiple MLOps tools like DVC and MLflow.

DVC will be specifically used for data versioning, MLflow to log experiments, track experiments and do multiple things. Now first of all, uh, before we go ahead and start writing our code, we will go ahead and set our normal parameters, all the basic parameters that we are going to work with. Okay.

So inside this particular params dot YAML file, let’s say I will go ahead and write one parameter like "pre-process". Now for pre-process, what I will be doing is that I will, uh, you know, we will just use some key value pairs with respect to this and we’ll try to set up some parameters. Okay. And those parameters I’ll be just displaying in front of you like this.

So it is saying that, hey, your input data is given somewhere over here. This is the basic information that you have. After you process the particular information or process the entire data, the data should be saved in this particular folder. So your output will be over here. So this is just like I’m providing some parameters.

The input parameter will be nothing but "data/raw/data.csv". After you perform the pre-processing, then your output, probably any data that you really want to save, it needs to be saved in this particular folder. Okay. So, uh, that is the basic common information that I’m giving.

The main aim of parameters dot YAML is that I’m trying to provide some parameters over here. And these all parameters will be hard coded so that we can actually use it in our code. Now, similarly for our training data, you know, I will be creating some parameters again over here.

So first of all where my data is basically present. After processing, the data is basically saved over here. So this is the same path that we are going to use. After we train the model we need to save the model in this particular path name and with the help of this particular file name "model.pickle". So this will be the path where our models will be saved.

Then you have this random state value, number of estimators I’m going to take as 100, and "max_depth=5". So these are some basic parameters that I’ll be giving during my training phase. And in the pre-processing phase, since I need the input data and where my output data needs to be saved, all this information I’m actually providing it.

This is a very good way to start any projects because as you will be seeing as we go ahead, I will be creating this params dot YAML in different end to end projects and this will be very, very much like many parameters will be coming over here. Uh, this is just the beginning over here.

Right now, after we have set all the parameters and our params dot YAML file, I will first of all start with my "pre-process.py" file. Now in the pre-process dot py file, which is my first step, let me just go ahead and import some of the libraries: "import pandas as pd". Okay, along with this I will go ahead and import this. Okay, since we need to do the pre-processing.

Then in order to read the params dot YAML file, I will be importing "yaml" library. And finally I will go ahead and import "os" so that I will be able to set the path and all. Okay, now first of all I need to load all the parameters from the YAML file. So here we will go ahead and write the code.

So I’ll write load parameters from param dot YAML. Now here I’m going to create a variable called as "params". And we can use "yaml.safe_load()" and inside the safe load I will be using my "open()" function. Let me go ahead and define my YAML file so it is nothing but "params.yaml".

As soon as we load this, you know what key you really need to call. Since this is my pre-process dot py, I will just go ahead and call this particular key. Okay. So let me just quickly go ahead and write this, call this key where we are going to call this. Okay. This is nothing but my parameters that I’m actually going to get from this YAML file. That basically means I’ll be having this two keys: input and output information available over here.

Now in the data pre-processing step we will go ahead and create a function "pre_process(input_path, output_path)". So these are the two parameters that I will be giving. "input_path" will be having the data that is already present. Because on this particular data only I need to perform any pre-processing.

So what I will do: I will go ahead and write "data = pd.read_csv(input_path)". Initially I thought of setting "header=None" but then I realized we need to use the headers itself. So I’ll remove that. Okay. Then what I will do after this, I will quickly go ahead and write "os.makedirs(os.path.dirname(output_path), exist_ok=True)".

Because in the params dot YAML, I know that my data dot csv needs to be stored in "data/preprocessed". So obviously whatever is my output path, I need to create a folder with respect to that. So here I’m going to give my output path. And this output path will be provided with this feature only.

Then finally what I will do, I will just read this dataset and I will save it in the form of a CSV in my output path using "data.to_csv(output_path, index=False)". So finally, let me just go ahead and write "print(f'Pre-processed data saved to {output_path}')".

Now you may be thinking, Krishnan data pre-processing is not performing any feature engineering at all. Guys understand right. Right now I just want to show you we are starting from some point. Later on you’ll be seeing EDA, you’ll be seeing feature engineering, you’ll be seeing multiple things as we go ahead.

But right now, if you really want to perform any feature engineering here, you can perform it before you save it into CSV. Right now I know that most of this particular data does not have any null values, it has numerical values, so I’m actually going to use this. Just to show you that how the pipeline is basically created. This will give you a super cool idea with respect to this.

So this is my pre-process dot py. Now if I go ahead and execute "if name == 'main':", I will first of all call my pre-process over here. So my pre-process function will be called as "pre_process(params['input'], params['output'])".

Because when I’m loading this params on pre-process, if you see in the param dot YAML you have your input key and your output key. You need to pass this information. So I’m passing params of input and params of output here.

So everything is working absolutely fine. Let’s execute this and see whether everything works well. So I’ll go to my command prompt. Understand, I’m not running this as a pipeline. I’ll run this file independently, but later on we will connect all the steps — pre-processed, evaluate, train — in a pipeline.

Just to test, I’m going to run "python src/pre-process.py". So here you can see it is executing. But here you are getting an error: it has no attribute "make directory". Okay, I made one error. So it should be "makedirs". Now I think it should work.

I will also not remove the error; I’ll show it to you directly. Now another error: "exist" unaccepted keyword argument. It should be "exist_ok". No worries, small errors will definitely be there.

Then again run "python src/pre-process.py". So here you can see my data has got created. Now inside my data I have my preprocessed file, so I have my data dot csv. Everything is perfectly ready. And here you can see that everything is working fine and it is getting saved to this particular location.

So my data pre-processing step is working absolutely fine. Now if I really want to go ahead and do any feature engineering, even convert my categorical features into numerical features, or change the scale of the data, I can actually do it over here. All the steps can be done over here.

But my main aim is basically to show you the entire data pipeline with the help of MLflow and DVC. When we are discussing about an end to end project at that time, we’ll be discussing. Initially we’ll build our basics and then we will probably go ahead and discuss more about it.

Okay. So I hope you like this particular video. Now in the next step, we will start working on our training pipeline. Then we’ll work on our evaluate. And then finally we’ll connect all these three and I’ll show you, with the help of DVC, how you can connect all these things.

So I hope you like this particular video. This was it from my side. I’ll see you in the next video. Thank you.

**Summary:**

**What has been done:**

Introduced the First Step of the Pipeline – Data Preprocessing

Created params.yaml file to store all project parameters.

For pre-processing: defined input (raw data path) and output (processed data path).

For training: defined paths for processed data, model save path (model.pickle), and ML hyperparameters (random_state, n_estimators=100, max_depth=5).

Purpose: keep configurations separate from code, so they can be easily reused or updated.

Implemented pre-process.py

Imported required libraries (pandas, yaml, os).

Loaded parameters from params.yaml.

Defined a function pre_process(input_path, output_path):

Reads CSV from the input path.

Creates the output directory (if not present).

Saves the processed dataset as CSV in the output path.

Added a simple test run with if __name__ == '__main__': to execute the preprocessing step.

Debugging & Fixes

Encountered small errors (make directory instead of makedirs, wrong keyword exist instead of exist_ok).

Fixed them and re-ran the script.

Verified that the preprocessed data (data/preprocessed/data.csv) was successfully created.

Demonstrated Execution

Ran python src/pre-process.py independently (not yet as a pipeline).

Confirmed that the script works and saves preprocessed data.

**Why it is needed:**

Params.yaml:

Centralizes all parameters (data paths, hyperparameters, model save paths).

Makes the pipeline configurable, reproducible, and easier to maintain.

Prevents hardcoding values inside Python scripts.

Preprocess.py:

Ensures raw data is read, cleaned, and stored consistently before model training.

Acts as the first stage of the ML pipeline.

Provides flexibility to later add transformations like missing value handling, encoding categorical features, scaling, or feature engineering.

Independent Testing:

Running preprocessing separately ensures each pipeline step works correctly on its own before connecting them with DVC.

Debugging early avoids issues when integrating into the full pipeline.

**Result:** This step set up the preprocessing stage of the pipeline. A params.yaml file was created to manage configurations, and pre-process.py was implemented to read raw data, process it, and save it to a defined location. This modular design ensures reproducibility, maintainability, and scalability, laying the foundation for the next stages (training and evaluation).

**3. Implementing Model Training Pipeline with MLFLOW Setup**

So we are going to continue the discussion with respect to our end to end ML pipeline using DVC and ML flow.

Uh, already I have made this entire folder structure. Uh, in the previous video you have your data dot csv. We have also spoken about the problem statement, what we are going to solve now in this entire pipeline. The first important component is your data pre-processing. Uh, for that I have actually created this particular file. Then you have to train a model, and then you have to probably evaluate metrics. And during the stages during in this pipeline, we will try to use multiple MLOps tools like DVC and MLflow.

DVC will be specifically used for data versioning, MLflow to log experiments, track experiments and do multiple things. Now first of all, uh, before we go ahead and start writing our code. So we will go ahead and set our all the normal parameters, all the basic parameters that we are going to work with. Okay.

So inside this particular params dot YAML file. So here uh, you know right. Let's say I will go ahead and write one one parameter like pre-process okay. Now for pre-process. What I will be doing is that I will, uh, you know, we will just use some key value pairs with respect to this and, uh, we'll try to set up some parameters, okay. And those parameters, I will be I'll be just displaying it in front of you like this.

So it is, it is saying that, hey, your input data is given somewhere over here. Uh, this is the basic information that you have. After you process the particular information or process the entire data, the data should be saved in this particular folder. So your output will be over here. So this is just like I'm providing some parameters. The input parameter will be nothing but "data/raw/././data.csv" which is nothing but this uh, after you perform the, uh, pre-processing, then your output, probably any any data that you really want to save, it needs to be saved in this particular folder. Okay.

So, uh, that is the basic common information that I'm giving. And the main aim of parameters dot YAML is that I'm trying to provide some parameters over here. And these all parameters will be hard coded so that we can actually use it in our code. Now, similarly for our training, our data, you know, I will be creating some parameters again over here.

So first of all where my data is basically present. So after the processing the data is basically saved over here. So this is the same path that we are going to use. After we train the model we need to save the model. Uh, in this particular path name and in with the help of this particular file name right. "model.pickle". So this will be the path where our models will be saved. Then you have this random state value number of estimators. I'm going to take it as 100 and "max_depth = 5". So I'm taking these are some basic parameters that I'll be giving during my train training phase okay.

And in the pre-processing phase, since I need the input data and where my output data needs to be saved. Okay. All this information, I'm actually providing it. And this is a very good way to probably start any projects because as you will be seeing as we go ahead, I will be creating this params dot YAML in different end to end projects and this will be very very much like many many parameters will be coming over here. Uh, this is just a beginning over here, right now, after we have set all the parameters and our params dot YAML file, I will first of all start with my pre-process dot py file.

Now in the pre-process dot py file, which is my first step, let me just go ahead and import some of the libraries. "import pandas as pd". Okay, along with this I will go ahead and import this. Okay, since we need to do the pre-processing. Okay. Then in order to read the params dot YAML file right I will be importing "yaml". Okay YAML file, YAML library. And finally I will go ahead and import "os" so that I will be able to set the path and all.

Okay, now first of all I need to load all the parameters from the YAML file. So here we will go ahead and write the code. So I'll write "load parameters from param.yaml". Okay. Now here I'm going to create a variable called as "params". And we can use "yaml.safe_load". And inside the safe_load I will be using my "open" function. And let me go ahead and define my YAML file so it is nothing but "params.yaml" file okay.

And "params.yaml" file. Uh, as soon as we load this, you know that what key you really need to call. Because since this is my pre-process dot py, I will just go ahead and call this particular key okay. So let me just quickly go ahead and write this. Call this key where we are going to call this. Okay. So this is nothing. But this is my parameters that I'm actually going to get from this YAML dot file. That basically means I'll be having this two keys input and output information available over here.

Now in the data pre-processing step we will go ahead and create a function "pre_process". Okay. And here I'm going to basically go ahead and write my "input_path". Then your "output_path". Okay. So these are the two parameters that I will be giving. "input_path" will be having the data that is already present. Because on this particular data only I need to probably perform any pre-processing. Right.

So what I will do, I will go ahead and write "data = pd.read_csv(input_path)". Okay. Let me set my "header=None" so that I don't want to use any header by default. Okay. So I can directly read the CSV file. Now after that what I will do. See. Anyhow, if I'm reading the data dot csv, if I'm keeping "header=None", I think it if you also keep like header without any headers also, then also it is going to read this entire data set because it is already having the data. So let me just remove this "header=None" because I need to use the headers itself. Okay.

Then what I will do after this. Okay. Uh I will quickly go ahead and write "os.makedirs". So we'll first of all make the directory path okay. And here I will write "os.path.dirname". And what directory I need to first of all create. Because in the params dot YAML. I know that my data dot csv needs to be stored in "data/preprocessed". Right? So obviously whatever is my output path, I need to probably create a folder with respect to that. So here I'm going to go ahead and give my "output_path".

Okay. And this output path will be provided with this feature only. I'll show you how you can actually go ahead and provide your output path also over here. So I will first of all go ahead and create the folder. And the folder should be inside this data folder itself. And that is what I have given. "data/preprocessed/data.csv". Okay. And then what I will do after this is that I will just go ahead and say, hey, if that folder already exist, "exist_ok=True". Okay. I'm just putting this particular parameter over there.

Then finally what I will do, I will just read this particular data set and I will convert this. I will probably save this in the form of a CSV in my "output_path". And here I can probably go ahead and take my "header=None", because I don't have to worry about any features or anything as such. So "index=False". I don't have to worry about any feature names and all. Okay, because we'll take this particular data set later on and we'll do the train test split, uh, whenever it is required. Okay. That will try to see it. But right now I'm just trying to save this particular data set in my output path itself. Okay.

So finally, let me just go ahead and write "print(f'Pre-processed data saved to {output_path}')". Now you may be thinking Christian data pre-processing is not perform any feature engineering at all. Guys understand right. Right now I just want to show you we are we are starting from some at some point. Right later on you'll be seeing EDA, you'll be seeing feature engineering. You'll be seeing multiple things as we go ahead.

But right now, uh, if you really want to perform any feature engineering here, only you can actually perform it right before you save it into CSV. But right now, I know that most of this particular data does not have any null values. It has numerical values. So I'm actually going to use this. Okay. Just just to show you that how the pipeline is basically created. This will give you a super cool idea with respect to this okay. So this is my pre-process dot py.

Now if I go ahead and execute "if name == 'main'". Okay I will prove first of all I will call my pre-process over here okay. So my pre-process function will be over here I will call "params['input']". Right. Because when I'm loading this params right on this pre-process, if you see in the param dot YAML you have your input key and your output key. You need to pass this information. You need to pass this information. So I'm passing "params['input']" over here. And finally I will also pass "params['output']" over here. Right. So everything is working absolutely fine right.

So let's execute this and let's see whether everything works well okay. So I'll go to my command prompt. Understand uh, I'm not running this as a pipeline. I'll run this file independently, but later on we will connect all the steps preprocessed to evaluate to train in a form of pipeline. But just to test, what I'm actually going to do is that I will just go ahead and run "python src/pre_process.py". Okay.

So here you can see it is executing. But here you are getting an error. Uh it has no attribute make directory or make direct. So let's see. Okay I made one error. So it should be "makedirs". Okay. Now I think it should work. So I will also not remove the error. I'll show it to you directly. Now uh exist uh unaccepted keyword argument exist underscore okay. So it should be "exist_ok". Okay no worries. Small small errors will definitely be there.

Okay then "python src/pre_process.py". So here you can see my data has got created. Now inside my data I have my preprocessed file. So I have my data dot csv. Everything is perfectly ready. And here you can see that, okay, everything is working fine and it is getting saved to this particular location. Okay, so my pre-processing step is data pre-processing step is working absolutely fine.

Now if I really want to go ahead and put do any feature engineering, even probably convert my categorical features into numerical features, even if I want to go ahead and probably, um, you know, change the scale of the data, I can actually do it over here. Right? All the steps can be done over here. But my main aim is basically to show you the entire data pipeline with the help of MLflow and DVC. But when we are discussing about an end to end project at that time, we'll be discussing. Right?

So initially we'll build, we'll build our basics, uh, and then we will probably go ahead and discuss more about it. Okay. So I hope you like this particular video. Now in the next step, we will start working on our training training pipeline. Uh, then we'll work on our evaluate. And then finally we'll connect all these three and I'll show you, with the help of DVC, how you can connect all these things. So I hope you like this particular video. This was it from my side. I'll see you in the next video. Thank you.

**Summary:**

**What has been done:**

Folder Structure Prepared

data.csv is available in the raw data folder.

A project structure is created for building the ML pipeline.

Defined Parameters with params.yaml

Created a YAML file to store input/output paths and training parameters.

Parameters include:

Input data location (data/raw/.../data.csv)

Output data location (data/preprocessed/.../data.csv)

Model save path (model.pickle)

Training parameters (random_state, n_estimators=100, max_depth=5).

Built the Preprocessing Script (pre_process.py)

Imported required libraries: pandas, yaml, and os.

Loaded parameters from params.yaml.

Implemented a function pre_process(input_path, output_path) to:

Read the raw CSV data.

Create the output directory if it doesn’t exist.

Save the processed data to the specified output path.

Added a main block (if __name__ == '__main__') to run the preprocessing step.

Tested Preprocessing Step

Executed python src/pre_process.py.

Fixed minor errors (makedirs, exist_ok).

Successfully saved the preprocessed data to data/preprocessed/data.csv.

**Why it is needed:**

Parameterization with YAML:
Using params.yaml ensures that paths, hyperparameters, and configurations are not hardcoded in scripts. This makes the pipeline flexible, reusable, and easier to modify.

Preprocessing Step:
This serves as the first building block of the ML pipeline. Even though no feature engineering is performed yet, it sets up the foundation for reading raw data, saving processed data, and ensuring the pipeline structure is ready.

Error Handling & Directory Setup:
Using os.makedirs(..., exist_ok=True) ensures output directories are created dynamically, making the workflow robust and reproducible.

Pipeline Readiness:
Running preprocessing independently verifies correctness before connecting it with training and evaluation. Later, DVC will orchestrate the entire workflow and MLflow will track experiments.

**Result:** We created a parameterized preprocessing step that prepares raw data into a structured, reusable form, forming the first step of the end-to-end ML pipeline with DVC and MLflow.

**4. MLFLOW Experiment Tracking In Dagshub**

Hello guys.

So we are going to continue the discussion with respect to our end to end machine learning pipeline. Already we have finished the training pipeline itself, and you could see that we are able to get accuracy score and why we have written the code till here and in this video we are going to probably go ahead 1 or 1 step ahead and we will go ahead and start tracking our MLflow experiments. And again all the tracking will specifically happen in the DAGs repository. So before that, I hope everybody has set up the set tracking URI in this specific code, which was shown in the next previous video. Right now let's go ahead and log log additional metrics okay.

Now in order to log additional metrics. As you all know, we are already inside this particular condition with the "MLflow.start_run". Uh, we are inside that particular block. So I will go ahead and write "MLflow.log_metric". So first of all we will go ahead and log our metric, which is nothing but accuracy. And you know that we have got our accuracy from the accuracy score itself. So here I will just go ahead and display my accuracy score.

Along with this, uh, I will also go ahead and log "log_param". So we are also going to log the parameters. Now some of the parameters that we are specifically going to log is like, uh, inside this "best_estimators". Right. We will go ahead and log what is the "n_estimators". Right. Uh what is the max depth. What is the minimum sample split. All those things will try to log.

So here uh my first parameter name I will just go ahead and write "best_n_estimators". And this is basically present inside my "grid_search.best_params". And here I will go ahead and write an "n_estimators". Okay. Now this "n_estimators" uh is basically coming from this particular value. And this entire is basically saved inside this "best_estimators". Because after the hyperparameter tuning with the help of this particular key we can actually retrieve it, right. Similarly for the Maxdepth I will be doing the same thing over here. We will also go ahead and log this.

After maxdepth we will log couple more parameters. One is "minimum_sample_split" okay. And the other one is "minimum_samples_leaf" okay. So let me name "best_sample_split" and "best_samples_leaf" okay. So all these values has been set over here. Okay. Uh, so this is the parameters that we are going to log. Along with that we are logging the metrics. This is good enough.

Then the next thing that we are going to log is the entire confusion matrix. And we'll try to log this entirely inside my artifact. Okay. So let's see this. So log the confusion confusion matrix and classification report. Okay so here is my confusion matrix. And here I have my "y_test, y_pred". This is my confusion matrix. Uh along with that I can also get my classification report by just using this "y_test" and "y_pred".

So, uh, all these things will be there, and, after this, what I'm actually going to do is that I'm going to log this entire confusion matrix and classification report in the form of one more important parameter, which is called as "log_text". Okay. So here I will write "MLflow.log_text". And I hope I've not shown you before. But there is also one more feature. When I was going through the documentation, I saw this one more feature, which was pretty much cool, right?

And I'll convert that entire confusion matrix into a string before, and then save it with the name as confusion matrix. Okay. And I'll show you where this will also be visible, which will be amazing. Then I will be also displaying "MLflow.log_text". Okay. And here you will be able to see CR. And here I will be writing my classification report "classification_report". And let me do one thing. See when I'm logging the text. Right. The second parameter that needs to be given is a text file, or it can be any of the files itself. So here I'll be giving a txt file which will be saving all this information like confusion matrix and classification report over here okay.

And finally the last step after probably logging each and everything is that I will take my I will create a variable called as "tracking_URL_type_store" okay. And I will go ahead and parse this "urlparse". And I will just get this "get_tracking_URL". This is just one conditions. I'm trying to put it over here so that I should be able to get it ".scheme". Okay. Scheme. Over here I will be getting my tracking URI type store which we have already discussed previously why we are doing this.

And along with this, I will just go ahead and write my condition. If the tracking URL type is not set, that is, it is not equal to file. That basically means whether it is equal to HTTP or Https. Then what we really need to do is that we will go ahead and learn "MLflow.sklearn.log_model". And here I'm going to basically go ahead and take "best_model, model". And I will just name it as "registered_model_name=best_model". Okay.

Otherwise I need to if it is of file type we need to set it as signature okay at the end. So I'll just go ahead and paste it over here. Else We will just go ahead and set the log this particular model. And we'll also include the signature over here. Okay. So this is done. All the steps are done.

But one thing I forgot to tell you is that finally, we also need to go ahead and create our pickle file. Right. So this is basically the logging part. The logging part is completed. Now what we are basically going to do is that we are going to create a directory to save the model okay. The directory directory to save the model okay. So for that I will write "os.makedirs". And I'll just sorry "makedirs". And here I'm going to go ahead and give my "os.path.dirname". And here I'm going to give that path entirely in the model path. And this in "params.yaml" I have this entire path. Right? "model/model.pickle".

So I have to take this particular path and that will be passed in my in my function over here. Right. That that path will get passed over here. And that also will I'll try to show you how we can proceed with that. Okay. Then along with this setting up with this particular directory path, I will also write a condition "if exists=True". Okay. If it exists, don't do anything. Don't create that particular path okay. Then I know what is my file name. My file name is nothing but this particular "model_path". Okay. "model_path" I will take this entire "model_path". And I will just use this "pickle.dump". And we will go ahead and dump our best model in the form of pickle file.

So for that I will open this file name in the form of write byte mode. Okay. So we are just going to open this entire file in the right byte mode. And we are going to dump this particular bus model. And the name of the model will be nothing but "model.pickle". Okay, so that is what what is going to happen once we have this. Okay.

So finally I will also go ahead and print for my sake. I will go ahead and write. Hey model saved to "model_path". Okay. "model_path". So we are going to save this. And finally you'll be able to see that after this particular definition I think this is my entire function. What I've actually written step by step, what all things we have actually done is that we have read that particular data set. We have done the train test split. So let me go ahead and, uh, show you over here. So we have done the train test split over here. We have also set up the set tracking URI. Then we have set up the parameter grid. Then we have performed hyperparameter tuning. Then you have this entire grid search. We have calculated all the metrics. We have logged all the metrics even confusion matrix. Then we have set up the tracking URI and then finally we are saving the model also.

So finally I will just go ahead and run this. "if name=='main'". And then I will just go ahead and write "train". Now when I call this particular function it should be given as params. Okay. Params with the name of with the name of this particular data. Right. So data over here I will pass data along with that. The second parameter that I'm actually going to pass is my. This is my params model path. So that will basically be my model. Along with this if you want to pass your params random state. Okay. "random_state". This params is nothing, but with the help of a code we had read the param your uh. See, with the help of this particular code, we have read this YAML file. Right? So all the configuration is basically present over here and we are reading it. And then finally you can also see that I will also go ahead and write my parents. And "n_estimators". Okay. And finally all these parameters. So we had "n_estimators". Also we have max depth also. Anyhow I'm not using those parameters. But just for your sake I am showing each and everything over here. Okay Max. Let's go. Depth. Perfect. I think we are good to go. So once this code is basically getting executed, this entire thing is going to happen. All the tracking will also happen.

Do you want to test it? Let's test this now. And I think we should be able to run this. So right now if I see inside my machine learning pipeline nothing has been logged yet. Okay, I'm not even committed any code, but we are going to commit it just in some time. But let's see whether we are able to log something or not over here. Okay, that is the most important thing. Now in order to log I have to run this train.py file. So I'll go ahead and write "python source/train.py". Let's run this also to get some error. But we'll try to fix it because I want to show each and every thing in front of you. Okay.

So cannot import name confusion matrix. Okay. So these are some of the problems. While typing you will face this problem confusion matrix. Let's see where I have used confusion matrix over here. Okay. Confusion matrix. Perfect. I think now it should be running it. So "python source/train.py". Okay now you see fitting three folds for three each for 24 candidates. All the information is coming over here. Uh, okay. Accuracy score. Local variable accuracy score. Reference before assignment. Okay, let's see this where it exactly it is. And I'll make some changes so that, uh, okay. This is the problem. No worries. I will just go ahead and copy this and paste it over here. And since I have just changed the name, uh, because this same accuracy, we will be using it over here, okay. Because internally I don't want to use accuracy score. Accuracy score. Because accuracy score is a different function over here. And same thing we are trying to use. Accuracy is fine. Uh let's see whether it should run now.

So finally we'll go ahead and run it. And the main thing is that whether my model file is basically getting created or not. So it has started its fitting three folds for each of 24 candidates. This is basically the hyper parameter tuning. I got the accuracy to 72%. I think I should be able to see my model. Okay, it is still not getting created, but first of all it will log all the experiments. Yeah. See it is logging now. Successfully registered perfect experiment tracking. Now you can also see my models folder is created. "model.pickle" is also there. Perfect. And the best part will be that if I just go ahead and reload this, my experiment should be there. See my experiments is basically getting created. Two experiments has got created. First of all, let's see what all information we have got. So this is with respect to all the parameters accuracy metrics okay. And uh accuracy is also over here. And your entire artifacts along with the "model.pickle" see "classification_report.txt". So this is also created confusion matrix is also created, which isn't good, right? Amazing.

Now another experiment which I see what has got. Okay, this was the previously failed one. No worries. But here you can see clearly, right? This has got created. If you want to probably see it in a much more better way. I can go ahead over here and inside my experiments, I think there should be a MLflow UI. See, MLflow ui is there, and this MLflow ui is basically running inside this DAGs hub remote repository. So this is a successful one. You can probably check it out. And the best part is that this model is already registered. Right. Because we have registered it and artifacts you are able to see this. This is the code to probably read anything or any kind of code later on. This is my runs everything you'll be able to see. And you can also write the code with respect to spark data frame. And if I go ahead and see in the models, my best model is also registered okay.

So in short, you know, this entire entire pipeline of training pipeline is working, which is good enough. But we will probably see at the end of the day, this will not be sufficient because we need to make sure that when I say pipeline, right, I'm not just talking about a single pipeline. This pipeline should work together. First pre-process, then train, then evaluate. So right now till train we have written the code. Now in the next step we will go ahead and write our "evaluate.py". And then I'll try to show you how with the help of DVC we can connect all these pipelines. And here you will be able to see a very good visualization. Diagrams can also be seen over here in data pipeline. We have still not yet committed anything, but just in the next tutorial you'll be able to see that.

So I hope you like this particular video. Now in the next tutorial I will go ahead and start working on my evaluate.py. Yeah, so this was it. I will see you in the next video. So yeah, this was it. I will see you all in the next video. Thank.

**Summary:**

**What we did:**

Extended Training Pipeline with MLflow Logging

Added experiment tracking with MLflow inside the training pipeline.

Set up tracking URI (configured in the earlier step).

Started logging within the mlflow.start_run() block.

Metrics Logging

Logged the accuracy score using mlflow.log_metric("accuracy", value).

Parameters Logging

Retrieved best hyperparameters from grid_search.best_params_.

Logged key parameters:

n_estimators

max_depth

min_samples_split

min_samples_leaf

Confusion Matrix & Classification Report

Generated confusion matrix (y_test, y_pred).

Generated classification report.

Converted both into text format and logged them using mlflow.log_text.

Saved outputs as artifacts (confusion_matrix.txt, classification_report.txt).

Model Logging

Checked tracking URI type:

If remote store (http/https) → logged model using mlflow.sklearn.log_model.

If local file store → logged model with signature.

Registered the model under best_model.

Pickle File Creation

Created directory for model storage (from params.yaml: model/model.pickle).

Used pickle.dump to save the best model locally.

Confirmed with a print message: Model saved to model_path.

Final Execution

Wrapped everything in if __name__ == "__main__":.

Passed parameters from params.yaml (e.g., model path, random_state).

Ran python src/train.py to test.

Fixed small errors (confusion_matrix import, accuracy variable conflict).

Successfully:

Performed grid search CV.

Logged metrics, parameters, confusion matrix, classification report.

Saved model.pickle.

Registered the model in MLflow.

MLflow UI Verification

Verified in MLflow UI (via DAGsHub remote repo):

Metrics and parameters logged.

Confusion matrix and classification report stored as artifacts.

Model successfully registered.

Experiment runs tracked (both failed and successful).

**Why it is needed:**

Metrics Tracking: Enables monitoring accuracy and performance across different runs.

Parameter Tracking: Logs hyperparameters used in training for reproducibility.

Artifacts Logging: Storing confusion matrix & classification report provides deeper insights into model performance beyond a single metric.

Model Versioning: Registering the model ensures experiment reproducibility and version control.

Pickle File Storage: Provides a local copy of the model for deployment.

MLflow UI: Centralized dashboard to visualize experiments, compare runs, and manage models.

**Result:** This step upgraded the training pipeline by integrating MLflow experiment tracking. Now, all metrics, parameters, artifacts, and the trained model are logged, saved, and registered—making the workflow reproducible, transparent, and ready for collaboration.

**5. ML Evaluation Piepline With MLFLOW**

So we are going to continue the discussion with respect to our end to end ML pipeline project with the help of DVC, ML flow and DAGs hub.

Uh, already in our previous video, we have implemented our training pipeline. We also executed it was working absolutely fine, and we were also able to track all the experiments in the MLflow UI that also we had actually checked. You could see in the experiment section all the ML flow experiments were basically getting created.

Okay, now the next step, what we are going to do is that we are going to basically go ahead and implement our evaluate pipeline. So for that I have this evaluate.py file inside this source. So first of all I will go ahead and import all these things. See evaluation is more about understanding with respect to any new data that we are going to have. You know how the accuracy is and what kind of accuracy we are able to get. Right. And for that you can actually do a separate MLflow tracking.

So initially you go ahead and import all this libraries. Pandas pickle sklearn dot metrics, accuracy SQL, YAML OS MLflow okay. And then again with respect to train.py what I am actually going to do, I will go ahead and import all these environment variables quickly. So let me go ahead and import this, because I will be requiring all this environment variable so that I know where we can specifically go ahead and track it. Right.

Uh, then what we will be doing is that we will be specifically going and loading our params dot YAML file. So and that also we require the training information again with respect to the same data. We will be working along with that right then.

Uh I will go ahead and create my function which is called as "def evaluate". And inside this I will go ahead and write "data_path, model_path". Right. And finally I have "data = pd.read_csv(data_path)". And here I'm going to go ahead and uh give my data_path okay. After reading it I will go ahead and set up. Or I will go ahead and probably create my x and y variable. Okay x and y variable with respect to our data. That is input and dependent input features. Uh and my output features.

Along with this, I will also go ahead and set up my "mlflow.set_tracking_uri" because I also I need to go ahead and upload all my metrics in my remote repository, right? The same data pipeline. I'm actually setting it up over here, not data pipeline. I think the name was this one, right. So here you have this. I will go ahead and paste it over here. I will close it. Okay. So this is nothing but machine learning pipeline right. And you can also go ahead and set it up. Okay.

Now the next step is that we already have our pickle file. Right. We know where the pickle file is. So I will be loading the model from the disk okay. And in in order to load it I will go ahead and write "model = pickle.load(open(model_path, 'rb'))" whatever model path we have defined from our params dot YAML, and we'll try to read this in the form of a read byte mode. Okay. So once we read it then we can actually do the predictions.

So predictions. I will just go ahead and do it. And I will go ahead and write "model.predict". And this will be predicting on my input data. And this can be my new data. See if you have something new data that is coming up in the params dot YAML. You can probably go ahead and create a new path. And from that you can pick up your data. Then finally I will go ahead and see my accuracy score. My accuracy score will be nothing, but I will try to find out the differences between my predictions, and then I will go ahead and log metrics to MLflow.

Okay then "mlflow.log_metric". And here is my "accuracy, accuracy". Okay so here it is. And finally I will go ahead and see I'm logging the metrics with the help of "mlflow.log_metric". Again in the same log it will probably go ahead. And this is with respect to the evaluation, new new things with respect to the new data that you are able to get right.

So finally I will go ahead and run "model_accuracy: accuracy". And this will basically be my accuracy just to print okay. So perfect. We have also written our model evaluation.

And here I will go ahead and write "if name == 'main'". Then I go ahead and call. My evaluate function will be nothing but params. And here I'm going to give my data. And this will be my params with model okay. So model path that I have data and model path.

So perfect I think we have implemented this thing also. And now it's time that you know, after we have probably written the evaluate.py file. Now we should be running together. We should try to combine all this pipeline and run. And that is what I'm actually going to do it in the next video.

So yes, this was it from my side. I'll see you in the next video. Thank you.

**Summary:**

**What has been done:**

Created evaluate.py

New file inside src to handle model evaluation.

Imported Required Libraries

pandas, pickle, sklearn.metrics (accuracy_score), yaml, os, and mlflow.

Ensures consistency with the training pipeline.

Loaded Configuration

Read params.yaml to fetch:

Data path

Model path

Reused same config for consistency across train and evaluate steps.

Defined Evaluation Function

def evaluate(data_path, model_path) created.

Steps inside function:

Load data using pd.read_csv(data_path).

Split into features X and target y.

Set MLflow tracking URI (to log evaluation metrics remotely).

Load saved model from pickle file (pickle.load(open(model_path, 'rb'))).

Run predictions with model.predict(X).

Calculate accuracy score (accuracy_score(y, y_pred)).

Log accuracy to MLflow with mlflow.log_metric("accuracy", value).

Print accuracy (model_accuracy: accuracy).

Main Execution Block

Wrapped everything in if __name__ == "__main__":.

Called evaluate() function with:

params["data"] (for dataset path).

params["model_path"] (for model pickle file).

Evaluation Completed

Accuracy of the model on given/new data is computed.

Metrics logged in MLflow (visible in experiments).

Evaluation script is ready to be combined with preprocess and training pipelines.

**Why it is needed:**

Separate Evaluation Step:
Keeps training and evaluation isolated, making the pipeline modular and reusable.

Validation on New Data:
Confirms how the trained model performs on unseen or updated datasets.

Experiment Tracking:
Logging evaluation metrics to MLflow helps compare training vs. evaluation performance in the same UI.

Reproducibility:
By using params.yaml for both training and evaluation, results are consistent and reproducible.

Preparation for Full Pipeline:
With preprocess, train, and evaluate steps coded separately, they can now be chained with DVC into a complete end-to-end ML pipeline.

**Result:** We built a dedicated evaluation pipeline (evaluate.py) that loads the trained model, predicts on test/new data, calculates accuracy, and logs it into MLflow. This ensures the pipeline is modular, reproducible, and ready to be connected into the full end-to-end workflow with DVC.

**6. Run The Complete Pipeline With DVC Stage And Repro**

So guys, now we are going to continue our discussion with respect to our end to end machine learning project pipeline. Already we have developed our three main important components that is pre-process, train and evaluate. And we are also able to track it with the MLflow.

Now what we will do is that we will will try to connect all these three, three independent components in the form of pipeline. And for this also we are going to use DVC because with the help of DVC we will track multiple parameters. We will track "params.yaml" also will track the data, also will track model versioning also and many more things.

Okay, so first of all what we will do is that we will open our new terminal. Okay. You have to be in the venv environment like how I am there. Okay. So first of all I will go ahead and write "dvc init". So once I go ahead and write "dvc init". So here you will be able to see that ".dvc" file will be created. Okay. And right now for currently I will just delete this model file because I don't require it. And with respect to our data write data over here. You will be able to see this.

Now what I will do the main raw data will try to track it. Okay, so here what I will be doing because raw data is coming from somewhere else, right? So we really need to go ahead and track those. So I will just go ahead and clear my screen. I will write "dvc add data/raw/data.csv". Because we need to track this because this is the first data that is probably coming up after that through the pipeline we will run, pre-process, then train, then we'll create our model and then we will evaluate.

So I don't want my git to basically track this particular file. So once I do this. So here you can see that it has now been tracked by uh by my DVC. But it will say that hey, additionally if I just go ahead and open this inside this there are two more files that has got created. Okay. One is ".gitignore", one is "data.csv.dvc". This needs to be tracked by the git right. So I will just go ahead and copy this entirely okay.

So let me just go ahead and copy this "git add data/raw/data.csv.dvc". And one more I will try to also add this okay "git add". So I'm basically going to add both this perfect okay. And then let me just go ahead and commit "git commit -m 'add raw data'". So I'll just committing this okay. Now once we commit it you know I can go ahead and do the "git push".

But before that you know as I said I'm going to combine all these independent components like evaluate pre-processing and train.py in the form of a pipeline right now to in order to do that now, please have a look onto this because this is really important. Okay.

Uh, one thing that you really need to understand is that, uh, we need to define like, if I really want to connect all these three important components, that is data preprocessing, training and evaluate, we will use another amazing functionality in DVC which is called as DVC stage.

Okay, so uh, DVC stage basically means uh, DVC will be able to define that how your corresponding step of workflow, machine learning workflow, like processing, training or evaluation, how they really need to be executed. And this entire things can be tracked in the "dvc.yaml" file.

So uh, just to go ahead and start and probably show it to you like how things work over here. What I will do is that quickly I will just go ahead and write DVC or let me just go and open my notebook. Okay. And let me just go ahead and copy one code that needs to be executed in the terminal. Okay.

So here it says hey "dvc stage add -n process". Okay. Now I have to execute this "dvc stage add". Whenever we say "dvc stage add" It is basically when I whenever we define a stage in a DVC pipeline, uh, you can just imagine that I'm creating this pipeline for executing my pre-process pipeline itself. Okay.

And this can further get connected to the next stage. So this is just one stage I can have multiple stages, right? I can have one more stage that will be for triggering training pipeline. One more stage can be there for triggering the evaluate pipeline. Right.

So, uh, if I just probably tell you in a basic, fundamental way, like what we are actually doing with this particular staging, uh, command. Right. You will be able to see that with this, we will be able to clearly define our pipelines. So and why we are doing this, we are specifically doing this so that we'll be able to track multiple files.

So if I just give you a basic definition over here, I'll just go ahead and copy and paste it in front of you. The "dvc stage add" command is used to define stages in a machine learning pipeline or data pipeline. This stage represents steps like data preprocessing and all.

So in order to just give you an idea how things work, let's say that I have three main important steps okay. One is pre-processing okay. This is independently running. We can run run it independently. The other one is training okay. And the other one is evaluation. So three important, uh, independent components you can consider now. But my entire machine learning ML pipeline should run in this way. Right. My ML pipeline should be, first of all, running with pre-processing, then the output probably I want to probably take it. I will be taking it in my training pipeline, then finally my evaluation pipeline.

And while doing all these things internally, you know, we may perform MLflow experiments, we may perform DVC data versioning or DVC data versioning. We may perform multiple things, right. We may do multiple things like this right now, considering all these things in order to define this in the form of pipeline. So DVC has one functionality which is called as DVC stage.

And we can probably add any number of stage. We can add stage one which will be which will be for this, you know for executing this pre processing. Then after stage one we can combine this with stage two which will be responsible in executing this pipeline. And finally we will be also able to combine with stage three which will be executing this evaluation pipeline. Right. So all these things we will try to do it. And for that we just need to run some command. We don't need to write any code.

So let's see this particular command. So here we have written "dvc stage add -n". "-n" basically means we are creating a new a new stage over here. And the new stage is nothing. But with the name of pre-process okay. Now this is my new stage over here.

And so it is basically showing that, hey, this is nothing but the name of the stage that we really want to create. Okay. Then in the next parameter which is "-p", this "-p" option tracks tracks the parameter that are available over here that we have written over here. Now this parameter is where it is this pre-processed input or pre-processed output. You know that this input are already there in the YAML file right. Input and output.

So to track that, you know, if if it is affecting the stage stage from the params dot YAML file and that point of time, if we really want to track it, we can go ahead and track it. The parameters are currently being tracked over here "process.input" and "process.output".

Then coming to the third parameter uh "-d". "-d" is nothing, but it specifies the dependencies dependencies for the stage. Now dependencies of the stage is that I require two files, one is "pre-process.py" and the other dependencies. I definitely require my "raw_data.csv" file. Okay, then then. So this d basically means dependencies. Uh, p is nothing but tracking the parameters. N is nothing but name of a process.

And if I go ahead and see with respect to "-o" specifies the output of the stage, now we know what is the output of the stage from "pre-process.py". It is nothing, but we need to create this particular file path. We need to create "data.csv". And in order to probably create this particular output, I need to execute this particular code which we had executed from the terminal.

So what I will do, I will just go ahead and copy this entirely, and I will paste it over here. Anyhow, I will be giving you this in the readme file. You can also go ahead and execute it. Now the problem is that uh here it will not get executed in the command terminal. Right? Because over here I have multiple multi-line. So let me do one thing. Let me just open git bash. And I can also go ahead and write step by step all the commands that I really want. Okay.

Let's say if my command is something like "dvc stage add pre-process" and all, so I can just go ahead and copy it over here. Otherwise with the help of git bash also we can do first of all in git bash you know how to activate your conda environment "source activate venv". Okay. Uh, sorry. It should be "source". Okay. So now it has got activated. My venv environment. So let me clear the screen. Okay.

And now what I'm actually going to do I'll just go ahead and copy this and we will create our first stage. Okay I'll paste it. So let's go ahead and execute. This pre-process stage already exists in "dvc.yaml" file. Okay. Previously it got created right when we executed it. I'll just delete this and I will execute it once again. Okay. Clear. Come on. So now let's go ahead and execute this. So this has got executed perfect. Okay.

So if you see there will be a YAML file which will get created "dvc.yaml" and here the stages will be defined. See this is my first stage. Amazing right? And that is why DVC is so powerful. Because after that, once we push it right you'll be able to see the results. Amazing results that you will be able to see.

Okay, now after my first stage, my second stage, you I hope everybody knows what it is because I need to probably focus more on the, uh, running the, uh, training pipeline after that. Right after pre-processing. It is, uh, training pipeline. Now, with respect to the training pipeline, I will probably go ahead and write the code over here.

Okay, so "dvc stage add train". So parameters I need to track is "train.data", "train.model", "train.random_state", "train.estimators", "train.maxdepth". So these all parameters are basically present in my YAML file. Then the dependencies is nothing but two files "source/train.py" and your pre-processed or instead of pre-processed I will just go ahead and write raw because there I have my entire data set. I'll keep it as raw. Only you can make the changes in pre-processed. As you wish.

Okay, then, uh, your output here I will be creating as "model.pkl". Okay, so that is the output. And this is nothing but "python source/train.py". So let's go ahead and execute this. So this is my second stage that will get added over here.

So I will go ahead and execute it. Let me press enter. Perfect. So this has also got it added. And here you can see in the "dvc.yaml". Here you have "python source/train.py". All these things are there. So the best part of this particular file will be that it will get executed in the same step. Okay.

And the third one which is nothing but my evaluation evaluation for evaluation. Now you can think that how your DVC command will be. So "dvc stage add evaluate". Evaluate is the name of the third stage. Then I have dependency on this and my "model.pkl" file. I need to have this first only and then you have another dependencies on data pre-processed data. So I will just go ahead and write raw over here. And here you have "python source/evaluate.py".

So let's go ahead and execute this. Also. Let's paste it I think it will get executed. Let's press enter. And the "evaluate.py" did I am I running uh reading the data set from params data? Okay, I have changed that in the "params.yaml" file. Okay, so dv configure everything has happened. Great great great added stage uh evaluate in this to track changes get run run run run. So everything is added and "dvc.yaml" file is also updated.

Okay. Now in order to run this entire pipeline okay, run this entire pipeline, I will just go ahead and write "dvc repro". Okay. Now "dvc repro", what it does is that it will be running, uh, the entire pipeline, all entire stages that is available. So if I press enter right now, you can see no "model.pkl" file is there. Okay, so now we will be able to see that entire pipeline will run.

Okay. Let's press enter. Hope so. Fingers crossed. So here you can see "python source/pre-process.py" run stage train "python source/train.py". Everything is going to execute. So here you can see fitting is happening. My MLflow tracking will automatically happen. And it should be able to probably track each and everything. And now my evaluate will also get executed after that. Right. So right now this "train.py" is running. See it is running in the form of a pipeline itself, which is quite amazing. Okay.

And this looks good. This looks really, really good. Okay. And here you can see "python source/evaluate.py". Great great great great great great. And here everything is run. Now let's see in my whether we are able to see some experiments or not. So experiments is over here. This looks good. This is my recent experiment. So see, this is nothing. But my accuracy that I'm able to see artifacts is not there. This is the evaluation metrics, right? "evaluate.py".

But if I probably go ahead and see this, here is my entire accuracy metrics. Along with that I have my classification report everything. If you also want to probably go ahead and see in the experiments, you can also go ahead and check out in the MLflow UI and in the MLflow UI. You will be able to see that this is my. This is my accuracy for the evaluation. Okay.

And the second one is specifically my model, which is giving me 77.9%. And if I go ahead and see in the artifacts, if I go ahead and see my classification report or confusion matrix, I should be able to see all these details, which is right. Very amazing. Right. So in short, we are running the entire pipeline over here. Okay.

But still, uh, there are a lot of work because we have to definitely do a lot of commits. Right. So let me again go back to the command prompt. So till here everything is, done well, but at the end of the day, we need to go ahead and add all the files that is required with respect to the commit. Right. So first of all, I will go to remote, go to DVC and we will set up our uh DVC, DAGs of DVC remote.

So let me go ahead and copy this. Okay. So two important information that I have. Again I will go ahead and open my git bash. I will just go ahead and clear my screen over here. And we need to set up the DVC hub remote. Right. So let's set up this okay. And I have already explained about these steps in a previous video. I will also copy this and we'll go ahead and set up the credentials. Okay.

Credentials. Paste it execute it paste it execute it right so perfectly it has got executed. Now what I can do I can probably say "dvc pull -r origin". Okay, so it will just try to pull and see whether everything is fine. Then I will say "dvc push -r origin". So it will just go ahead and push it. All my DVC files that are important files which has been tracked by DVC. So it is pushing to the S3. Perfect.

Now I will go to my command prompt and quickly go ahead and commit all those things. So let's see whether I am not committing unnecessary things. Mhm. Mhm. Perfect. Raw is there. This is there. "git add ." "git commit -m 'final changes'" "git push origin main". So my push should happen.

And now if I just go ahead and reload it, I should be able to see my data pipeline and hear the beautiful data pipeline is here. See, initially I had this data raw "data.csv". See blue color is nothing, but it is DVC managed. Green color is nothing but git managed. You have your "model.pkl" file. Okay. Uh, which is again DVC manage which is beautiful. Okay. "data.csv" again DVC manage. And here you can see my entire pipeline. Isn't it just amazing. Okay.

And you can see the entire pipeline even if you probably go inside your data folder. Uh whatever data you have. Right. Like let's say your raw data, if you go ahead and see in "data.csv" here, you will be able to see the history. And this is where it is tracking. It is getting tracked with the MD5 MD5 file. Right. And this is beautiful right. All the entire pipeline is in front of you. And it shows that how things are basically getting executed. The visualization Mechanism of doing all these things right.

Uh, one very important information. I will just try to upload all these things in my readme file. Uh, let me just go ahead and update this in my readme file. Okay. So quickly. For adding stages I will just go ahead and use this. Okay. Perfect. Now you can also go ahead and preview it. Uh open preview. And here are all your commands. Okay.

So I hope you like this particular video. A long tutorial, a long amazing module, but this will definitely give you a lot of confidence if you have executed it successfully. Right? So yes, this was it from my side. I will see you all in the next video. And please go ahead step by step and just follow the process that how I have actually done it okay. So yeah this was it. I will see you in the next video. Thank you. Take care.

**What has been done:**

Independent Components Built – Three key modules were developed:

Pre-process (data cleaning/transformation)

Train (model training)

Evaluate (model testing/metrics)
These were already working individually and tracked with MLflow.

Pipeline Creation with DVC – Instead of running each component separately, all were connected into a single ML pipeline using DVC (Data Version Control).

DVC Stages Defined –

Stage 1: Pre-process → takes raw data, outputs processed data.

Stage 2: Train → takes processed data, outputs model.pkl.

Stage 3: Evaluate → takes the trained model + data, outputs evaluation metrics.
These stages were tracked in dvc.yaml.

Pipeline Execution – Used dvc repro to run the full workflow (preprocess → train → evaluate) automatically, ensuring all steps are linked.

Versioning & Tracking –

Raw data tracked via dvc add.

Model versions, parameters (params.yaml), and outputs tracked in Git + DVC.

MLflow simultaneously tracked experiments, metrics, and artifacts.

Remote Setup – Connected to a DVC remote (S3) so that datasets, models, and pipeline outputs are stored and version-controlled in the cloud.

Visualization – DVC generated a DAG (Directed Acyclic Graph) of the pipeline showing dependencies and flow (raw data → pre-process → train → evaluate).

**Why it is needed"**

Reproducibility – Anyone can re-run the pipeline (dvc repro) and get the same results.

Version Control – Every dataset, model, and parameter change is tracked, enabling rollbacks and comparisons.

Automation – Instead of manually running scripts, the pipeline executes in the right sequence.

Experiment Tracking – MLflow ensures all metrics and experiments are logged.

Collaboration – With Git + DVC, multiple team members can work seamlessly, pulling the right versions of data and models.

Scalability – Future updates (new data, new models) can easily be added as new stages in the pipeline.

**Result:** We created a complete end-to-end ML pipeline where preprocessing, training, and evaluation are connected using DVC. The pipeline tracks datasets, parameters, models, and metrics while logging experiments in MLflow, ensuring reproducibility and transparency. It can be executed with a single command to generate the trained model, evaluation metrics, and a visual pipeline representation.

# **M) End To End NLP Project With HuggingFace And Transformers**

**1. Introduction To Huggingface And Problem Statement**

So now we are going to implement a new end-to-end NLP project using Hugging Face models. If you’re not familiar with Hugging Face, it’s an amazing platform that provides a variety of pre-trained models which you can integrate into your projects to build complete end-to-end solutions. Hugging Face also provides API endpoints, making it ideal for generative AI applications because most open-source models are available there. Many companies that release open-source models integrate them with Hugging Face, so knowing how to use these models and integrate them into your projects is essential.

First, go to Hugging Face
 and sign up for an account. I have already signed up, and once logged in, you can go to the "Models" section. Hugging Face provides models for multiple domains: multi-modal, computer vision (like depth estimation, image classification, object detection, image segmentation, text-to-image), natural language processing (tasks like text classification, token classification, question answering, zero-shot classification), audio (text-to-speech, text-to-audio, audio-to-audio), tabular machine learning (classification and regression), and reinforcement/graph machine learning.

In this project, we will focus on text summarization. Once you click on “Text Summarization” in the models section, you will see a list of available models. You can pick any summarization model and integrate it generically so that similar steps will work for other models as well. For example, we can select the “Facebook BART CNN Daily Mail” model. Here you can find details like datasets used for training (C4 and HugeNews) and other information about the model. Another option is the “Falcon AI Text Summarization” model, which is a fine-tuned T5 small variant.

Text summarization basically means reducing long text into a concise summary. To illustrate, we can use websites like CoolBot
 which provide text summarization tools. You can input a long story, such as one generated using ChatGPT about a lion and a king, and get a summarized version with selected keywords. This is exactly what we will implement programmatically using Hugging Face models.

To use the selected model programmatically, we will rely on the Transformers library and PyTorch. Hugging Face provides sample code for each model. For example, for the BART CNN Daily Mail model, you can use it as follows:

from transformers import pipeline

# Initialize the summarization pipeline
summarizer = pipeline("summarization", model="facebook/bart-large-cnn")

# Input text to summarize
text = "Once upon a time in Kingdom Nestlé nestled between vast forest and hills, there lived a lion who was known as the king of all animals..."

# Get the summarized text
summary = summarizer(text, max_length=100, min_length=30, do_sample=False)
print(summary)


This approach is generic, so you can swap in any other Hugging Face summarization model and the same steps will largely work. Hugging Face’s Transformers library is designed such that loading a model, using AutoTokenizer, fine-tuning, and inference follow similar patterns across models.

In our project, we will also focus on fine-tuning a selected model. We will use datasets available in Hugging Face, such as the SamSum dataset, which contains annotated dialogue summaries. For example, to load the dataset, you can do:

from datasets import load_dataset

# Load the SamSum dataset
dataset = load_dataset("samsum")

# View sample data
print(dataset['train'][0])


Once we explore the dataset, we will preprocess it and fine-tune our selected model on it. After fine-tuning, we can integrate the model into an end-to-end project pipeline, including data ingestion, preprocessing, model training, and inference. This project will give a complete hands-on understanding of deploying a Hugging Face NLP solution.

So, in summary, this project will teach you how to:

Navigate Hugging Face and select a pre-trained model.

Understand text summarization and example applications.

Use the Transformers library for summarization with Python:

from transformers import AutoTokenizer, AutoModelForSeq2SeqLM

# Load tokenizer and model
tokenizer = AutoTokenizer.from_pretrained("facebook/bart-large-cnn")
model = AutoModelForSeq2SeqLM.from_pretrained("facebook/bart-large-cnn")

# Tokenize and summarize
inputs = tokenizer(text, return_tensors="pt", max_length=1024, truncation=True)
summary_ids = model.generate(inputs["input_ids"], max_length=150, min_length=40, length_penalty=2.0, num_beams=4)
summary_text = tokenizer.decode(summary_ids[0], skip_special_tokens=True)
print(summary_text)


Explore datasets from Hugging Face and use them for fine-tuning.

Integrate the model into an end-to-end NLP pipeline for real-world use.

This introduction covers everything about what we are going to do in this project. In the next video, we will start building the project step by step, exploring the dataset, fine-tuning the model, and performing summarization.

**2. Github Repo And Project Structure Set up**

So now we are going to start our project implementation. In this particular video, I will discuss how to set up your GitHub repository and also define a project structure suitable for this NLP project.

First, navigate to your folder location where you keep all your projects and create a new folder, for example, named Summarizer. This will be our project name. Open the folder using VS Code by typing code . in your command prompt. This will launch VS Code in the newly created project folder.

Next, we need to create a GitHub repository. Go to GitHub
 and click on "New Repository." Name it TextSummarizer, keep it private, add a README file, and choose a license (General Public License). Once the repository is created, copy the repository path. Instead of creating the folder locally, we can clone it directly:

git clone <repository-path>


After cloning, open the folder in VS Code using code . again. You will now see the .git configuration, README file, and license already present in your project folder.

The next step is to create a Python environment. Use Conda for this:

conda create -p venv python=3.10
conda activate venv


After activating the environment, we will create a requirements.txt file to list all necessary libraries. For this project, we will need:

transformers
sentencepiece
datasets
scikit-learn
pandas
nltk
tqdm
pyyaml
matplotlib
torch
boto3
fastapi


Install all dependencies with:

pip install -r requirements.txt


Now, we will create a template Python file (template.py) to automate the creation of our project structure. Start by importing necessary modules:

import os
from pathlib import Path
import logging


Set up basic logging to monitor the creation of directories and files:

logging.basicConfig(level=logging.INFO, format='%(asctime)s - %(levelname)s - %(message)s')


Define the project structure for TextSummarizer. We will create folders and files like:

__init__.py in project root and subfolders

components/__init__.py

utils/logging.py

config/config.yaml, params.yaml

pipeline/, entity/ folders with __init__.py

app.py, main.py, Dockerfile, requirements.txt

research/research.ipynb

Use the following logic to create files if they do not exist:

list_of_files = [
    ".gitkeep",
    "__init__.py",
    "components/__init__.py",
    "utils/logging.py",
    "config/config.yaml",
    "params.yaml",
    "app.py",
    "main.py",
    "Dockerfile",
    "requirements.txt",
    "research/research.ipynb"
]

for file_path in list_of_files:
    file_path = Path(file_path)
    if not file_path.parent.exists():
        os.makedirs(file_path.parent)
    if not file_path.exists() or file_path.stat().st_size == 0:
        with open(file_path, 'w') as f:
            pass  # Creating empty file
        logging.info(f"Created file: {file_path}")
    else:
        logging.info(f"File already exists: {file_path}")


After creating the template, run it:

python template.py


This will automatically generate the entire project structure including folders and empty files.

Next, create a .gitignore file to exclude certain folders from Git tracking, for example, venv/ and artifacts/. All remaining files will be tracked. Then, add the files to Git, commit, and push to your GitHub repository:

git add .
git commit -m "Project structure"
git push origin main


At this point, the requirements.txt installation should be completed as well. We now have a clean project structure ready for further implementation.

In the next tutorial, we will focus on logging and common functionalities. This includes functions to read YAML files, write outputs, and define shared utilities for our project. This will form the core of the TextSummarizer source folder.

So far, we have successfully:

Created and cloned the GitHub repository.

Set up a Conda environment and installed all required packages.

Built a template script to automatically generate the project folder structure.

Configured Git for version control and pushed the initial project structure.

This completes the project structure setup. In the next video, we will implement logging and the common functionalities that will help manage configurations, data loading, and model interactions.

**3. Logging And Utils Common Functionalities**

In this video, we are going to implement our logging functionalities and define the utils common functionalities that will be used throughout this project. First, navigate to the src folder inside TextSummarizer. Here, we already have a logging folder. Open the __init__.py file inside this folder to implement our custom logging functionality.

Start by importing the necessary libraries:

import os
import sys
import logging


For Python logging, there are three important steps. First, define the logging directory. For this project, we will create a folder named logs at the project root:

log_dir = "logs"
os.makedirs(log_dir, exist_ok=True)


Next, define a logging format string that includes the time, log level, module, and message:

log_format = "%(asctime)s - %(levelname)s - %(name)s - %(message)s"
log_file_path = os.path.join(log_dir, "logs.log")


Now, set up the logging configuration using both a file handler and a stream handler to display logs in the terminal as well as write them to the log file:

logging.basicConfig(
    level=logging.INFO,
    format=log_format,
    handlers=[
        logging.FileHandler(log_file_path),
        logging.StreamHandler(sys.stdout)
    ]
)


This completes our custom logging setup. To test it, open the main.py file. First, import the logger and define it:

from src.text_summarizer.logging import logging

logger = logging.getLogger("SummarizerLogger")
logger.info("Logging is implemented")


Run the file in your active venv environment:

python main.py


You should see log messages in the terminal, and the logs folder will contain a logs.log file with all messages. This confirms that our custom logging functionality is working.

Next, we will define common functionalities inside utils/common.py. Import the necessary libraries:

import os
from box.exceptions import BoxValueError
import yaml
from src.text_summarizer.logging import logger
from ensure import ensure_annotations
from box import ConfigBox
from pathlib import Path
from typing import Any


The first common functionality we implement is reading YAML files. Using ConfigBox allows us to access dictionary values using dot notation instead of key indexing. For example:

dict_info = {"name": "Krish", "last_name": "Nayak"}
dict_info = ConfigBox(dict_info)
print(dict_info.name)  # Output: Krish


We also use ensure_annotations to enforce type checking for function inputs. For example, a multiplication function:

@ensure_annotations
def multiplication(x: int, y: int) -> int:
    return x * y

multiplication(2, 3)  # Output: 6
multiplication(2, "3")  # Raises error: argument y of type str


This ensures that all functions receive inputs of the correct type, which is critical for robust project code.

Now, the function to read YAML files can be implemented as:

@ensure_annotations
def read_yaml(path_to_yaml: Path) -> ConfigBox:
    try:
        with open(path_to_yaml) as yaml_file:
            content = yaml.safe_load(yaml_file)
        return ConfigBox(content)
    except BoxValueError as e:
        logger.error(f"Error reading YAML file at {path_to_yaml}: {e}")
        raise e


Another common functionality is creating directories:

@ensure_annotations
def create_directories(path_to_directories: list, verbose=True):
    for path in path_to_directories:
        os.makedirs(path, exist_ok=True)
        if verbose:
            logger.info(f"Directory created at: {path}")


These two functions—reading YAML files and creating directories—will be heavily used throughout the project for configuration management and project setup.

With these implementations, our logging and common utilities are ready. In the next video, we will explore which Hugging Face model we are going to use and the dataset for our text summarization project.

**4. Finetuning HuggingFace Models In Google Colab**

So far, we have completed the common functionalities and created the project structure with template.py. Along with that, we have implemented logging and some common utility functions such as reading YAML files, creating directories, and other helper functions.

The next step is to demonstrate how to work with Hugging Face models using Jupyter Notebook. Specifically, I will show you how to fine-tune a pre-trained model on our dataset.

Setting up Google Colab

Open Google Colab.

Open the file text_summarized.ipynb from the research folder in the project.

Change the runtime to GPU:

If you have a paid Colab account, select L for GPU.

Otherwise, select T for GPU.

Save and connect the runtime.

Once connected, we will use the Google Pegasus CNN/DailyMail model for text summarization. The dataset we will use has three fields:

dialogue: The text of the conversation

summary: Human-written summary of the dialogue

unique ID: Unique identifier for the example

The dataset is split into train, validation, and test sets.

Loading and Using the Model

Since Pegasus is a sequence-to-sequence model, we need:

Tokenizer – to convert text into tokens compatible with the model.

AutoModelForSeq2SeqLM – to load the pre-trained sequence-to-sequence model.

We will also use the Hugging Face transformers library, along with datasets, evaluate, and accelerate.

Accelerate is particularly important because:

It enables multi-device training (multiple GPUs or TPUs) with minimal code changes.

Supports mixed precision for faster training and reduced memory usage.

Provides Zero Redundancy Optimizer (ZeRO) for efficiently handling large models.

Preparing the Dataset

Download and unzip the dataset from the GitHub link using wget.

Load the dataset using datasets.load_from_disk.

Check dataset details: number of rows, features, and example dialogues & summaries.

For fine-tuning, we need to convert the data into tokenized features:

input_ids: Token IDs for dialogues

attention_mask: Attention mask for the model

labels: Token IDs for target summaries

We apply tokenization to the train, validation, and test sets.

Data Collator

The DataCollatorForSeq2Seq helps:

Batch the data efficiently

Prepare it for model training

We initialize it with the tokenizer and model.

Training the Model

We define TrainingArguments and the Trainer:

output_dir: Where to save checkpoints

num_train_epochs: 1 (just for demonstration)

per_device_train_batch_size: 1

evaluation_strategy: steps

logging_steps: 10

weight_decay: 0.01

The Trainer takes:

model

args

train_dataset and eval_dataset

data_collator

tokenizer

Then we start training using trainer.train().

Evaluation

For evaluation, we:

Split the data into smaller batches for efficient processing.

Use the generate method of the model to produce summaries.

Decode the tokenized summaries back into text.

Calculate metrics like ROUGE-1, ROUGE-2, ROUGE-L, and BLEU.

Scores close to 1 indicate a strong overlap between generated and reference summaries.

Scores between 0.5–0.7 indicate moderate overlap.

Scores below 0.5 indicate poor match (expected here since we trained for only 1 epoch).

Saving the Model

After training, we save:

The model: model.save_pretrained("Pegasus_Samsung")

The tokenizer: tokenizer.save_pretrained("Pegasus_Samsung")

Later, we can reload them and create a pipeline for generating summaries with custom parameters like:

max_length

length_penalty

Example usage:

from transformers import pipeline

summarizer = pipeline("summarization", model="Pegasus_Samsung", tokenizer="Pegasus_Samsung")
summary = summarizer("Your text here", max_length=128, length_penalty=1.0)

Summary

We learned how to load a pre-trained Hugging Face model (Google Pegasus)

Tokenize and prepare a custom dataset

Fine-tune the model for one epoch

Evaluate using ROUGE metrics

Save and reload the model for inference

This approach is generic and can be applied to any Hugging Face model.

In the next session, we will focus on implementing the end-to-end solution using this trained model.

**5. Data Ingestion Implementation- Part 1**

Hello everyone! In this session, we will continue building an end-to-end project using the Hugging Face API. Previously, we created a Jupyter notebook where we trained a model and explored its parameters. The goal now is to convert that notebook into a modular, production-ready project. Our first step in this modular workflow is data ingestion.

First, make sure you download your Jupyter notebook file (.ipynb) and upload it to your research folder. Rename it to something like text_summarizer.ipynb. This notebook contains all previous steps, which we will now convert into modular code. The final project workflow will include components such as data ingestion, data transformation, model training, model evaluation, pipeline creation, and deployment. We will define configurations, classes, and reusable modules so that the project can scale and be production-ready.

To manage the workflow, we create a config.yaml file that holds paths, directories, and artifact locations. For example, for data ingestion, the config.yaml might include: "artifacts_root: artifacts", "data_ingestion:", " root_dir: artifacts/data_ingestion", " source_URL: <your-dataset-URL>", " local_data_file: artifacts/data_ingestion/data.zip", and " unzip_dir: artifacts/data_ingestion/unzip". This configuration allows us to define inputs and outputs of our modules clearly.

Next, we define a Python data class for data ingestion so that we can hold the configuration in a structured format. We use "from dataclasses import dataclass" and "from pathlib import Path", then define "@dataclass class DataIngestionConfig:" with fields "root_dir: Path", "source_URL: Path", "local_data_file: Path", and "unzip_dir: Path". This ensures that our data ingestion component knows exactly where to read inputs and where to write outputs.

We then create a Configuration Manager to read these YAML files and initialize directories. The Configuration Manager uses "self.config = read_yaml(config_path)" and "self.params = read_yaml(params_path)" to load the files and "create_directories([self.config.artifacts_root])" to ensure the artifact folder exists. To get data ingestion configuration, we define a method "def get_data_ingestion_config(self) -> DataIngestionConfig:" which reads "cfg = self.config.data_ingestion" and returns "DataIngestionConfig(root_dir=cfg.root_dir, source_URL=cfg.source_URL, local_data_file=cfg.local_data_file, unzip_dir=cfg.unzip_dir)".

Once the configuration manager is ready, we implement the Data Ingestion component. This component first downloads the dataset if it does not exist by checking "if not os.path.exists(self.config.local_data_file): urllib.request.urlretrieve(self.config.source_URL, self.config.local_data_file)", and logs "logger.info(f'File downloaded: {self.config.local_data_file}')". If the file already exists, it logs "File already exists". Next, it extracts the zip file into the specified folder using "os.makedirs(self.config.unzip_dir, exist_ok=True)" and "with zipfile.ZipFile(self.config.local_data_file, 'r') as zip_ref: zip_ref.extractall(self.config.unzip_dir)".

Finally, to execute the data ingestion, we initialize the configuration manager and the component. "config_manager = ConfigurationManager()", then "data_ingestion_config = config_manager.get_data_ingestion_config()". Next, we initialize the component with "data_ingestion = DataIngestion(config=data_ingestion_config)" and call the methods "data_ingestion.download_file()" and "data_ingestion.extract_zip()". After execution, the artifacts folder contains the downloaded zip file and the extracted dataset, including train, test, and validation CSV files.

With this approach, we have implemented a modular data ingestion module that can be reused and scaled. In the next steps, we can create additional modules such as data transformation, model training, model evaluation, and pipelines in a similar modular way, following industry-standard practices.

**6. Data Ingestion Implementation- Part 2**

Hello guys! Today, we are going to continue the discussion with respect to data ingestion. Already, in part one, we designed an entire Jupyter notebook wherein we executed every step sequentially. Our aim was to generate the artifact folder, and currently, we have successfully created it. In the next step, I am going to convert the entire Jupyter notebook into modular Python code using .py files. We will follow the same steps that we previously implemented in the notebook. The first step involves updating the config.yaml file, which is already done, so no action is required here. Next, we usually update params.yaml; however, for data ingestion, this is not required at this stage.

Moving forward, we need to update the config entity. This is a crucial step because the config entity defines the structure for our data ingestion configuration. In the source folder, inside the entity package, there is an __init__.py file. You can either create a new file like config_entity.py or directly use the existing one. Inside this entity file, we first define a data class as follows: "from dataclasses import dataclass" and "from pathlib import Path", then "@dataclass class DataIngestionConfig:" with fields "root_dir: Path", "source_URL: Path", "local_data_file: Path", and "unzip_dir: Path". This ensures that our component knows where to read inputs and where to store outputs.

The next step involves updating the configuration manager, which is located in src/config/configuration.py. Here, we update libraries and import the DataIngestionConfig from the entity package using "from src.textSummarizer.entity import DataIngestionConfig". The configuration manager reads the config.yaml and returns the DataIngestionConfig using a method "def get_data_ingestion_config(self) -> DataIngestionConfig:" which retrieves the paths for local files, unzip directories, and the source URL.

Once the configuration manager is ready, we move on to implement the data ingestion component. Inside the components folder, we create a file named data_ingestion.py. This file contains a class DataIngestion which has two primary functionalities: "download_file" and "extract_zip". The download_file method checks if the file already exists: "if not os.path.exists(self.config.local_data_file): urllib.request.urlretrieve(self.config.source_URL, self.config.local_data_file)" and logs "logger.info(f'File downloaded: {self.config.local_data_file}')". If the file exists, it logs "File already exists". The extract_zip method extracts the downloaded file to the specified directory using "os.makedirs(self.config.unzip_dir, exist_ok=True)" and "with zipfile.ZipFile(self.config.local_data_file, 'r') as zip_ref: zip_ref.extractall(self.config.unzip_dir)". The component imports the configuration using "from src.textSummarizer.entity import DataIngestionConfig".

After creating the data ingestion component, we proceed to create the pipeline. Inside the pipeline folder, we create data_ingestion_pipeline.py for stage one of the pipeline. We import the configuration manager and the data ingestion component using "from src.textSummarizer.config.configuration import ConfigurationManager" and "from src.textSummarizer.components.data_ingestion import DataIngestion". A class DataIngestionTrainingPipeline is created with an "__init__" method and a function "initiate_data_ingestion(self):" that initializes the configuration manager, fetches the data ingestion configuration, creates a DataIngestion object, and executes "download_file" and "extract_zip".

Finally, we test the pipeline in main.py. We import the pipeline using "from src.textSummarizer.pipeline.data_ingestion_pipeline import DataIngestionTrainingPipeline" and the logger using "from src.textSummarizer.logging import logger". We define a constant for the stage name: "STAGE_NAME = 'Data Ingestion Stage'". Using a try-except block, we log "logger.info(f'Stage {STAGE_NAME} initiated')" and execute the pipeline: "data_ingestion_pipeline = DataIngestionTrainingPipeline()" and "data_ingestion_pipeline.initiate_data_ingestion()". Upon completion, we log "logger.info(f'Stage {STAGE_NAME} completed')". Any exceptions are caught and logged using "logger.exception(e)" and then raised again using "raise e".

After setting up everything, we can delete the existing artifact folder to test the pipeline afresh and run the main file using "python main.py". If everything is set up correctly, the dataset file will download, the zip file will extract, and the artifact folder will be created automatically. This modular approach ensures a reusable and production-ready data ingestion pipeline. Finally, we can commit all files to the repository using "git add ." followed by "git commit -m 'Data ingestion completed'" and "git push origin main".

In the next session, we will continue with the data transformation module, following the same modular approach, converting the Jupyter notebook steps into .py files. The methodology will be identical to the data ingestion process, ensuring that all steps from configuration to pipeline execution are fully automated.

**7. Data Transformation Implementation**

Hello guys! Today, we are going to continue the discussion with respect to our end-to-end project using the Hugging Face API. In our previous video, we implemented the data ingestion part, and now we proceed to implement data transformation, which is essentially feature engineering. In the text_summarizer notebook, we performed preprocessing by converting each feature with the help of a tokenizer, creating three essential inputs for the model: input_ids, attention_mask, and labels. We need to integrate the same process into our modular end-to-end project. First, in the research folder, we create a new notebook named 2__data_transformation.ipynb, select the kernel, and test it with simple code to ensure it’s running correctly.

We begin by importing the OS module and checking the current working directory using "import os" and "os.getcwd()". We navigate to the parent folder with "os.chdir('..')" to make sure we are in the text_summarizer root directory. Next, we update the config.yaml file for data transformation, specifying three important fields: the root_dir for the artifact folder, the data_path for input data, and the tokenizer_name for the Hugging Face tokenizer. After updating the config, we proceed to define a data class for the data transformation config using "from dataclasses import dataclass" and "from pathlib import Path". We create "@dataclass class DataTransformationConfig:" with fields "root_dir: Path", "data_path: Path", and "tokenizer_name: Path" to hold configuration parameters for the transformation component.

Next, we implement the configuration manager by importing "from src.textSummarizer.constants import *" and "from src.textSummarizer.utils.common import read_yaml, create_directories". We define a function "def get_data_transformation_config(self) -> DataTransformationConfig:" that reads the YAML file, creates directories with "create_directories(config.root_dir)", and returns an instance of DataTransformationConfig with values "root_dir=config.root_dir", "data_path=config.data_path", and "tokenizer_name=config.tokenizer_name". This ensures that all paths and tokenizer details are properly initialized.

After setting up the configuration, we implement the data transformation component. We import the required libraries: "import os", "from src.textSummarizer.logging import logger", "from transformers import AutoTokenizer", and "from datasets import load_from_disk". We create a class "class DataTransformation:" with an "__init__" method that initializes the configuration and tokenizer using "self.config = config" and "self.tokenizer = AutoTokenizer.from_pretrained(config.tokenizer_name)". Then, we implement the function "def convert_example_to_features(self, example_batch):" which uses the tokenizer to convert examples into features, returning the input_ids, attention_mask, and labels. We also define a "convert" method which loads the dataset with "dataset = load_from_disk(self.config.data_path)", applies the convert_example_to_features function using "dataset.map(self.convert_example_to_features)", and saves the transformed dataset to disk as "dataset.save_to_disk(os.path.join(self.config.root_dir, 'samsum_dataset'))". This ensures that all transformed features are properly stored for training.

Once the component is implemented, we create a pipeline. In the pipeline folder, we create a new file "stage_two_data_transformation_pipeline.py". Similar to data ingestion, we import the configuration manager and the data transformation component using "from src.textSummarizer.config.configuration import ConfigurationManager" and "from src.textSummarizer.components.data_transformation import DataTransformation". We define a class "class DataTransformationTrainingPipeline:" with an "__init__" method and a function "initiate_data_transformation(self):" which initializes the data transformation component using "config = ConfigurationManager().get_data_transformation_config()" and "data_transformation = DataTransformation(config)". We then call "data_transformation.convert()" to perform the mapping and save the dataset.

Finally, in main.py, we integrate this stage by adding a new stage for data transformation. We import the pipeline using "from src.textSummarizer.pipeline.stage_two_data_transformation_pipeline import DataTransformationTrainingPipeline". We define a stage name "STAGE_NAME = 'Data Transformation Stage'" and use a try-except block to log "logger.info(f'Stage {STAGE_NAME} initiated')" and execute the pipeline using "data_transformation_pipeline = DataTransformationTrainingPipeline()" and "data_transformation_pipeline.initiate_data_transformation()". After completion, we log "logger.info(f'Stage {STAGE_NAME} completed')".

To test the end-to-end pipeline, we delete the existing artifact folder for data transformation and run "python main.py" in the terminal. This executes both the data ingestion and data transformation stages, creating the transformed dataset with input_ids, attention_mask, and labels saved in the artifact folder. Logs are also generated, and we can optionally add them to .gitignore. Finally, we commit all changes using "git add .", "git commit -m 'Data transformation completed'", and "git push origin main".

This completes the data transformation stage in our Hugging Face end-to-end project. The next step will be implementing the model trainer, following the same modular approach as data ingestion and data transformation. All components are now integrated and ready for the next stage of the pipeline.

**8. Model Trainer Implementation**

In this stage of our end-to-end project, we focus on model training. We begin by creating a new notebook, model_trainer.ipynb, which will host all the training code for our model. The first step is to import essential libraries such as os and Pathlib, set the working directory to the project root, and ensure that all paths are correctly configured. This sets the stage for consistent execution and proper organization of outputs.

Next, we update our config.yaml to include key information required for the model trainer: the root directory, the path to the processed data from the data transformation stage, and the Hugging Face model checkpoint that we will use as a pre-trained model. Alongside this, we modify params.yaml to define our training parameters, including the number of epochs, warmup steps, weight decay, logging frequency, evaluation strategy, save steps, and gradient accumulation steps. This approach ensures flexibility, allowing us to adjust training parameters without altering the core code.

With configurations in place, we create a Model Trainer configuration class using Python’s dataclass. This class holds all necessary variables for training, including paths and hyperparameters. Data types are carefully matched to the values in params.yaml to avoid type-related errors. We then implement a configuration manager that reads both the config.yaml and params.yaml, creates necessary artifact directories for storing outputs, and returns a fully initialized ModelTrainerConfig object. This modular approach helps keep the training pipeline organized and reusable.

For the training process itself, we initialize the tokenizer and model from Hugging Face using the model checkpoint specified in our configuration. We also define a data collator for sequence-to-sequence tasks and load the training dataset from disk. Training arguments are set according to our parameters, either by reading from the configuration or hardcoding them temporarily for testing. The Trainer object is initialized with the model, tokenizer, data collator, and training arguments, and training is initiated by calling trainer.train(). After training completes, the model and tokenizer are saved to the artifact directory, ready for downstream evaluation and inference.

Since training on a local CPU can be very slow, we recommend performing training on a GPU-enabled environment such as Google Colab, and then downloading the saved model and tokenizer files into the local project directory. This approach significantly reduces training time and ensures reproducibility. Once the model is saved, the notebook code can be modularized: the ModelTrainerConfig class is placed in the entity module, the configuration manager is updated, and the training code is moved to a model_trainer.py component in the components folder. A dedicated Model Trainer pipeline is created in the pipeline module to orchestrate configuration initialization, model training, and artifact storage. Finally, the main script is updated to include this stage in the end-to-end workflow.

By the end of this stage, we have a fully trained model stored in our artifact directory, along with a tokenizer, ready to be evaluated in the next stage. We also ensure proper version control by committing and pushing the changes to the repository, while excluding large model files from Git using .gitignore. This completes the model training stage of our pipeline, setting the foundation for evaluation and deployment.

**9. Model Evaluation Implementation**

In the final stage of our pipeline, we focus on model evaluation. This step is crucial because it allows us to measure the performance of the trained model on a test dataset and record all relevant metrics. We begin by creating a new Jupyter notebook called model_evaluation.ipynb inside the research folder. After selecting the kernel and running a simple sanity check like 1 + 1, we ensure the environment is ready. Next, we import the os module and verify the current working directory using os.getcwd() to confirm we are inside the research folder. At this point, we organize our workspace by closing unnecessary files and preparing to set up the evaluation configuration.

The first step in preparation is to update the config.yaml file to include all paths relevant for model evaluation. This includes the root_dir, data_path (pointing to the dataset), model_path (pointing to the trained model saved during training), tokenizer_path, and metric_file_path where evaluation results will be stored. For example, inside our config.yaml, we add entries like: "model_path: artifacts/model_trainer/model" and "metric_file_path: artifacts/model_evaluation/metrics.csv". With this in place, we create a Model Evaluation Config class using Python’s dataclass to hold all these paths and configurations: "@dataclass class ModelEvaluationConfig: root_dir: Path; data_path: Path; model_path: Path; tokenizer_path: Path; metric_file_path: Path".

After setting up the configuration class, we proceed to create a configuration manager. This manager reads all paths from the YAML file and ensures necessary directories exist using a utility function like "create_directory([config.root_dir, config.model_path, config.tokenizer_path])". This step provides a centralized way to manage configurations and avoids hardcoding paths throughout the evaluation pipeline. Once the configuration manager is ready, we move to the model evaluation component, which will handle actual performance measurement.

The evaluation component begins by importing all necessary libraries, including "import evaluate". Unlike training, we do not need to import load_dataset, because we only need the test data and metrics evaluation. Using the trained model and tokenizer from the artifacts folder, we define a helper function to generate batches from the dataset, for example: "def generate_batches(dataset, batch_size): for i in range(0, len(dataset), batch_size): yield dataset[i:i+batch_size]". Next, we define the calculate metrics function, which iterates over the test dataset batches, runs inference using the model, and calculates relevant metrics using the evaluate library. For example, "metric = evaluate.load('rouge'); result = metric.compute(predictions=preds, references=refs)".

Once metrics are calculated, we save them in a CSV file using "pd.DataFrame([metrics]).to_csv(config.metric_file_path, index=False)". The evaluation component also includes an evaluate function, which orchestrates the whole process: loading the model, tokenizer, and dataset, running inference, calculating metrics, and saving them to the artifact folder. This ensures that the evaluation is reproducible and modular. Any temporary errors, like rogue metrics referenced before assignment, are resolved by calling the functions correctly within the class or using appropriate variable scopes.

After defining the component, we move on to the pipeline integration. A dedicated model_evaluation.py file is created in the components folder, where we copy the entire evaluation logic. This file imports the ModelEvaluationConfig from entity, the configuration manager, and utility functions. Then, a training pipeline module is updated to include a new method like "def initiate_model_evaluation(self): config = ConfigurationManager().get_model_evaluation_config(); evaluator = ModelEvaluation(config); evaluator.evaluate()". Finally, the main.py is updated to include the model evaluation stage as stage four: "from components.model_evaluation_pipeline import ModelEvaluationTrainingPipeline; pipeline = ModelEvaluationTrainingPipeline(); pipeline.initiate_model_evaluation()".

Executing python main.py runs the entire pipeline including model evaluation. The evaluation loads the trained model from the artifacts folder, performs inference on the test dataset, calculates performance metrics such as ROUGE scores, and saves the results in "artifacts/model_evaluation/metrics.csv". While this process may take some time on CPU, using GPU (e.g., in Google Colab) significantly speeds up inferencing. After this stage, we have a fully modularized pipeline with reproducible model evaluation, and the metrics can be used for reporting or further analysis. This completes the model evaluation stage, setting the stage for deployment and API integration in the final step of the project.

**10. Prediction Pipeline And API Integration**

In this final stage, we focus on creating the prediction pipeline and building a front-end API using FastAPI to interact with our text summarization model. The first step is to create a new file called prediction_pipeline.py inside the src/text_summarizer/pipeline folder. This pipeline will handle loading the trained model and tokenizer, preparing the input text, running inference, and returning the summarized text. For instance, we import the configuration manager to get paths and parameters: "from src.text_summarizer.config.configuration_manager import ConfigurationManager". Next, we initialize the pipeline using the trained tokenizer and model paths stored in the artifacts folder, for example: "tokenizer = AutoTokenizer.from_pretrained(config.tokenizer_path); model = AutoModelForSeq2SeqLM.from_pretrained(config.model_path)".

Once the model and tokenizer are loaded, we define a prediction function that takes an input text and runs it through the model. This function creates a summarization pipeline using Hugging Face's pipeline class: "summarizer = pipeline('summarization', model=model, tokenizer=tokenizer)". The function then takes a text string and outputs the summarized result, which can be printed or returned. For example: "result = summarizer(input_text, max_length=150, min_length=50, do_sample=False); return result[0]['summary_text']". The logic of this function mirrors what we had already implemented in the text_summarizer.ipynb notebook, ensuring consistency between the notebook and the modular pipeline.

With the prediction pipeline ready, we move on to creating the FastAPI app to serve our model as an API. We start by importing FastAPI and our prediction pipeline: "from fastapi import FastAPI; from src.text_summarizer.pipeline.prediction_pipeline import PredictionPipeline". Then we initialize the FastAPI app: "app = FastAPI()". We create a home route ("/") to test if the API is running, and define a route for training ("/train") which calls our main training script: "@app.post('/train'); def train(): os.system('python main.py'); return {'status': 'Training started'}". While training via API is optional, this demonstrates the modularity and control FastAPI provides.

Next, we define the prediction route ("/predict"), which takes a text input, calls the prediction function from our pipeline, and returns the summarized output. For example: "@app.post('/predict'); def predict(text: str): obj = PredictionPipeline(); summary = obj.predict(text); return {'input': text, 'summary': summary}". This allows any front-end or client to send a POST request with a text payload and receive a summarized result in JSON format. The route is fully functional and mimics the notebook workflow but in a scalable, modular API format.

Finally, we run the FastAPI server using Uvicorn from the command line: "uvicorn app:app --host 127.0.0.1 --port 8080 --reload". Once the server is running, we can navigate to http://127.0.0.1:8080/docs to see the automatically generated Swagger UI, which provides a simple interface to test both the training and prediction endpoints. For testing, we can input a string like "What is text summarization?" in the /predict endpoint and get the summarized response returned by the model. Longer text, such as a small story, can also be tested to see how the model performs on more substantial inputs.

After testing, we commit our code to Git for version control. We use commands like "git add .; git commit -m 'Implemented prediction pipeline and FastAPI endpoints'; git push origin main". This ensures that the entire project—including the prediction pipeline and API—can be deployed or shared easily. The API serves as a front-end for users to interact with the model, providing a practical and end-to-end implementation for text summarization, from training to inference and real-time API-based predictions.
