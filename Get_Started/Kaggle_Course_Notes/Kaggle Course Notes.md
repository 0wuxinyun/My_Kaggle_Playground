# Notes


- Kaggle Course - Intro to Machine Learning

    ![Draft%20efdfad7c47964c4a89ea608b8fc47eea/Screenshot_2021-02-08_at_11.30.07_PM.png](Draft%20efdfad7c47964c4a89ea608b8fc47eea/Screenshot_2021-02-08_at_11.30.07_PM.png)

    - Pandas : Data

        [Tutorials - pandas 0.15.2 documentation](https://pandas.pydata.org/pandas-docs/version/0.15/tutorials.html)

        [Pandas: 强大的 Python 数据分析支持库 | Pandas 中文](https://www.pypandas.cn/docs/)

    - Sklearn : Model
    - automated machine learning (AutoML) tools → Google

- Kaggle Course - Intermediate Machine Learning

    [Learn Intermediate Machine Learning Tutorials](https://www.kaggle.com/learn/intermediate-machine-learning)

    - Missing Values
        - A Simple Option: Drop Columns with Missing Values : **BAD**

            ![Draft%20efdfad7c47964c4a89ea608b8fc47eea/Screenshot_2021-02-09_at_12.37.29_AM.png](Draft%20efdfad7c47964c4a89ea608b8fc47eea/Screenshot_2021-02-09_at_12.37.29_AM.png)

        - Imputation

            **Imputation** **fills** in the missing values with some number. For instance, we can fill in the mean value along each column.

        - An Extension To Imputation

            ![Draft%20efdfad7c47964c4a89ea608b8fc47eea/Screenshot_2021-02-09_at_12.07.46_AM.png](Draft%20efdfad7c47964c4a89ea608b8fc47eea/Screenshot_2021-02-09_at_12.07.46_AM.png)

    - Categorical Variables
        - Drop Categorical Variables
        - Label Encoding

            Label encoding assigns each unique value to a different integer.

            This approach assumes an **ordering** of the categories → ordinal variables.

        - One-Hot Encoding

            nominal variables.

            PS : One-hot encoding generally does **not** perform well if the categorical variable takes on a **large number of values** (i.e., you generally won't use it for variables taking more than 15 different values).

            Might not appear in the training dataset Categorical Variables

    - Pipelines
        - What is pipelines

            Pipelines are a simple way to keep your data preprocessing and modeling code **organized**. Specifically, a pipeline **bundles** preprocessing and modeling steps so you can use the whole bundle as if it were a single step.

        - Construction
            - Step 1: Define Preprocessing Steps
            - Step 2: Define the Model
            - Step 3: Create and Evaluate the Pipeline
    - Cross-Validation
        - What is cross-validation?

            In cross-validation, we run our modeling process on different subsets of the data to get multiple measures of model quality.

            ![Draft%20efdfad7c47964c4a89ea608b8fc47eea/Screenshot_2021-02-09_at_8.04.17_PM.png](Draft%20efdfad7c47964c4a89ea608b8fc47eea/Screenshot_2021-02-09_at_8.04.17_PM.png)

        - Go Or Not ?
            - *For **small** datasets*, where extra computational burden isn't a big deal, you should run cross-validation.
            - *For **larger** datasets*, a single validation set is sufficient. Your code will run faster, and you may have enough data that there's little need to re-use some of it for holdout.
    - XGBoost

        XGBoost stands for ***extreme gradient boosting***,

        - **Ensemble method**s combine the predictions of several models : Decision trees → Random forest
            - Gradient boosting :

                Gradient boosting is a method that goes through cycles to iteratively add models into an ensemble.

        - **Gradient boosting**
            - It begins by initializing the ensemble with a **single** model, whose predictions can be pretty **naive**.
            - Then, we use the **loss function** to fit a new model that will be added to the ensemble. Specifically, we determine model parameters so that ***adding this new model to the ensemble will reduce the loss.*** (Side note: The "gradient" in "gradient boosting" refers to the fact that we'll use **gradient descent** on the loss function to determine the parameters in this new model.)

            ![Draft%20efdfad7c47964c4a89ea608b8fc47eea/Screenshot_2021-02-09_at_8.36.15_PM.png](Draft%20efdfad7c47964c4a89ea608b8fc47eea/Screenshot_2021-02-09_at_8.36.15_PM.png)

            - Improvements :
                - Number of estimator ?

                    ![Draft%20efdfad7c47964c4a89ea608b8fc47eea/Screenshot_2021-02-10_at_7.28.48_PM.png](Draft%20efdfad7c47964c4a89ea608b8fc47eea/Screenshot_2021-02-10_at_7.28.48_PM.png)

                    Problem : Trade off of under fitting and overfitting 

                    Solution : Early stopping causes the model to stop iterating when the validation score stops improving in n round[n=5 is a good starting point].

                - Learning rate
    - Data Leakage
        - What is Data Leakage

            Data leakage (or leakage) happens when your training data **contains information about the target**, but similar data will not be available when the model is used for prediction. This leads to high performance on the training set (and possibly even the validation data), but the model will perform poorly in production.

        - Target leakage : will be available at the time we want to make a prediction?

            Target leakage occurs when your predictors include data that will not be available at the time you make predictions. It is important to think about target leakage in terms of the **timing or chronological order** that data becomes available, not merely whether a feature helps make good predictions.

            To prevent this type of data leakage, any variable updated (or created) after the target value is realized should be excluded.

        - Train-Test Contamination

            Recall that validation is meant to be a measure of how the model does on data that it hasn't considered before. You can corrupt this process in subtle ways if the validation data affects the preprocessing behavior. This is sometimes called train-test contamination.

- Kaggle Course -Pandas
    - Dataset types

        There are two core objects in pandas: the **DataFrame** and the **Series**

        - DataFrame

            A DataFrame is a table. It contains an array of individual entries, each of which has a certain value. Each entry corresponds to a row (or record) **and** a column.

            - Construct : `pd.DataFrame()` ← Dictionary["col_name"]:[1,2,3...]
            - Index :

                The list of **row labels** used in a DataFrame is known as an Index. We can assign values to it by using an `index parameter` in our constructor:

        - Series

            A Series is, in essence, a single column of a DataFrame. ← **LIST**

    - Data types

        `dtype` property to grab the type of a specific **column**.

        `dtypes` property returns the dtype of every column in the **DataFrame**

        - Data types :
            1. float64
            2. int64
            3. object

            Convertion : `.astype()`

        - Missing data :
            - Find :

                `pd.isnull(series)` `pd.notnull(series)` : Extract NaN

            - Filling :

                `series.fillna("opti")` provides  value to missing data.

                Backfill strategy : fill each missing value with the first non-null value that appears sometime after the given record in the database.

    - DataFrame Objects Popular Methods
        - `head(n)`
        - `shape`
        - `to_csv("path")`
        - `.describe()`
    - Common manipulation
        - Selecting  :
            - `df.col`
            - `df["col"]`

            → Conditional selection

            → Assigning data 

        - Indexing  :

            Row-first, column-second

            - **Index**-based selection: `df.iloc[i,j]`
            - **Label**-based selection: `df.loc[i,j]` ← Index name j=[index/colmns 1, 2 ,3 ]

                Logical value : **TRUE FALSE**

        - Manipulating the index :
            - Use specific columns as an index :  `df.set_index("col")`
        - Conditional selection :
            - `&` : AND `|` : OR
            - `.isin([..])`
            - `.isnull` and its companion `.notnull()`
        - Sorting :

            To sort by column values : `sort_values(by="",ascending=True)`

            To sort by index values : `sort_index()`

        - Replacing : a non-null value that we would like to replace : `replace(a,b)`
        - Renaming
            - `rename(index = {a:b})`, which lets you change index names and/or column names.
            - `set_index()`
        - Combining
            - `concat([d1,d2],index=0/1)`. Given a list of elements, this function will smush those elements together **along an axis.**
            - `join()` lets you combine different DataFrame objects which have an **index** in common.
    - Statistical Summary
        - `.describe()`
        - `.mean()`
        - `.unique()`
        - `**.value_counts()**`
        - `.max()` `idxmax()`
        - `.count()`
    - Mapping

        In data science we often have a need for **creating new representations from existing data**, or for transforming data from the format it is in now to the format that we want it to be in later.

        - `map()`

            ```python
            review_points_mean = reviews.points.mean()
            reviews.points.map(lambda p: p - review_points_mean)
            ```

        - `apply()`

            ```python
            def remean_points(row/col):
                row.points = row.points - review_points_mean
                return row

            reviews.apply(remean_points, axis='columns/index')
            ```

    - Group-wise analysis

        `groupby()` created a group of reviews which allotted the same point values to the data 

        Use with the **statistical function** to perform aggregated function

        Further manipulate via the **apply** method 

        `agg()` which lets you run **a bunch of different function**s on DataFrame simultaneously.

        `size()` Compute group sizes. → Count 

        ```python
        reviews.groupby('points').price.min()
        reviews.groupby('winery').apply(lambda df: df.title.iloc[0])
        reviews.groupby(['country']).price.agg([len, min, max])
        ```

        - Gotcha :
            - Multi-indexes

                 `reset_index()` methodconverting back to a regular index
