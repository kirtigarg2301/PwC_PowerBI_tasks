I have done three tasks/projects of PwC Switzerland PowerBI virtual internship. three tasks are: call center performance dashboard; churn analysis dashboard and diversity and inclusion dashboard.

CALL CENTER Performance DASHBOARD:

I have followed following steps:
        1. Data preparation:
                Received Data: I got an Excel sheet from the company with information like Call ID, Agent, Date, Time, Topic, Answered (Y/N), Resolved, Speed of                                         Answer, AvgTalkDuration, and Satisfaction Rating.
                Data Check: First, I looked at the data in Excel to understand its structure.
        2.Cleaning in Power BI: Next, I imported this data into Power BI. In Power Query Editor, I did some cleaning:
                 Handling Null Values: I replaced empty cells with 0 in some columns. This was because there were no clear patterns in those columns, and I didn’t have                                        additional insights from stakeholders to understand why the cells were empty.
                Answered (Y/N) and Resolved: You changed "N" and "Y" to "No" and "Yes" to make it easier for people to understand.
                Column Adjustments: I renamed "AvgTalkDuration" to "Avg. Talk Duration" and adjusted it to show only the time part because it was about how long calls                                      lasted each day.
                Time Column: Similarly, I changed the format of the "Time" column to show only the time part, not the date.
        Data Ready for Dashboard: After these changes, data was clean and ready to be used for creating your Power BI dashboard.
        In essence, I prepared the data by making it more organized and understandable for creating visualizations in Power BI.
        
        3. Creating measures with DAX functions in Power BI  (essential for calculating KPIs and metrics)
                   Note:DAX (Data Analysis Expressions): It's a language used in Power BI (and also in Excel Power Pivot) for creating custom calculations and                                  measures. These measures are crucial for generating insights and performing calculations within your reports and dashboards.
                some calculations I did:
                        CALLS ANSWERED = COUNTX(FILTER(Sheet1,Sheet1[Answered (Y/N)]="YES"),Sheet1[Answered (Y/N)])
                        CALLS UNASWERED = COUNTX(FILTER(Sheet1,Sheet1[Answered (Y/N)]="NO"),Sheet1[Answered (Y/N)])
                        RESOLVED CALLS = CALCULATE(COUNT(Sheet1[Call Id]),FILTER(Sheet1,Sheet1[Resolved]="YES"))
                        UNRESOLVED CALLS = CALCULATE(Sheet1[TOTAL CALLS]-Sheet1[RESOLVED CALLS])
                        TOTAL CALLS = CALCULATE(Sheet1[CALLS ANSWERED]+Sheet1[CALLS UNASWERED])
                        count of satisfaction rating = count(Sheet1[Satisfaction rating])
                        positive satisfaction rating = CALCULATE(count(Sheet1[Satisfaction rating]),filter(Sheet1,Sheet1[Satisfaction rating] in {3,5}))
                        overall customer satisfaction score = DIVIDE([positive satisfaction rating],[count of satisfaction rating],0)
        5. now I used different types of visualization tools and create the dashboard.

