# Determination of the cost of cars

**Task description:**

A used car sales service "Not beaten, not crashed" is developing an app to attract new customers. It will be possible to find out the market value of your car in it. Build a model that can determine it. You have data on technical specifications, equipment, and prices of other cars. The criteria that the customer values are:
- quality of prediction;
- training time of the model;
- prediction time of the model.

**Data set description:**

Independent features:

- DateCrawled - date the profile was downloaded from the database;
- VehicleType - type of vehicle body;
- RegistrationYear - year of vehicle registration;
- Gearbox - type of transmission;
- Power - power (horsepower);
- Model - car model;
- Kilometer - mileage (km);
- RegistrationMonth - month of vehicle registration;
- FuelType - type of fuel;
- Brand - car brand;
- Repaired - was the car in repair or not;
- DateCreated - date the profile was created;
- NumberOfPictures - number of photos of the vehicle;
- PostalCode - postal code of the profile owner (user);
- LastSeen - date of last user activity.

Target feature:

- Price - price (euros)

**The goal of the work** is to develop machine learning models capable of predicting the cost of a car, and to select the best models based on the criteria that the customer values.

Notes:
- The RMSE metric will be used to evaluate the quality of the models;
- The value of the RMSE metric should be less than 2500.

The work will be carried out in the following 7 stages:
1. Exploratory analysis and primary data processing;
2. Formation and analysis of the dataset;
3. Formation of samples and their preprocessing;
4. Model training;
5. Analysis of the quality and performance of the models;
6. Testing the best model & features importance determing
7. Conclusions.


# Conclusions

To achieve the goal of **developing machine learning models capable of predicting the cost of a car and selecting the best one based on quality metrics and training speed**, the following work was done:

1. A research analysis of the data and their preprocessing was carried out and the following conclusions were made:
    - There are outliers in the data and their distributions are non-normal;
    - There are a lot of anomalies in the data, namely:
        - The presence of advertisements for the sale of cars at extremely low prices, including for free (zero price values);
        - The registration year of the car has a strong spread: from 1000 to 6000;
        - Engine power also has errors in the data: some cars have a power of 0 or 20000 horsepower;
        - The mileage has a categorical, not quantitative, form in the data;
        - The number of photos is represented by a single value (0);
        - The registration year of the cars contains yet to be reached years;
    - Features that should be included in the dataset have been identified, and the impact of the features on the target parameter has been estimated.

2. With the outputs from the data research analysis, data preprocessing was conducted, specifically:
    - Low values of the target parameter were removed from the data;
    - Anomalous values of the registration year were replaced with the average registration year;
    - Anomalous engine capacity values were replaced with missing values and later transformed into a categorical feature;
    - Makes and models were grouped into price categories;
    - Rare categories of the fuel type parameter were grouped into one group;
    - Postal codes were also aggregated into more general groups.

3. A dataset was created, as well as training and validation samples:
    - All duplicates were removed from the dataset;
    - The training and validation samples were formed in a ratio of 75% to 25% respectively;
    - Quantitative features were normalized using the MinMax method;
    - Categorical features were split into binary features using OHE.

4. The following ML models were developed and analyzed:
    1. Linear Regression;
    2. Random Forest;
    3. MLP;
    4. XGBoost;
    5. LightGBM;
    6. CatBoost.

5. The most suitable model for the purpose of the work was determined to be the LightGBM model with the following characteristics:
    - RMSE - 1802.83 euros;
    - Training speed - 11 seconds.

6. The following parameters were identified as the most important ones in determining the cost of a car:
    1. The year of registration of the car;
    2. Engine power;
    3. The brand of the car;
    4. The car's mileage;
    5. The type of transmission.


7. The selected model reaches the following results in terms of RMSE metric, at 1814.66 euros, during testing.


For future work, it is necessary to determine the nature of the anomalies and correct errors in the data, after which it is necessary to adjust the hyperparameters of the proposed model to improve its quality.

Thus, it can be said that the goal of this work has been achieved.
