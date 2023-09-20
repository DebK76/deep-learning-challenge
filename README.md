# deep-learning-challenge
1. Overview:
The purpose of the analysis is to create a tool for the nonprofit foundation Alphabet Soup that can help it select the applicants for funding with the best chance of success in their ventures.
The data source is an .csv file compiled by Alphabet Soup’s business team containing information on more than 34,000 organizations that have received funding from Alphabet Soup over the years.
The processes are machine learning and neural networks, which are employed to construct a binary classifier that can predict whether applicants will be successful if funded by Alphabet Soup.
The tools of the project are TensorFlow, a free open-source library with a particular focus on training and inference of deep neural networks, and Keras, another open-source library that provides a Python interface for TensorFlow. Coding was conducted in Python.
Success is defined as creating a tool with a predictive power of 73% or more: i.e., its predictions are correct 73% of the time or more.

Background
The nonprofit foundation Alphabet Soup wants a tool that can help it select the applicants for funding with the best chance of success in their ventures. With your knowledge of machine learning and neural networks, you’ll use the features in the provided dataset to create a binary classifier that can predict whether applicants will be successful if funded by Alphabet Soup.

From Alphabet Soup’s business team, you have received a CSV containing more than 34,000 organizations that have received funding from Alphabet Soup over the years. Within this dataset are a number of columns that capture metadata about each organization, such as:

EIN and NAME—Identification columns
APPLICATION_TYPE—Alphabet Soup application type
AFFILIATION—Affiliated sector of industry
CLASSIFICATION—Government organization classification
USE_CASE—Use case for funding
ORGANIZATION—Organization type
STATUS—Active status
INCOME_AMT—Income classification
SPECIAL_CONSIDERATIONS—Special considerations for application
ASK_AMT—Funding amount requested
IS_SUCCESSFUL—Was the money used effectively

Data Preprocessing
What variable(s) are the target(s) for your model?
The target (i.e., dependent) variable is IS_SUCCESSFUL, which contains the binary values 0 or 1. As such, this task is one of classification.

What variable(s) are the feature(s) for your model?
The features (i.e., independent variables) are all the remaining variables excluding EID (i.e., Employee Identification Number), discussed immediately below.

What variable(s) should be removed from the input data because they are neither targets nor features?
Variables that were removed include EID and NAME, because these strings appear incidental to the performance and financial underpinnings of IS_SUCCESSFUL. As I will demonstrate below, this is not the case. EID is indeed expendable, but NAME is not.

Compiling, Training, and Evaluating the Model

How many neurons, layers, and activation functions did you select for your neural network model, and why?

I was able to confine the model to two hidden layers and an output layer (Figure 2). The hidden layers both used the Rectified Linear Unit (ReLU) activation function. Despite seeming simple, binary classification problems often involve complex, non-linear decision boundaries, perhaps like the subjective-sounding categories USE_CASE and SPECIAL_CONSIDERATIONS. ReLU introduces non-linearity to the model, enabling it to learn these non-linear relationships in the data. By contrast, my output layer used a sigmoid activation function, since its results are confined to values of 0 and 1, like the IS_SUCCESSFUL target variable. Finally, settling on the number of neurons was a trial-and-error process. I found that 80 neurons for the first hidden layer and 30 for the second worked well. The idea is that the earlier layers learn lower-level, more general features, while the later layers learn higher-level, more specific features. I therefore concentrated computational power with more neurons in the first layer, and then reduced the number in the second to capture the smaller number of high-level abstractions.

SUMMARY REPORT

The pursuit of improved accuracy in our model required several rounds of trial and error. We made four distinct attempts, each involving different strategies. These strategies included feature selection by dropping additional variables, reorganizing feature categories, altering the model architecture by adding hidden layers, and, intriguingly, reintroducing a previously excluded variable, namely, 'NAME.'

The results we obtained were quite surprising. Notably, the inclusion of the 'NAME' variable had a substantial impact on our model's accuracy. This outcome challenged our initial assumption that only variables related to historical performance, industry positioning, and financial metrics would significantly influence the 'IS_SUCCESSFUL' target variable. The unexpected importance of the 'NAME' variable raises intriguing questions. Could more efficient and fiscally responsible organizations tend to use specific keywords in their names? Is there an underlying bias in the model that favors certain name strings over others? Investigating these questions would necessitate the use of different unsupervised machine learning techniques, which fall outside the scope of this project.

In summary, an alternative approach to this classification task could involve exploring different models, such as Random Forest Classifier or Support Vector Machine (SVM). These models have demonstrated effectiveness in binary classification problems and might yield higher accuracy without the need for extensive optimization. Furthermore, they can adeptly handle both numerical and categorical variables, making them well-suited for datasets that may contain outliers or imbalanced distributions. As such, considering these alternative models could provide a promising solution to our classification challenge.
