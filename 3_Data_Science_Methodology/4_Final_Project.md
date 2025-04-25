# Final Project

#### Which topic did you choose to apply the data science methodology to? (2 points)

Hospitals

#### Prompt

##### Next, you will play the role of the client and the data scientist. 

##### Using the topic that you selected, complete the Business Understanding stage by coming up with a problem that you would like to solve and phrasing it in the form of a question that you will use data to answer. (3 points)

##### You are required to:

##### Describe the problem, related to the topic you selected.

##### Phrase the problem as a question to be answered using data.

##### For example, using the food recipes use case discussed in the labs, the question that we defined was, "Can we automatically determine the cuisine of a given dish based on its ingredients?".

In hospitals, medical imaging (such as X-rays) takes an extended amount of time. Can we automatically determine whether an X-ray image of a specific part of the body is normal or abnormal

#### Prompt
##### Briefly explain how you would complete each of the following stages for the problem that you described in the Business Understanding stage, so that you are ultimately able to answer the question that you came up with. (5 points):

##### Analytic Approach

##### Data Requirements

##### Data Collection

##### Data Understanding and Preparation

##### Modeling and Evaluation

##### You can always refer to the labs as a reference with describing how you would complete each stage for your problem.

1. Analytic Approach- We would have to follow medical professionals through their workflow as they analyze X-Rays.

2. Data Requirements- We would have to determine what types of data we may need to train a model to predict whether X-ray images are normal or not. For example, how many samples would we use? What parts of the body would we focus on?

3. Data Collection- We would collect the data as determined by the above step. For example, we may look for existing datasets of X-Ray images, or we may have to build our own.

4. Data Understanding and Preparation- We would have to ensure we understand what normal vs abnormal X-Rays look like. We would also have to prep data. For example, if we are using a CNN, we would have to ensure that all images are the same size.

5. Modeling and Evaluation- We would train our model on the data. Then, we would evaluate the model by seeing how accurately it can predict if an X-Ray image is abnormal or not on our test set, that we had not used while training the model.