![CALL CENTER PERFORMANCE DASHBOARD](https://github.com/kirtigarg2301/PwC_PowerBI_tasks/assets/159450818/2faf8d37-ebad-4ab5-b873-f77e9495e013)


CUSTOMER CHURN ANALYSIS DASHBOARD:
        
        The purpose of this project is to provide a Business Analysis Solution to minimize Customer churn rate for a Telecom service provider.
        To do that I did data collection, data preparation, data processing, some clacluation and at last create dashboard.
        
        Data collection: PwC provided data (excel sheet) of customer churn.
        
        Data preparation: I started by opening dataset in Excel to understand its structure and contents. Here’s what I found:
                Number of Rows and Columns: The dataset contains 7,044 rows (entries) and 23 columns (features or variables).
                Column Names: The columns in your dataset are: CustomerID, Gender, SeniorCitizen, Partner, Dependents, Tenure, PhoneService, MultipleLines,                                           InternetService, OnlineSecurity, OnlineBackup, DeviceProtection, TechSupport, StreamingTV, StreamingMovies, Contract, PaperlessBilling,                                 PaymentMethod, MonthlyCharges, TotalCharges, NumAdminTickets, NumTechTickets, and Churn.
                Types of Data: I identified various types of data in each column, such as customer demographics (like Gender, SeniorCitizen, Partner, Dependents),                                   services subscribed to (PhoneService, InternetService, etc.), billing information (MonthlyCharges, TotalCharges), and service tickets                                   (NumAdminTickets, NumTechTickets).
                Null Values: I checked for null values (empty cells) across the dataset to understand if any data was missing, which is crucial for ensuring the                                   accuracy and completeness of your analysis.
        Understanding these details helps to prepare the dataset for further analysis, such as cleaning the data, creating visualizations, or building predictive               models in tools like Power BI or Excel itself.
        
        Data processing: After checking out the dataset in Excel, I switched to Power BI. I connected to the dataset and started cleaning and processing it in the                               Power Query Editor. Here are the steps I took:
                                Handling Null Values: I replaced empty cells with appropriate values where needed. This ensures consistency and accuracy in the data.
                                Renaming and Reformatting Columns: I renamed columns for clarity and adjusted their formats if necessary to better suit the analysis.
                                Filtering and Sorting Data: I filtered out unnecessary data and sorted the dataset to focus on relevant information.
                                Removing Duplicates: I checked for and removed any duplicate rows to maintain data integrity.
        These steps in Power BI's Power Query Editor helped prepare the dataset for creating visualizations and performing deeper analysis in the dashboard.
        
         DAX:
                CHURNED = CALCULATE(COUNTX(FILTER(sheet2,sheet2[Churn]="yes"),sheet2[Churn]))
                RETAINED = COUNTX(FILTER(sheet2,sheet2[Churn]="no"),sheet2[Churn])
                TOTAL CUSTOMERS = CALCULATE(sheet2[CHURNED]+sheet2[RETAINED])
                TOTAL REVENUE = CALCULATE(sheet2[TOTAL REVENUE(CHURNED)]+sheet2[TOTAL REVENUE(RETAINED)])
                TOTAL REVENUE(CHURNED) = CALCULATE(SUM(sheet2[TotalCharges]),sheet2[Churn]="yes")
                TOTAL REVENUE(RETAINED) = CALCULATE(SUM(sheet2[TotalCharges]),sheet2[Churn]="no")
                REVENUE LOSS = CALCULATE(sheet2[TOTAL REVENUE]-sheet2[TOTAL REVENUE(RETAINED)])
                
        Now I used different types of visualization tools and create the dashboard.
![CUSTOMER CHURN ANALYSIS](https://github.com/kirtigarg2301/PwC_PowerBI_tasks/assets/159450818/b27621ff-8bcd-4d48-af21-2bf93f02f38f)


Diversity and Inclusion dashboard
        My task is to define relevant KPIs in hiring, promotion, performance and turnover, and create a visualization
        
        Data Preparation: I used ’03 Diversity-Inclusion-Dataset’ provided by PWC. I organized the data with the help of powerbi query editor and load it.
        
        DAX:
                male = CALCULATE(COUNT(sheet3[Gender]),FILTER(sheet3,sheet3[Gender]="male"))
                female = CALCULATE(COUNT(sheet3[Gender]),FILTER(sheet3,sheet3[Gender]="female"))
                female promoted in FY2020 = CALCULATE(COUNT(sheet3[Promotion in FY20?]),FILTER(sheet3,sheet3[Gender]="female"),sheet3[Promotion in FY20?]="yes")
                female promoted in FY2021 = CALCULATE(COUNT(sheet3[Promotion in FY21?]),FILTER(sheet3,sheet3[Gender]="female"),sheet3[Promotion in FY21?]="yes")
                male promoted in FY2020 = CALCULATE(COUNT(sheet3[Promotion in FY20?]),FILTER(sheet3,sheet3[Gender]="male"),sheet3[Promotion in FY20?]="yes")
                male promoted in FY2021 = CALCULATE(COUNT(sheet3[Promotion in FY21?]),FILTER(sheet3,sheet3[Gender]="male"),sheet3[Promotion in FY21?]="yes")
                leaver FY20 = calculate(count(sheet3[FY20 leaver?]),FILTER(sheet3,sheet3[FY20 leaver?]="yes"))
                total employees = CALCULATE(sheet3[female]+sheet3[male])

         Now I used different types of visualization tools and create the dashboard.

![diversity(performnace and turnover](https://github.com/kirtigarg2301/PwC_PowerBI_tasks/assets/159450818/b32677c3-54ff-4844-a247-bbf3d247070a)
![diversion(hiring and promotion](https://github.com/kirtigarg2301/PwC_PowerBI_tasks/assets/159450818/e2d9ab2b-b829-456e-8957-0f26f72fff8b)

Overall I learned a lot through this internship, like how to create an attractive dashboard, define KPIs, and DAX formulas, and clearly visualize data to tell actionable insights.


        
        

