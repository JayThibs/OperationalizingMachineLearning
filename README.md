# Udacity Machine Learning Engineer with Microsoft Azure Nanodegree

# Project - Operationalizing Machine Learning

In this project, we are going to configure, deploy, consume a model which is trained using Automated ML and consume the Endpoint. The Project also involves in creating, publishing, and consuming a pipeline.

## Architectural Diagram
![Architectural Diagram of the project](./screenshots/azure_automl_architectural_diagram.png)

In this project, we'll follow above steps, these are:

1. Authentication: As we were using udacity workspace so we can't do this step beacuse of we are not authorized to create a security principal.

2. Auto ML model: In this project we will configure the AutoML, train and find the best model.

3. Deploy the best model: In this step we use best model from step 2 and deploy it so others can use it.

4. Enable logging: After deploying we'll enable application insights to monitor and check logs of model behaviour.

5. Documentation: In this step we'll swagger document for the deployed model so that anyone can run using UI.

6. Consume model endpoints: In this step we'll write a python script in which we'll use the model endpoint get inference.

7. Create and publish a pipeline: In this step we'll create a pipeline of all step (excluding step 4 and 5) and publish it on Azure so that one can use pipeline on new data and run experiment doing manually.

## Key Steps
### Step 1: Authentication
**Since the entire experiment was executed in Udacity Provided Azure Workspace, the authentication step is already part of the setup and no additional step is added.** This is in accordance with the note in Project Guidelines.

### Step 2: Automated ML Experiment
- First we register the dataset on Azure ML.
![Registered dataset](./screenshots/2_dataset.png)

- After the dataset is registered, we configure AutoML for "Classification" objective and run the experiment. "VotingEnsemble" is the best model. Below is the image that tells the experiment of AutoML is completed.
![AutoML completion](./screenshots/2_automl_complete.png)

-  Below is the best model created by AutoML.
![Best model](./screenshots/2_automl_best_model.png)

- Below is the explanation of the best model, i.e. top 8 features.
![Explanation of best model](./screenshots/2_automl_best_model_explain.png)

### Step 3: Deploy the best model
- After getting the best mode, next step was to deploy it. Below is the image of succesful deployment of model.
![Best model deployed](./screenshots/3_automl_model_deploy.png)

- Below image give endpoint and application insights is disabled.
![Endpoint and AI disabled](./screenshots/3_automl_model_deploy_ai_false.png)

### Step 4: Enable logging
- To do this step we have to download congig.json file from our workspace and run the script "logs.py" (both files are included in the repository). After running the script we'll get logs, below is the image of the same.
![Logs 1](./screenshots/4_logs_1.png)
![Logs 2](./screenshots/4_logs_2.png)

- After model is deployed we have to enable "Application Insights" to view logs and monitor model.
![Application Insight enabled](./screenshots/4_deployed_ai_true.png)

- When "Application insights" is enabled we can go to the link provided and monitor model.
![Application Insight UI](./screenshots/4_deployed_ai_ui.png)

### Step 5: Documentation (Swagger)
- After enabling logging we'll create Swagger UI using "swagger.json" and 2 scripts (all files included in "swagger" folder).
![Swagger UI](./screenshots/5_swagger_ui.png)

- Our model payload.
![Model payload](./screenshots/5_swagger_payload.png)

- To run swagger we pulled swagger file from docker. Logs of same is below.
![Swagger docker pull logs](./screenshots/5_swagger_docker_pull.png)

### Step 6: Consume model endpoints
- After deployment of model we can consume it. To do it we used "endpoint.py" python script (included in the repository). We have to update model endpoint and key in the file.
![Consume model result](./screenshots/6_score_result.PNG)

### Step 7: Create and publish a pipeline
- After doing many thing manually like making AutoML configs, select compute target, train, etc we'll create a pipeline that can be used to do all those things and give the best model. To do this there is a jupyter notebook with code that tells how to do.
#### Pipeline created
![Pipeline created](./screenshots/7_pipeline_created.png)

#### Pipeline completed on Jupyter
![Pipeline completes on Jupyter](./screenshots/7_jupyter_step_runs.png)

#### Pipeline published
![Pipeline published](./screenshots/7_pipeline_published.png)

#### Published Pipeline Endpoint
![Pipeline endpoint](./screenshots/7_pipeline_endpoint.png)

#### Scheduled Pipeline Run
![Scheduled Pipeline Run](./screenshots/7_sheduled_run.png)

## Screen Recording
- If link is not working then, one can find video in repository in "video" folder. 
[Screencast link](https://drive.google.com/file/d/1r_CgNGdqX62BnslVC9iZEspJpQDt2VMj/view?usp=sharing)

## Standout Suggestions
In the future, the performance of the algorithm may be better if we have more data and run AutoML again. Also we need to run for more time after getting more data as of now there is less data and it looks it have high accuracy and it probably reached the possible limit performance.

Another possible improvement would be to try using Deep Learning, which is currently not used by AutoMl in the runs we tried.
