# SQL-Bank-Loan 


## Problem Statement

"Many banks struggle with efficiently managing and analyzing the vast amount of loan data they collect on a daily basis.
This leads to inefficiencies in decision-making processes and a lack of timely insights into loan performance and risk.
The objective of this Power BI project is to develop a solution that allows banks to effectively visualize and 
analyze loan data in real-time, enabling them to make informed decisions, mitigate risks, and improve overall loan management efficiency."


-- Total Applications--

    select COUNT(id) as total_loan_count from bank_loan

    ![image](https://github.com/Ambikapandey0821/SQL-Bank-Loan/assets/162020155/c6a049db-2e1a-4aef-a3c5-ea61794167d2)
    
-- Total Applications on the Month Of December--

    select COUNT(id) as loan_count from bank_loan where MONTH(issue_date)=12
    
    ![image](https://github.com/Ambikapandey0821/SQL-Bank-Loan/assets/162020155/cada4e70-780f-4b39-971c-ba407d78fd66)
