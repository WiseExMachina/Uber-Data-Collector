# Uber-Data-Collector
Uber Ride Demand Predictor for Mexico City

Uber-Data-Collector
Uber Ride Demand Predictor for Mexico City
Project Title: Uber Ride Demand Prediction for Driver Planning Optimization for Mexico City
Driver Problem / Justification
As an Uber driver, the inefficiency of preparing to drive (getting the car ready, leaving home) only to find low demand for "convenient" rides is a real problem. This leads to wasted time and missed opportunities, as I could be dedicating that time to other productive activities, like studying data science. The ability to forecast ride demand would allow me to make informed decisions about when it's truly profitable to hit the road.

Main Objective
Develop a Machine Learning model that predicts the number of ride requests expected in specific future hours (e.g., 12:00 PM to 1:00 PM and 2:00 PM to 3:00 PM), based on the observed request rates in the immediately preceding hours (specifically, the first 15 minutes of 10:00 AM and 11:00 AM).

Target Variable
Total number of ride requests in future time intervals (e.g., the total requests between 12:00 PM and 1:00 PM, and between 2:00 PM and 3:00 PM).

Data Sources and Potential Features
To build this model, I'll need historical ride request data. As a driver, this involves systematic manual data collection.

Ride Request Data (Driver Collection):

Timestamp of each request: Fundamental for calculating rates.

Request appearance rate: The key variable. This is the time it takes for a new ride request to appear (e.g., 00:31.45), observed in specific 10-minute windows (e.g., 12:00 PM - 12:10 PM, 1:00 PM - 1:10 PM, 2:00 PM - 2:10 PM).

Temporal Variables:

Day of the week: Monday, Tuesday, weekend, etc.

Hour of the day: The specific hour of prediction (e.g., 12 PM, 2 PM).

Public holiday: Is it a local or national holiday?

Special events: Large concerts, sports games, conferences (if they can be incorporated).

Feature Engineering
This is where I'll transform raw data into useful variables for the model:

Request Rate in Preceding Windows (10-minute intervals):

Calculate the number of requests per minute/every 10 seconds for specific 10-minute observation windows (e.g., 12:00 PM - 12:10 PM, 1:00 PM - 1:10 PM, 2:00 PM - 2:10 PM).

I can calculate averages, medians, or even the standard deviation of these rates within these 10-minute windows.

Total Ride Count in Previous Hours:

Total number of requests in the hour preceding the prediction window (e.g., 11:00 AM - 12:00 PM for a 12 PM prediction).

Time Characteristics:

Extract the day of the week (numeric or categorical).

Extract the hour of the day (e.g., 12 for 12 PM, 1 for 1 PM, 2 for 2 PM).

Create a binary flag for "weekend" or "public holiday."

Technical Implementation: Building a Custom Data Pipeline
To facilitate this crucial manual data collection, I've engineered a robust, full-stack data entry solution:

Frontend (User Interface): A custom HTML spreadsheet application, styled with Tailwind CSS, is hosted on GitHub Pages. This provides a user-friendly and mobile-responsive interface for efficiently logging ride details, including stopwatch lap times for precise request rate calculations.

Backend (Data Persistence): This static frontend seamlessly integrates with a Google Apps Script web app. This script acts as a secure intermediary, receiving data submitted from the GitHub Pages frontend and automatically appending it to a designated Google Sheet. This ensures all collected data is immediately saved, organized, and accessible for further analysis, overcoming the limitations of static website hosting.

This setup demonstrates proficiency in web development (HTML, CSS, JavaScript), cloud scripting (Google Apps Script), and version control/hosting (GitHub Pages), creating a complete and effective data acquisition system for my project.

Machine Learning Methodology
This is a regression problem, as I am predicting a number (the quantity of requests).

Data Collection and Storage: Establish a consistent method to record requests over time. The custom HTML/Apps Script solution serves this purpose.

Data Preprocessing:

Handling missing values.

Encoding categorical variables (e.g., One-Hot Encoding for the day of the week).

Normalizing/Standardizing numerical variables.

Data Splitting: Divide data into training and testing sets. It's crucial that the test set contains more recent data than the training set to simulate real-world prediction (temporal validation).

Model Selection and Training:

Candidate Models:

Linear Regression: A good starting point to understand basic relationships.

Tree-based Models (Random Forest Regressor, Gradient Boosting Regressor - XGBoost, LightGBM): Often perform very well with tabular data and can capture complex relationships.

Time Series Models (ARIMA, Prophet): If I have enough historical data and want to explicitly model temporal dependence.

Model Evaluation:

Regression Metrics:

Mean Absolute Error (MAE): The average difference between the prediction and the actual value. Easy to interpret.

Root Mean Squared Error (RMSE): Penalizes larger errors more heavily.

R-squared (R 
2
 ): Indicates how well the model explains the variability of the target variable.

Visualization: Plot the model's predictions against the actual values to visually assess performance.

Implementation and Driver Use
Once the model is trained and evaluated:

Real-time Observation:

At 12:00 PM, I would observe the request rate in my Uber app during the following 10 minutes (until 12:10 PM).

At 1:00 PM, I would observe the request rate during the following 10 minutes (until 1:10 PM).

At 2:00 PM, I would observe the request rate during the following 10 minutes (until 2:10 PM).

Data Input: I would input these observed rates and other variables (day of the week, if it's a holiday) into my model via the custom spreadsheet.

Prediction: The model would give me an estimate of the number of requests expected for the upcoming hours.

Decision Making: Based on these predictions, I could decide whether it's worth preparing and going out to drive, or if it's better to dedicate that time to something else.

Potential Challenges
Data Collection: While the custom tool automates logging, consistent manual observation in real-time is still required.

Unexpected Variability: Unplanned events (accidents, surprise concerts) can affect demand unpredictably.

Sampling Bias: My own driving patterns and location might bias the data I collect.

This project is ambitious and allows me to apply advanced data science concepts to a personal and real-world problem. It's an excellent idea for a year-long project!

Author
Wise Ex Machina, Bernardo Lozano Wise

Share
[Link to your LinkedIn Profile]
[Link to your Portfolio Website, if you have one]
