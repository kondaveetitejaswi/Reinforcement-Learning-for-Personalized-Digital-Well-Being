# Reinforcement-Learning-for-Personalized-Digital-Well-Being
This project aims to develop an AI-driven digital well-being system that leverages Reinforcement Learning (RL) to promote healthier social media usage and improve mental well-being. By analyzing user habits, preferences, and digital behaviours, the system assigns a Mental Health Score (MHS) and dynamically suggests personalized interventions to reduce excessive screen time, encourage offline activities, and foster healthier digital habits.

The RL agent learns from user feedback, optimizing recommendations such as taking breaks, engaging in hobbies, reading, or limiting social media exposure. The project also incorporates gamification elements, including streaks, rewards, and progress tracking, to motivate users toward sustained behaviour change.

## Data Structuring for Reinforcement Learning Implementation
The raw data was taken from the Google sheets which was linked with the survey form.\\
This data included the responses to all the questions, including the Timestamp of the response and the consent approval. This raw data can be found in [Survey_ Effect of social media on youth and teenagers (Responses) - Form Responses 1](https://github.com/kondaveetitejaswi/Reinforcement-Learning-for-Personalized-Digital-Well-Being/blob/main/Survey_%20Effect%20of%20social%20media%20on%20youth%20and%20teenagers%20(Responses)%20-%20Form%20Responses%201.csv)

This Raw data was preprocessed in the notebook: [Data structuring for RL](https://github.com/kondaveetitejaswi/Reinforcement-Learning-for-Personalized-Digital-Well-Being/blob/main/Data%20structuring%20for%20RL.ipynb)
The 3 main steps in the notebook are:
* Conversion of Categorical text data into Numerical Data.
* Conversion of Multi valued text data into separate numerical data columns of binary values.
* Word Embedding through vectorizer for the custom response textual data. The top 100 words are considered as our dataset was small and had only 128 entries(responses).
This structured data is saved as [Structured survey data for RL implementation](https://github.com/kondaveetitejaswi/Reinforcement-Learning-for-Personalized-Digital-Well-Being/blob/main/Structured%20survey%20data%20for%20RL%20implementation.csv).

## Mental Health Score estimation
The next step was to use this structured data to estimate the Mental Health Scores. This is done in the notebook [Mental Health Scoring Estimation](https://github.com/kondaveetitejaswi/Reinforcement-Learning-for-Personalized-Digital-Well-Being/blob/main/Mental%20health%20score%20estimation.ipynb).

This notebook imports the structured survey data for the calculation of the Mental Health scores. For the calculation of the scores, the weights for each feature are defined based on the importance. The least importance was given to the TF_IDF and custom responses as this data was not perfectly structured with a lot of missing values and improperly filled responses by the user; including these features with a lower weight seemed to be a suitable method. The highest importance was given to the emotions, platforms used, etc. The _calculate mental health score_ function was defined to calculate the mental health scores based on the weights and outputs a data frame with all the Mental health scores in the dimensions: Emotional Score, Social Media Time score, Platform score, Usage pattern score, Impact score, Additional feature score, TFIDF score and Mental Health Score. This data frame was saved in a CSV format and the data can be found in the file [Mental_Health_Score_Dataframe](https://github.com/kondaveetitejaswi/Reinforcement-Learning-for-Personalized-Digital-Well-Being/blob/main/Mental_Health_Score_Dataframe.csv).

## RL model implementation and evaluation
The Mental health scores are now used to train the Reinforcement Learning Algorithm to give suggestions to the users based on their preferences and hobbies. This part of the project can be found in the notebook [RL_model_implementation](https://github.com/kondaveetitejaswi/Reinforcement-Learning-for-Personalized-Digital-Well-Being/blob/main/RL_model_implementation.ipynb).

The notebook includes:
* Importing the Mental Health Score Dataset
* Creating the Mental Health Environment using the Gymnasium open-source library. The environment includes the action suggestions, the effects of each action, the estimation of the current state from the data and the option to reset the environment after the estimation of one person is done.
* Training of the Models: Deep-Q Network (DQN) and the Action-2-Critic (A2C)
* A function to evaluate and compile the results of the model. The results include the mean value, standard deviation and suggestions for the user.

## Discussion
The result suggestions are the primary suggestions given by the model for the user based on their current state. The performance can be clearly analysed by analysing the suggestions: The DQN model suggests a similar action to most of the users, while the A2C uses a wider range of action suggestions for the user. This clarifies that the A2C model is better suited for this scenario for the suggestion purpose. The reason for this better performance by the A2C model could be because of the model's ability to handle long-term decision-making, which could be advantageous while focusing on the actions that lead to consistent improvements rather than short-term rewards.

## Future directions
This study can be further strengthened by incorporating additional steps, such as:
* Comparing with Baseline models
* Testing on the Real-World Data
* Deployment and User Interaction
