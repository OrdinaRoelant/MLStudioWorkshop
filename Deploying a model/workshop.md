This workshop is based on the Microsoft tutorials for learning to deploy a model in Azure Machine Learning Studio.

This workshop contains three distinct tasks that will help you with understanding the moving parts when:
1) [Training a model](https://github.com/OrdinaRoelant/MLStudioWorkshop/blob/master/Training%20a%20model/workshop.md)
2) [**Deploying a model**](https://github.com/OrdinaRoelant/MLStudioWorkshop/blob/master/Deploying%20a%20model/workshop.md)
3) [Running automated machine learning experiments](https://github.com/OrdinaRoelant/MLStudioWorkshop/blob/master/Running%20auto%20ML%20experiments/workshop.md)

In this part we are going to deploy a model by:

✔ Create a real-time inference pipeline  
✔ Create an inferencing cluster  
✔ Deploy the real-time endpoint  
✔ Test the real-time endpoint  

## Training a model
In this part of the workshop we are going to deploy the model we trained in [part 1](https://github.com/OrdinaRoelant/MLStudioWorkshop/blob/master/Training%20a%20model/workshop.md). Be sure to finish that part first, before continuing with the deployment part.

## Create a real-time inference pipeline  
To deploy your pipeline, you must first convert the training pipeline into a real-time inference pipeline. This process removes training components and adds web service inputs and outputs to handle requests.

1) Above the pipeline canvas, select **Create inference pipeline** > **Real-time inference pipeline**  
**NOTE**: The screen takes a couple of seconds to load  
![Result](images/create-inference-pipeline.png)  
Your pipeline now looks like this  
![Result](images/real-time-inference-pipeline.png)  
When you select **Create inference pipeline**, several things happen:
- The trained model is stored as a **Dataset** component in the component palette. You can find it under **My Datasets**.
- Training components like **Train Model** and **Split Data** are removed.
- The saved trained model is added back into the pipeline.
- **Web Service Input** and **Web Service Output** components are added. These components show where user data enters the pipeline and where data is returned.
2) Select **Submit**, and use the same compute target and experiment that you used in part one  
**NOTE:** Make sure the experiment run in done, before continuing with deploying the endpoint. While the experiment is running, the *Submit* button reads *Cancel run*.

## Deploy the real-time endpoint  
1) Select **Deploy**
2) Enter a name for the endpoint respecting the naming convention: [prefix]-endpoint
3) Select the **Azure Container Instance** as the **Compute type**
4) Select **Deploy**  
**NOTE:** A success notification above the canvas appears after deployment finishes. It might take a few up to 15 minutes.  
If you have navigated away from the canvas, you can view the status by clicking the bell icon in the top bar ![Bell](images/bell.png), or navigate to **Endpoints** in the navigation bar on the left and click on an endpoint.  

## Test the real-time endpoint  
After deployment finishes, you can view your real-time endpoint by going to the Endpoints page.  

1) On the **Endpoints** page, select the endpoint you deployed. 
In the **Details** tab, you can see more information such as the REST URI, Swagger definition, status, and tags  
In the **Consume** tab, you can find sample consumption code, security keys, and set authentication methods  
In the **Deployment logs** tab, you can find the detailed deployment logs of your real-time endpoint  
2) To test your endpoint, go to the **Test** tab. From here, you can enter test data and select Test verify the output of your endpoint  

## Wait, wut?
Of course this is a kind of happy flow path and real-world scenarios pose real-world problems, but it is good to realize what exactly we did the past two parts, we:

1) Created a pipeline through which we can train new versions of our model
2) Could fine-tune every step and add extra steps if necessary 
3) Created our first machine learning model that actually predicts values
4) Converted the training pipeline to an inferencing pipeline, making it possible to:
5) Deploy(ed) our machine learning model as a webservice in a Docker container, hosted as an Azure Container Instance  

Pretty cool, eh?  

In the case of the car prices prediction, you could have used [a ML cheat sheet](https://docs.microsoft.com/en-us/azure/machine-learning/algorithm-cheat-sheet){:target="_blank"} to pinpoint us in the correct family of algorithms, or maybe even the correct algorithm. However sometimes it is not so clear upfront and that is where part III comes in: [Running automated machine learning experiments](https://github.com/OrdinaRoelant/MLStudioWorkshop/blob/master/Running%20auto%20ML%20experiments/workshop.md)