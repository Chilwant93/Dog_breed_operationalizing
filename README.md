# Dog_breed_operationalizing
First, find and downloaded starter files, which are located in the Resources section for this project lesson. The starter file called ****train_and_deploy-solution.ipynb**** is a Jupyter notebook that trains and deploys a computer vision model. The starter file called ****hpo.py**** is the "entry point" for the train_and_deploy-solution.ipynb notebook.  Upload both of these files to a Sagemaker instance and run them there, using Jupyter or JupyterLab.
![alt text](https://github.com/LittleAlchemy/Dog_breed_operationalizing/raw/main/snapshots/notebook%20instatnce.png?raw=true)

# Download data to an S3 bucket
The first three cells of the train_and_deploy-solution.ipynb will download data to AWS workspace. The third cell copies the data to an S3 bucket. set up an S3 bucket that copy the data to.

After setttin up an S3 bucket, 

After setting up an S3 bucket, need to change some cells in the ****train_and_deploy-solution.ipynb notebook****.

![alt text](https://github.com/LittleAlchemy/Dog_breed_operationalizing/raw/main/snapshots/Dataset%20s3.png?raw=true)

After changing all of these references, prepared to run the first three cells of  ****train_and_deploy-solution.ipynb**** notebook. Run these cells to download training and validation data for the project's ML pipeline.
# EC2 Setup
After completing Step 1, the notebook that completes model training and deployment on Sagemaker. The next step is to set up an EC2 instance and accomplish model training there.

![alt text](https://github.com/LittleAlchemy/Dog_breed_operationalizing/raw/main/snapshots/Ec2.png?raw=true)

After training and deploying the model, setting up a Lambda function is an important next step. Lambda functions enable the model and its inferences to be accessed by API's and other programs, so it's a crucial part of production deployment.
# Setting up a Lambda function
set up a Lambda function that uses Python 3 for its runtime. In the same starter files downloaded in Step 1 of this project lesson,  also find starter code for Lambda function, in a file called lambdafunction.py. This file contains some of the basic Python code for a Lambda function, but ou need to make an important adjustment to it:

Change the endpoint_name variable, to give it the same name as the endpoint deployed in Step 1. find the name of this endpoint in the "Inference > Endpoints" section of Sagemaker.

![alt text](https://github.com/LittleAlchemy/Dog_breed_operationalizing/raw/main/snapshots/lambda%20success.png?raw=true)
# Cocurrancy and Auto scaling
Because reserved concurrency is free and meets our present needs, I chose it over shared concurrency. Furthermore, we are unlikely to handle more than a few requests per endpoint instance at any given time, as this would indicate that the latter is overloaded, so a value that is a multiple of the number of endpoint instances makes sense, so I chose 100, which allows for 20 requests per endpoint instance. I choose to scale the endpoint to between one and five instances. While this is unlikely to ever be an issue, because each forecast takes about 0.25 seconds, this should allow for about 20 requests per second, which, along with appropriaterequest throttling, should allow for a large number of individuals to utilise the service.
![alt text](https://github.com/LittleAlchemy/Dog_breed_operationalizing/raw/main/snapshots/concurrancy.png?raw=true)
