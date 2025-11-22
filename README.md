# Investment-Guide-Towards-40k-in-2-Years-with-Data-Analysis-and-Forecasting.ipynb

Layse is a successful nutritionist, dedicated to helping her patients achieve a healthier life. However, beyond her passion for nutrition, Layse has a big personal dream: to take her family on an unforgettable trip through Europe in just two years. To turn this dream into reality, she has set a clear financial goal: accumulate R\$ 40,000.

**Imagine Layse hires you, the data scientist, to help her on this mission.**

With a busy routine, Layse is looking for a smart and data-driven way to optimize her savings and investments. This is where this data science project comes in.

The main objective of this project is to assist Layse in her financial journey, providing actionable insights to help her reach her goal of R\$ 40,000 in 2 years. Through the analysis of historical financial market data, we will use Machine Learning models to project potential returns and risks of various assets. Based on these projections, we will calculate the required monthly investment for Layse to achieve her goal, considering her initial capital (or lack thereof).

In addition to historical analysis and projections, the project will explore integration with real-time data processing tools like Spark and Kafka. This will enable the construction of a more dynamic data pipeline, capable of providing updated insights into the financial market, potentially improving investment recommendations over time.

Join us on this data journey to help Layse turn her European dream into a reality!

. High-Level Functional Requirements (Use Cases)This section defines the high-level functional requirements that the system must fulfill to solve the proposed problem: determining which asset (ticker) the client, Layse, should invest in to accumulate R$ 40,000.00 in 2 years, prioritizing the lowest possible monthly contribution.1.1. Actors InvolvedFinancial Analyst/Investor: Represents the technical user of the system (in this context, the developer or a person with financial/programming knowledge). This actor is responsible for configuring goals, executing the analysis pipeline, and interpreting the results.Client (Layse): Represents the final beneficiary of the analysis. She does not interact directly with the system at this stage but is the recipient of the asset recommendation.1.2. Main Use CasesDefine Goals and Constraints: Allows the Financial Analyst/Investor to input the client's objectives (Target: R$ 40,000; Term: 2 years) and the optimization constraint (minimize monthly contribution).Execute Time Series Analysis Pipeline: This is an aggregate Use Case that encapsulates the technical analysis process. It includes (i.e., mandates the execution of) the following sub-Use Cases:Collect Historical Data (yfinance): The system must be able to fetch historical data for financial assets.Validate Stationarity and Differentiate: The system must verify the stationarity of time series and apply differentiation when necessary.Train Model and Analyze Residuals: The system must train predictive models and perform residual analysis to validate model quality.Identify Best Asset (Ticker): Upon completion of the pipeline, the system must determine which asset best meets the defined criteria, aiming for the lowest monthly contribution.1.3. Relationships Between Use Cases<<include>>: Indicates that one Use Case implicitly invokes another. For example, to "Execute Time Series Analysis Pipeline," it is mandatory to "Collect Historical Data."2. Activity Diagram: Technical Process FlowThe Activity Diagram details the step-by-step workflow, including decisions and iterations, that the system will follow to perform predictive analysis and identify the ideal asset.2.1. Workflow DescriptionThe process follows a logical sequence aimed at processing data and calculating the financial projection:Start: The Analyst initiates the system.Input Parameters: The system receives the target amount (R$ 40k) and the time horizon (24 months).Select Candidate Tickers: A list of potential assets (e.g., PETR4, VALE3, IVVB11) is selected for analysis.Data Processing Loop (For each Ticker):Fetch Data: The system requests historical prices via the yfinance API.Test Stationarity: An Augmented Dickey-Fuller (ADF) test is performed.Decision: Is the data stationary?No: Apply differentiation (Difference $n+1$). Re-test.Yes: Proceed to modeling.Train Model: Fit the Time Series model (e.g., ARIMA).Analyze Residuals: Check if residuals behave like white noise (randomness check).Decision: Is the model valid?No: Adjust model parameters (Auto-ARIMA/Grid Search) and retrain.Yes: Proceed to forecast.Forecast Price: Predict the asset price for $T + 24$ months.Calculate Required Monthly Contribution: Based on the expected return (forecast) and the target amount (R$ 40k), calculate how much Layse needs to deposit monthly.Compare Results: The system ranks the processed tickers based on the calculated monthly contribution.Select Optimal Asset: The asset requiring the lowest monthly contribution is identified as the best choice.Output Recommendation: The system presents the Ticker and the suggested monthly value.End.2.2. Mermaid Diagram Representation (Code-view)To assist in visualizing the structure described above, here is the standard logic flow:Snippet de códigograph TD
    A([Start]) --> B[Define Goal: R$ 40k / 24 Months]
    B --> C[Select List of Tickers]
    C --> D{Loop: For Each Ticker}
    
    D --> E[Fetch Data via yfinance]
    E --> F{Is Stationary? ADF Test}
    F -- No --> G[Apply Differentiation]
    G --> F
    F -- Yes --> H[Train Predictive Model]
    
    H --> I[Analyze Residuals]
    I -- Poor Fit --> H
    I -- Good Fit --> J[Forecast Price T+24 Months]
    
    J --> K[Calculate Monthly Contribution]
    K --> L[Store Result]
    L --> D
    
    D -- All Processed --> M[Compare Monthly Contributions]
    M --> N[Identify Minimum Contribution Asset]
    N --> O([Output Recommendation for Layse])

    <img width="1024" height="1024" alt="image" src="https://github.com/user-attachments/assets/7fc60d1f-2c81-42a5-9b99-56d092012de6" />
