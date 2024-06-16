# At-Home-Thyroid-Diagnosis-Model

# Overview
This project applies machine learning to the field of medicine by trainig an automated diagnosis model for thyroid disorder detection. From a business perspective, such a predictive tool can be monetized through various avenues, including advertising, pharmaceutical sales related to thyroid medication, and future contract opportunities. Also, by offering individuals an easy-to-use tool to self-assess their thyroid disorder risk, they can become convinced to seek medical attention before symptoms worsen. This could lead to earlier diagnoses and more effective treatments, ultimately improving healthcare outcomes.

# What's the point?
Thyroid diseases such as hypothyroidism and hyperthyroidism pose a significant health concern globally, with their prevalence on the rise. Despite being among the most common hormone imbalance diseases, there is a notable absence of proactive research and diagnostic tools to assess individual risk levels for thyroid disorders. This gap in medical research and care hinders the ability to provide timely interventions and preventative measures, resulting in individuals often seeking medical attention only after experiencing symptoms or complications. Consequently, there is a pressing need for the development of a machine learning-based predictive tool that can assess an individual's risk for thyroid disorders, thereby enabling early intervention and personalized recommendations for healthcare.


# Models
## Random Forest

The data suggests that random forest is the top performing model to use for thyroid disorder detection. It received scores of 0.92 for both accuracy and recall. It even outperformed the ensemble model it is included in. It might be fair to assume that the other two models lower the predictive capacity of the model. The lift chart hovers above the random chance line for the entire  duration - which is a great sign.

## Logistic Regression

For logistic regression cross-validation, the overall result had a low accuracy score at 68%. Precision was high at predicting healthy target instances at 94%. However, precision on predicting hyperthyroidism, hyperthyroidism, and others were all less than 48% in spite of balancing the target classes. Looking at the metrics report, the first 10% delivers 1.2x lift and a steep decline thereafter. Gains are relatively close to the baseline up to 30% of the population and a loss in response after 4 deciles. All these suggest that logistic regression cross-validation is a poor performing model to use for diagnosis of thyroid conditions based on presence of analytes.

## Neural Network

Targeting the 4 target classes, a sequential Neural Network model was created with a total of 6 layers. Of the 6 layers, 5 of them are hidden layers. Each hidden layer is comprised of different number of neurons: layer 1 = 64, layer 2 = 32, layer 3 = 16, layer 4 = 8, and layer 5 = 4. Using encoded predictor variables, the model is given 'early stopping' criteria to ensure that the optimal number of epochs (i.e., iterations) is used.

The resulting classification report indicates that the Neural Network model performed very well with a 70% accuracy rate. Additionally, precision, recall, and F1 scores across the 4 classess are signifcant as well.

A lift curve and a cummulative gain curve also confirm significant performance for the model. The lift curve begins at a high value of ~1.6 and illustrates a step decline thereafter for the next 5 deciles. In turn, this confirms that, compared to a random model, the sequential Neural Network model performs optimally. Though, its performance begins to deminish after the 5 decile. The cummulative gain curve confirms a similar output, illustrating a curve that begins at the bottom-left value of 0 (zero) and quickly rises to 100 within the next 2 deciles-- it is at decile number 3 that the model performs optimally.

## Ensemble

The ensemble method scored a .86 which was the second highest performing model. The advantage of this model over the random forest is it has greater protection from over fitting which random Forests are prone to do. This ensemble method essentially trains a new model on the predictions of the other models against the actual results. This new model learns how to take the advice from the three models and make the best prediction possible. This ensemble is a model trained on the predictions of a few individual models trained on the actual data.

# To summarize. 
We used both exploratory data analysis and a host of tools within the data preprocessing toolkit to create a final data frame that would deliver the best performing models. We dropped highly correlated columns, meaningless columns, and redundant information. We transformed data to mitigate the problems of different scales across features. We transformed the datatypes of the boolean features without losing information.

Using this final data frame, the three models were made. Cross validation was used to determine and set the optimal hyperparameters. These models were combined into a fourth ensemble model and then their performances were compared.
The top performing model was the random forest model. It is important to understand the underlying data and ensure to compare the performances of many different types of models. The model-to-data type relationship is so important. In this case the random forest model drastically outperformed the others.
One of the next steps will be to train a model that can be completely trained using information a person will have themselves at home. This could involve using the query information we dropped to see if there is predictive capacity there, or it could mean finding other data features that won't require testing like the hormone level data we used.
