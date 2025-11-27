# Investment-Guide-Towards-40k-in-2-Years-with-Data-Analysis-and-Forecasting.ipynb

Layse is a successful nutritionist, dedicated to helping her patients achieve a healthier life. However, beyond her passion for nutrition, Layse has a big personal dream: to take her family on an unforgettable trip through Europe in five years. To turn this dream into reality, she has set a clear financial goal: accumulate R\$ 40,000.

**Imagine Layse hires you, the data scientist, to help her on this mission.**

With a busy routine, Layse is looking for a smart and data-driven way to optimize her savings and investments. This is where this data science project comes in.

The main objective of this project is to assist Layse in her financial journey, providing actionable insights to help her reach her goal of R\$ 40,000 in 5 years. Through the analysis of historical financial market data, we will use Machine Learning models to project potential returns and risks of various assets. Based on these projections, we will calculate the required monthly investment for Layse to achieve her goal, considering her initial capital (or lack thereof).


Join us on this data journey to help Layse turn her European dream into a reality!

Sure! Here’s a well-organized and structured format for the requirement analysis you provided:

Requirements Analysis
1. High-Level Functional Requirements (Use Cases)
This section defines the high-level functional requirements that the system must fulfill to determine which asset (ticker) the client, Layse, should invest in to accumulate R$ 40,000.00 in 5 years, prioritizing the lowest possible monthly contribution.
1.1. Actors Involved


Financial Analyst/Investor

Represents the technical user of the system (developer or financial expert).
Responsible for configuring goals, executing the analysis pipeline, and interpreting the results.



Client (Layse)

Represents the final beneficiary.
Does not interact directly with the system at this stage but is the recipient of the asset recommendation.



1.2. Main Use Cases


Define Goals and Constraints

Allows the Financial Analyst to input the client’s objectives (Target: R$ 40,000; Term: 5 years) and the optimization constraint (minimize monthly contribution).



Execute Time Series Analysis Pipeline

This is an aggregate Use Case that encapsulates the technical analysis process. It includes the following sub-Use Cases:
Collect Historical Data (yfinance): Fetch historical data for financial assets.
Validate Stationarity and Differentiate: Verify time series stationarity and apply differentiation if needed.
Train Model and Analyze Residuals: Train predictive models and perform residual analysis to validate quality.
Identify Best Asset (Ticker): Upon pipeline completion, determines which asset best meets the criteria, aiming for the lowest monthly contribution.



1.3. Relationships Between Use Cases

<>: Indicates that one Use Case implicitly invokes another (e.g., “Execute Pipeline” requires “Collect Historical Data”).


2. Activity Diagram: Technical Process Flow
The Activity Diagram details the step-by-step workflow, including decisions and iterations, that the system follows to perform predictive analysis.
2.1. Workflow Description


Start:

The Analyst initiates the system.



Input Parameters:

The system receives the target amount (R$ 40k) and the time horizon (24 months).



Select Candidate Tickers:

A list of potential assets (e.g., PETR4, VALE3, IVVB11) is selected for analysis.



Data Processing Loop (For each Ticker):

Fetch Data: Request historical prices via the yfinance API.
Test Stationarity (ADF Test):

Decision: Is the data stationary?

No: Apply differentiation ($n+1$). Re-test.
Yes: Proceed to modeling.




Train Model: Fit the Time Series model (e.g., ARIMA).
Analyze Residuals: Check for white noise (randomness).

Decision: Is the model valid?

No: Adjust parameters (Grid Search) and retrain.
Yes: Proceed to forecast.




Forecast Price: Predict asset price for $T + 24$ months.
Calculate Monthly Contribution: Calculate the required monthly deposit based on the forecast and the R$ 40k target.



Compare Results:

The system ranks the processed tickers based on the calculated monthly contribution.



Select Optimal Asset:

The asset requiring the lowest monthly contribution is identified.



Output Recommendation:

The system presents the Ticker and the suggested monthly value for Layse.



End.



This format provides clear sections and sub-sections for different aspects of the requirements analysis, making it more readable and organized.


<img width="1024" height="1024" alt="image" src="https://github.com/user-attachments/assets/7fc60d1f-2c81-42a5-9b99-56d092012de6" />
