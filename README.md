
# Table of Content

**Team Introduction** 
* individual background introduction
* collaboration/communication methods, team formation

**Project Description** 
* Executive Summary 
* Problem Statement 
  + Problem Description 
  + Data Description
  + Our Solution 
  + Outcome Description 
  + Solution Assessment and Impact 

**Project Execution** 
* Technical Summary 
* Phase 1: Set up environment 
* Phase 2: Create functions 
* Phase 3: Calculate Bench Portfolio Metrics
* Phase 4: Construct Final Dataset 
* Phase 5: Create Return Matrix 
* Phase 6: Construct Portfolio with Constraints 
* Phase 7: Create Annual Data Table 
* Phase 8: Save Data Sets, subsetted 
* Phase 9: Visualize Performance 
* Appendix 1: Data Dictionary 
* Appendix 2: Key Data Inputs

**Project Summary** 
* Project Output
* Scalable Solution
  + Time: for n~inf options
  + All Equity Market   
* Future Improvement on Technical Project Collaboration
  + Cloud Computer Solutions  

# Team Introduction
(blank)

# Project Description
## Executive Summary 
Managing technical teams poses unique challenges. We considered and addressed them in the initial planning stages of our technical project. In this case study we had difficulties in the planning portion of our project that lead to reduced time in validation of our submission. We have outlined a prefered process to address the potential issues to help provide better management of our present and future projects. The goal is to prevent some common pitfalls of technical teams without extensive project management experience. 

## Problem Statement
### Problem Description 
Portfolio optimization refers to the problem of constructing an optimal portfolio of stocks. The common objective will be to maximize investment return with a given level of risk, or to minimize risk with a given level of return. 

In reality, investors have to consider some other constraints such as limits on the number of unique assets in the portfolio or how many assets outside a specified benchmark can or must be added. 

Our challenge was to develop an equity portfolio optimization framework that improves returns as it compares to a benchmark portfolio with a same or slightly higher risk level. The optimization framework minimized the trade-off between risk, in the form of tracking error, and expected excess return through time, subject to several constraints. This problem represented a basic Markowitz portfolio optimization problem.

### Data Description
We are given...
- Covariance data was supplied in a long format and was given for every four weeks over a ten year period from 01-03-2007 to 12-21-2016. 

- The time series data supplied included the names, SEDOL, Sector, bench weight, etc. for the stocks used in the benchmark portfolio at a given time. 

- See Appendix 2 in the project execution section for more information

### Our Solution
We created three functions to reorganize the given data to create a complete covariance matrix, to calculate portfolio variance with our data, and to create an optimized portfolio using Markowitz principles with added constraints. We calculated the benchmark portfolio performance and created comparison metrics to contrast our solution versus the benchmark. 

### Outcome Description 
The outcome description is a Markowitz portfolio optimized by our algorithm integrated with several constraints as stated in the problem description. The key output is the list of stocks and their optimized weights. 

### Solution Assessment and Impact 
Once we had our algorithms created we ran our program of algorithms to construct our portfolios and fill a table to hold the comparison metrics. As a result, our constrained portfolio outperformed the benchmark by a factor of 9x, after the 10-year time frame our portfolio model cumulative returns were 388% where the benchmarks was 44%. 


# Project Execution
The project execution and phases are a living document that will change as the problem and solution are explored more thoroughly during the practice. 

**Technical Summary 

Our challenge was to develop an equity portfolio optimization framework that improves risk adjusted excess returns as it compares to a benchmark portfolio. The optimization framework minimized the trade-off between risk, in the form of tracking error, and expected excess return through time, subject to several constraints. This problem represented a basic Markowitz portfolio optimization problem. This Markowitz implementation was also used to create the benchmark data that was provided and served as a starting point to further add the constraints. The constraints to be added were: 1) The portfolio only consisted of long positions, all asset weights were non-negative. 2) The portfolio must also be fully invested at all times, weights sum to one. 3) Max allocation in any asset was limited to 5%. 4) Sector allocation was limited to 10%. 5) Limit the target number of distinct assets in the portfolio to 50-70. 6) Active share constraint, which controls how closely we follow the benchmark index in terms of active weights, as well as a tracking error in terms of a risk measure rather than return. Additionally, we were limited to < 3 minutes to compute a new portfolio. This limited our solution to integrate functions and algorithms that would help meet this final constraint. Emphasis was placed on a solution that is scalable to a global equity market.

