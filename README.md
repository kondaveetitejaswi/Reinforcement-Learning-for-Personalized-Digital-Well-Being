# Reinforcement-Learning-for-Personalized-Digital-Well-Being
This project aims to develop an AI-driven digital well-being system that leverages Reinforcement Learning (RL) to promote healthier social media usage and improve mental well-being. By analyzing user habits, preferences, and digital behaviours, the system assigns a Mental Health Score (MHS) and dynamically suggests personalized interventions to reduce excessive screen time, encourage offline activities, and foster healthier digital habits.

The RL agent learns from user feedback, optimizing recommendations such as taking breaks, engaging in hobbies, reading, or limiting social media exposure. The project also incorporates gamification elements, including streaks, rewards, and progress tracking, to motivate users toward sustained behaviour change.

## Data Structuring for Reinforcement Learning Implementation
The raw data was taken from the Google sheets which was linked with the survey form.\\
This data was including the responses to all the questions inluding the Timestamp of response and the consent approval. This raw data can be found in [Survey_ Effect of social media on youth and teenagers (Responses) - Form Responses 1](https://github.com/kondaveetitejaswi/Reinforcement-Learning-for-Personalized-Digital-Well-Being/blob/main/Survey_%20Effect%20of%20social%20media%20on%20youth%20and%20teenagers%20(Responses)%20-%20Form%20Responses%201.csv)

This Raw data was preprocessed in the notebook: [Data structuring for RL](https://github.com/kondaveetitejaswi/Reinforcement-Learning-for-Personalized-Digital-Well-Being/blob/main/Data%20structuring%20for%20RL.ipynb)
The 3 main steps in the notebook are:
* Conversion of Categorical text data into Numerical Data.
* Conversion of Multi valued text data into separate numerical data columns of binary values.
* Word Embedding through vectorizer for the custom response textual data. The top 100 words are considered as our dataset was small and had only 128 entries(responses).
This structured data is saved as [Structured survey data for RL implementation](https://github.com/kondaveetitejaswi/Reinforcement-Learning-for-Personalized-Digital-Well-Being/blob/main/Structured%20survey%20data%20for%20RL%20implementation.csv).