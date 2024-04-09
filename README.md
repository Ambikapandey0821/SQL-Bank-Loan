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

-- Total loan Amount issued--

    select SUM(loan_amount) as total_loan_amount from bank_loan
    
![image](https://github.com/Ambikapandey0821/SQL-Bank-Loan/assets/162020155/f5c63379-4f24-4a52-b091-64d3619a07da)

-- Total Loan Amount issued on the Month Of December--

    select SUM(loan_amount) as Month_loan_amount from bank_loan where MONTH(issue_date) = 12

![image](https://github.com/Ambikapandey0821/SQL-Bank-Loan/assets/162020155/0ae595e0-8678-4df9-9e7a-3bf69b305f01)

-- Total loan Amount Collected--

    select SUM(total_payment) as Total_collected_amount from bank_loan

![image](https://github.com/Ambikapandey0821/SQL-Bank-Loan/assets/162020155/7674414d-fd39-43f1-9961-9ae2da1e7a55)


-- Total Loan Amount Collected on the Month Of December--

    select SUM(total_payment) as Dec_month_total_collection from bank_loan where MONTH(issue_date)=12

![image](https://github.com/Ambikapandey0821/SQL-Bank-Loan/assets/162020155/346f0c2f-d89b-471c-ac74-bfdd03942ad7)

-- Average Interest Rate--

    select round(AVG(int_rate)*100,2) as Average_interest_rate from bank_loan

![image](https://github.com/Ambikapandey0821/SQL-Bank-Loan/assets/162020155/aa478e96-e69d-4584-a8d7-14e212abfac2)

-- Average DTI (Debt to Income Ratio)--

    select round(AVG(dti)*100,2) as Average_interest_rate from bank_loan

![image](https://github.com/Ambikapandey0821/SQL-Bank-Loan/assets/162020155/b01281cc-0015-4bb7-b4fa-58b5bbf79219)

 --Good loan percentage--

    select (count(case when loan_status='Fully Paid' Or loan_status='current' then ID end)*100.0)/COUNT(ID) AS Good_loan_percentage from bank_loan
    
![image](https://github.com/Ambikapandey0821/SQL-Bank-Loan/assets/162020155/2d3d8540-c6c8-4af1-9fa9-d5e64ea79aa7)

--Good loan count--

    select COUNT(id) as Good_loan_applications from bank_loan where loan_status='Fully Paid' Or loan_status='current'
    
![image](https://github.com/Ambikapandey0821/SQL-Bank-Loan/assets/162020155/a180a617-e953-401e-b484-8aa6778a357f)

--Good loan applications--
 
    select COUNT(id) as Good_loan_applications from bank_loan where loan_status='Fully Paid' Or loan_status='current'
    
![image](https://github.com/Ambikapandey0821/SQL-Bank-Loan/assets/162020155/ed83a117-a331-430a-810e-cfda1aa2c18e)

--Good loan funded amount--

    select SUM(loan_amount) as Good_loan_funded_amount from bank_loan where loan_status='Fully Paid' Or loan_status='current'

![image](https://github.com/Ambikapandey0821/SQL-Bank-Loan/assets/162020155/f52c8045-bc2b-4820-ab46-5d428b00e0e8)    

--Good loan amount received--

    select SUM(total_payment) as Good_loan_amount_received from bank_loan where loan_status='Fully Paid' Or loan_status='current'

![image](https://github.com/Ambikapandey0821/SQL-Bank-Loan/assets/162020155/e4ba611c-5c2e-4d85-acbe-0df78eaac908)

-- Bad loan issued--

    select COUNT(case when loan_status='charged off' then id end)*100/COUNT(id) as Bad_loan_issuance_percentage from bank_loan

![image](https://github.com/Ambikapandey0821/SQL-Bank-Loan/assets/162020155/35a919a4-9a42-42d5-9516-05681198e368)

-- Bad loan application--

    SELECT COUNT(id) AS Bad_Loan_Applications FROM bank_loan WHERE loan_status = 'Charged Off'

![image](https://github.com/Ambikapandey0821/SQL-Bank-Loan/assets/162020155/5ed350da-f650-4577-a478-c48277e9d34f)

--Bad Loan Funded Amount--

    SELECT SUM(loan_amount) AS Bad_Loan_Funded_amount FROM bank_loan WHERE loan_status = 'Charged Off'

![image](https://github.com/Ambikapandey0821/SQL-Bank-Loan/assets/162020155/228d727a-6f40-4b9d-af7b-1817cab21d56)

--Bad Loan Amount Charged off-- 

    SELECT SUM(total_payment) AS Bad_Loan_amount_received FROM bank_loan WHERE loan_status = 'Charged Off'

![image](https://github.com/Ambikapandey0821/SQL-Bank-Loan/assets/162020155/802e5c4e-ab12-4324-b22f-f20455a006bc)

-- Loan Status, Count of Loan, Total Funded Amount, Total Amount Received, Avg Interest Rate, Avg DTI --

    select loan_status, COUNT(id) as Loan_count, SUM(loan_amount) as Total_funded_amount, SUM(total_payment) as Total_amount_received, AVG(int_rate*100) as Interest_rate, avg(dti*100)       as DTI from bank_loan group by loan_status
    
![image](https://github.com/Ambikapandey0821/SQL-Bank-Loan/assets/162020155/67545d28-bf91-444e-965f-0d6213a9e5fd)
 
--B.	BANK LOAN REPORT | OVERVIEW--

    select MONTH(issue_date) as Month_no, DATENAME(month, issue_date) as Month_name, COUNT(id) as Total_loan_applications,
    SUM(loan_amount) as Total_loan_funded, SUM(total_payment) as Total_amount_received
    from bank_loan
    group by MONTH(issue_date), DATENAME(month,issue_date) order by MONTH(issue_date)

![image](https://github.com/Ambikapandey0821/SQL-Bank-Loan/assets/162020155/73ecb096-4143-4cab-8c66-16f0ab810660)

--STATE--

    SELECT 
	    address_state AS State, 
	    COUNT(id) AS Total_Loan_Applications,
	    SUM(loan_amount) AS Total_Funded_Amount,
	    SUM(total_payment) AS Total_Amount_Received
    FROM bank_loan
    GROUP BY address_state
    ORDER BY address_state

![image](https://github.com/Ambikapandey0821/SQL-Bank-Loan/assets/162020155/5d5dd60f-1592-42ed-af90-825553e64942)

--TERM--

    SELECT 
	    term AS Term, 
	    COUNT(id) AS Total_Loan_Applications,
	    SUM(loan_amount) AS Total_Funded_Amount,
	    SUM(total_payment) AS Total_Amount_Received
    FROM bank_loan
    GROUP BY term
    ORDER BY term
    
![image](https://github.com/Ambikapandey0821/SQL-Bank-Loan/assets/162020155/234af33c-069f-4ce9-8cd2-278499a290db)

--EMPLOYEE LENGTH--

    SELECT 
	    emp_length AS Employee_Length, 
	    COUNT(id) AS Total_Loan_Applications,
	    SUM(loan_amount) AS Total_Funded_Amount,
	    SUM(total_payment) AS Total_Amount_Received
    FROM bank_loan
    GROUP BY emp_length
    ORDER BY emp_length
    
![image](https://github.com/Ambikapandey0821/SQL-Bank-Loan/assets/162020155/b054223f-95fa-4c17-a28e-78d7849ec355)

--PURPOSE--

    SELECT 
	    purpose AS PURPOSE, 
	    COUNT(id) AS Total_Loan_Applications,
	    SUM(loan_amount) AS Total_Funded_Amount,
	    SUM(total_payment) AS Total_Amount_Received
    FROM bank_loan
    GROUP BY purpose
    ORDER BY purpose

![image](https://github.com/Ambikapandey0821/SQL-Bank-Loan/assets/162020155/e58bf095-48cb-4fd7-a108-757fb79d3092)

--HOME OWNERSHIP--

    SELECT 
    	home_ownership AS Home_Ownership, 
    	COUNT(id) AS Total_Loan_Applications,
    	SUM(loan_amount) AS Total_Funded_Amount,
    	SUM(total_payment) AS Total_Amount_Received
    FROM bank_loan
    GROUP BY home_ownership
    ORDER BY home_ownership

![image](https://github.com/Ambikapandey0821/SQL-Bank-Loan/assets/162020155/1026de95-a55f-4d54-8cd5-79e8d7291309)

