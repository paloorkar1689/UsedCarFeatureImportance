#  What drives the price of a car?

## Overview
This used car dataset has been retrieved from Kaggle. The original dataset had over 3 million entries. 
For the sake of processing, only 426k entries were selected. 
The goal is determining what factors make a car more or less expensive. 

This is a Kaggle dataset which can be found in the data folder.

I am following the CISP-DM Framework for this analysis. 

<p align="center">
  <img src=“images/“crisp.png>
</p>

### 1 - Business Understanding
    **1.1 - Data problem definition** <br>
    >   The goal of this problem is to develop a predictive model that will correctly predict the prices of used cars based on various features
        such as Odometer readings, Size, make/model and so on. We would need to employ various Regression models to identify patterns, 
        important features that contribute to the price determination based on historical data and accurately predict any future car sale prices.
        In summary, the objective is to create a robust predictive model that accurately predicts the prices of used cars
        and identified the most significant factors contributing to their valuation.

### 2 - Data Understanding
    **  2.1 Data Collection** <br>
        -   Vehicle.csv dataset is present in data folder.
        -   Data will be loaded with pd.read_csv() method of Pandas

    **  2.2 Data Description** <br>
        The cursory overview of the data
	    -	Total 426880 Samples and 18 Features
	    -	Categorical data - region, model, manufacturer, condition, 
           cylinders, fuel, title_status, transmission, VIN, drive, size
           type, paint_color, state
	    -	Numerical data - id, price, year, odometer
        -   Identify missing data, 
                -   size has 300k missing entries 
                -   condition and cylinders have 175k missing entries
                -   Drive and paint_color has 130k missing entries.

    **  2.3 Data Exploration** <br>
        ⁃	Check the describe function to identify the mean and standard deviation
        ⁃	Identify unique values for Categorical
        -   Identify missing data, 
                -   size has 300k missing entries 
                -   condition and cylinders have 175k missing entries
                -   Drive and paint_color has 130k missing entries.
        -   Plot histogram of price distribution. 
                -   ~5000 cars are priced at 0 value, this needs further examination.

### 3 - Data Preparation
    **  3.1 Data Cleaning** <br>
        -   Drop Columns that would not provide any information or have a high correlation with other fields.
            -   State and Region are highly correlated, dropping Region
            -   Type and Size are highly correlated, dropping Size
            -   Model and Manufacturer are highly correlated, dropping Model
            -   Drop VIN and ID as they do not provide any meaningful information
        -   Drop Any duplicates/nans from the dataset.
    **  3.2 Data inputation** <br>
        -   Fill categorical data ('year', 'fuel', 'title_status', 'transmission', 'type', 'drive') with mode
        -   Fill numeric missing data (odometer) with mean
    **  3.3 Remove outliers** <br>
        -   Plotting histogram of price we understood that price has outliers.
            -   Remove outliers identifying the Q1 and Q3 quantile, deciding the upper and lower bounds
                and drop any data that does not conform to this bound.
            -   Remove any entries which has price listed as < 1000
    **  3.3 Data Encoding** <br>
        -   Ordinal encoding for features condition/Size/title_status
        -   Label encoding for features fuel, cylinder, transmission, paint_color, manufacturer, state
        -   Create new DataFrame by dropping object columns and only keeping numeric columns

    **  3.3 Data Visualization** <br>

### 4 - Modeling
    **  4.1 Data split 
        -   train(70%) and test(30) with train_test_split with random_state=42
        -   X_train, X_test, y_train, y_test 
    **  4.2 Random Forest Regression ** <br>
        -   Create a pipeline with standard scalar and Random Forest Regressor
        -   Define a params_grid with different n_estimators and min_samples_split
        -   Run GridSearchCv with the pipeline and params_grid with scoring as neg_mean_absolute_error
        -   Fit the model on the training dataset
        -   Find out the best model - n_estimators=300
        -   Extract and plot the feature importance data 
    **  4.3 Ridge Regression* <br>
        -   Create a pipeline with standard scalar and Ridge
        -   Define a params_grid with different alpha values
        -   Run GridSearchCv with the pipeline and params_grid with scoring as neg_mean_absolute_error
        -   Fit the model on the training dataset
        -   Find out the best model - alpha=10.0
        -   Extract and plot the feature importance data 

### 5 - Evaluation
    **  5.1 Model performance
        -   Use the best_model from the above steps to predict both test and train data
        -   Calculate MAE and R2_score for both the model fits.
        -   Also identify the mean fit time
        -   Choose a model based on the analysis.

### 6 - Deployment
**  6.1 overview** <br>
    >   As a used car dealer looking to fine-tune your inventory pricing strategy, 
        understanding the factors that positively and negatively impact pricing is crucial for maximizing profitability and optimizing sales. 
        By analyzing the vehicle dataset with over 400k entries here are some insights into these factors and suggest actionable steps.
    >   Top 5 car Manufacturers with the highest number of sales and average sale price ranging between 100k to 150k
    >   The top 5 states with the highest number of sales are  NY, CA, Florida, Ohio, Texas

**  6.2 Positive Factors Impacting Pricing** <br>
    1. **Car Age:** Newer cars generally command higher prices due to their lower mileage and perceived reliability. Consider prioritizing newer models in your inventory and adjusting prices accordingly.
    2. **Brand and Model:** Popular and reputable brands/models tend to have higher resale values. Focus on stocking sought-after brands and models to attract customers willing to pay premium prices.
    3. **Features and Options:** Cars equipped with desirable features such as navigation systems, leather seats, and advanced safety features often fetch higher prices. Consider highlighting these features in your marketing efforts and pricing strategy.
    4. **Condition:** Well-maintained cars with a clean service history and minimal wear and tear typically command higher prices. Invest in reconditioning and detailing services to improve the overall condition of your inventory.

**  6.3 Negative Factors Impacting Pricing** <br>
    1.  **Mileage:** Higher mileage is generally associated with increased wear and decreased value. Consider pricing older vehicles with high mileage more competitively to account for potential maintenance costs and perceived depreciation.
    2.  **Accident History:** Cars with a history of accidents or damage tend to sell for lower prices due to concerns about reliability and safety. Disclose any accident history transparently and price these vehicles accordingly to reflect their condition.
    3.  **Outdated Features:** Cars with outdated technology or styling may struggle to attract buyers and command lower prices. Consider discounting older models or offering incentives to move inventory with less desirable features.
    4.  **Market Demand:** Pay attention to market demand trends and adjust pricing accordingly. Monitor factors such as seasonal fluctuations, regional preferences, and changes in consumer preferences to stay competitive in the market.

**  6.4 Actions to take ** <br>
    1.  **Conduct Market Research:** Analyze market trends and competitor pricing to ensure your inventory is priced competitively.
    2.  **Optimize Inventory Mix:** Focus on stocking popular brands, models, and features that align with customer preferences and market demand.
    3.  **Invest in Reconditioning:** Prioritize reconditioning efforts to improve the condition and appeal of your inventory, thereby justifying higher prices.
    4.  **Transparency and Customer Service:** Build trust with customers by providing transparent information about your inventory's condition, history, and pricing rationale. Offer exceptional customer service to differentiate yourself from competitors.

**  6.5 Summary ** <br>
    >   By leveraging these insights and taking proactive steps to optimize your inventory pricing strategy, you can enhance your competitiveness, 
        attract more customers, and maximize profitability in the used car market.
