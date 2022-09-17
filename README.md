# Churn Prediction Using Spark

# Table of Contents
1. [Motivation](#motivation)
2. [Installation](#installation)
3. [Data](#data)
4. [Usage](#usage)
5. [Results](#results)
6. [Licensing, Authors, Acknowledgements](#licensing)

## 1. Motivation <a name="motivation"></a>
This project is a tutorial on how to train a churn prediction model using Spark. It contains a prototyping step within the notebook file.
Also, it shows how you can ship your research code into a Spark processing file that can be shipped into production.

The training is done entirely with Spark, starting from the cleaning until the training and evaluation steps.

![Listened Songs Distribution](/images/listened_songs_distribution.jpg)

## 2. Installation <a name="installation"></a>
### Install Dependencies
The dependencies are versioned by `poetry`. Make sure to have it installed on your system.
Also, the code was tested with:
* Ubuntu 20.04
* Python 3.8

<br/>From the root directory run:
```shell
poetry install
```

## 3. Data <a name="data"></a>
To train the models, we used a dataset provided by Udacity with user activity from a fictional streaming
music company called Sparky. It consists of user events within the platform such as: `Login`, `NextSong`, `Error`, etc.

We considered `churn` users the ones that left the platform by generating an event with the `page=Cancellation Confirmation`.

<br/> You can download the mini Sparkify dataset from [here](https://drive.google.com/drive/folders/14jI_mEW4pVFEESWYM0k8FkKIUHPUUzwh?usp=sharing).

<br/> The file should be placed under the root directory.

![Churn Distribution](/images/user_churn_distribution.jpg)


## 4. Usage <a name="usage"></a>
### Files Structure
The prototyping was done within the `Sparkify.ipynb` Notebook.
The same code was shipped in the `process.py` Python file, which can be run and automated with `Spark.

Both files contain the following steps:
- Data cleaning
- Feature engineering
- Model training & testing

The EDA component is only within the `Sparkify.ipynb` Notebook.
You can look at the `EDA` within an exported PDF at `Sparkify.pdf`.

### Run
#### Run Notebook
Run notebook with:
```shell
jupyter notebook .
```

#### Run Spark Script
Run Spark python script with:
```shell
export PYSPARK_PYTHON=`which python`
spark-submit --master localhost process.py
```

## 5. Results <a name="results"></a>
The results show the `F1 score` on the validation and test.
The validation split was computed within a `cross-validation` with a `3 folds` step.
The test split represents `20%` of the initial data.

|        Model        | Validation |   Test   |
|:-------------------:|:----------:|:--------:|
| Logistic Regression |   0.6723   |  0.6294  |
|     Naive Bayes     |   0.6723   |  0.6294  |
|  Gradient Boosting  |  *0.7001*  | *0.6492* |

The GBT model performed slightly better than the Logistic Regression and the Naive Bayes. 
Probably, because it is a more complex model that can understand non-linear relationships better.

![Listened Songs Distribution](/images/visited_pages_distribution.jpg)

## 6. Licensing, Authors, Acknowledgements <a name="licensing"></a>
The code is licensed under the MIT license. I encourage anybody to use and share the code as long as you give credit to the original author. 
I want to thank Udacity for its contribution to making the data available. Without their assistance, I would not have been able to train the models.

If anybody has machine learning questions, suggestions, or wants to collaborate with me, feel free to contact me 
at `p.b.iusztin@gmail.com` or to connect with me on [LinkedIn](https://www.linkedin.com/in/paul-iusztin-7a047814a/).