The solution we created started by creating three functions to reorganize the risk data given back into a complete covariance matrix, to calculate portfolio variance with our data, and to create an optimized portfolio using Markowitz principles with the added constraints. We then calculated the benchmark comparison metrics to ensure we had the algorithms to calculate our constrained portfolio. Once we had our algorithms created we ran our program of algorithms to construct our portfolios and fill a table to hold the comparison metrics. As a result, our constrained portfolio outperformed the benchmark by a factor of 9x, after the 10-year time frame our portfolio model cumulative returns were 388% where the benchmarks was 44%.

**Phase 1: Set up environment**
- Goal 
  + Identify libraries and prioritize functions if needed
  + Load data sets
      + clean data structures
  + Create project tree for shared use
- Data Input
  + Covariance data
  + Time series data
- Diagram
- Code

**Phase 2: Create functions**
- Goal 
  + Create three key functions that later will be used for portfolio construction and portfolio assessment.
  + The three functions are 
      + Create_covm
      + Pf_var
          + Single (using a given PF)
          + All (using individual covariance files and PF weights)
  + Construct_PF
- Data Input
  + Covariance data
  + Time series data
- Diagram
- Code
      

**Phase 3: Calculate Bench Portfolio Metrics**
- Goal 
  + Create metrics for the reconstructed benchmark portfolio, so that we can compare them to our own benchmark metrics.
      + Returns and Relative Returns 
      + Turnover
      + Adjusted Returns 
      + Information Ration (IR)
- Data Input
  + Time series data
- Diagram
- Code

**Phase 4: Construct Final Dataset** 
- Goal 
  + Create a single final dataset from multiple datasets provided for portfolio building and assessment 
- Data Input
- Diagram
- Code

**Phase 5: Create Return Matrix** 
- Goal 
  + Collect all returns from the given data and put it into a matrix format in order use it in our solution function Construct_PF. Two possible ways is to use a simple mean with a recency bias and using a bayesian hierarchical model. The input to the solution needs a vector of expected returns with the same length as number of stocks.
  + Recency Bias using one year actual returns
  + Bayesian Inference model to calculate expected returns for PF construction
- Data Input
  + Four week returns from each portfolio.
- Diagram
- Code

**Phase 6: Construct Portfolio with Constraints** 
- Goal 
  + Create an optimized Markowitz Portfolio while adding in additional constraints, as required by the competition rules, using the Construct_PF function. The constraints were as follows: The portfolio only consisted of long positions, all asset weights were non-negative. The portfolio must also be fully invested at all times/weights sum to one. Max allocation in any asset was limited to 5%. Sector allocation was limited to 10%.  Limit the target number of distinct assets in the portfolio to 50-70.
- Data Input
- Diagram
- Code


**Phase 7: Create Annual Data Table** 
- Goal 
  + Create data table that returns metrics for our portfolio on an annual basis. This includes metrics such as:
      + Annual Benchmark Portfolio Returns (Ann_Bench_Returns)
      + Annual New Portfolio Returns (Ann_New_Returns)
      + Cumulative Benchmark Returns (Bench_Returns_Cum)
      + Cumulative New Portfolio Returns (New_Returns_Cum)
      + Excess Returns (Excess_Returns)
      + Benchmark Sharpe Ratio (Bench_Sharpe_Ratio)
      + New Portfolio Sharpe Ratio (New_Sharpe_Ratio)
      + Annual Tracking Error for new portfolio (Ann_Tracking_Error)
      + Annual Information Ratio for new portfolio (Ann_IR)
- Data Input
- Diagram
- Code


**Phase 8: Save Data and Visualize Performance** 
- Data Input
  + Use annual data table and the recreated benchmark portfolio statistics to create various data visualizations to compare performance over a ten year period.
- Diagram
- Code

**Appendix 1: Data Dictionary**  

**Appendix 2: Key Data Inputs**
Provided by the contest organization, which includes:
1. Covariance data 
  + This dataset is supplied in a long format and was given for every four weeks over a ten year period from 01-03-2007 to 12-21-2016. 
  + (a simple table visualization to help user understand)
  
2. Time series data 
  + This dataset is supplied included the names, SEDOL, Sector, bench weight, etc. for the stocks used in the benchmark portfolio at a given time. 
  + (a simple table visualization to help user understand)
