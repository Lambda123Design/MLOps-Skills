# MLOps-Skills

### Boto3 is an important Library when we want to work with AWS S3; Experiments will get saved in S3 Bucket and MLFlow server will pick it up from there

### Refer to - AWS Cloud EC2,IAM,S3 Bucket Set Up - 79th Video for AWS Setup

**A) Getting Started with MLFlow Tracking Server**

**B) MLFlow with AWS**

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
