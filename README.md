# PowerBI_HR_Attrition
# HR Attrition Dashboard

### Dashboard Link : https://app.powerbi.com/groups/me/reports/6a67a4cd-c4ec-45f5-97ac-12e128f3b615/ReportSection?experience=power-bi


### Problem Statement:	Analyse HR Attrition Dataset and make informative output out of it.  

### About Dataset :	Let us first go through the data and try analysing/understanding it to visualize the data in any meaningful way to help to get the solution result as per the company requirements.


### Columns Present in dataset are : 	
•	AGE, which gives the age of each employee
•	ATTRITION, which shows the reduction of workforce by employees leaving company (by value as YES/NO).
•	BUSINESS TRAVELL, the travel information of employees summarized in 3 categories
•	DEPARTMENT, names of departments where the particular employee is working for
•	DISTANCE FROM HOME, shows the overall travel distance from home to office
•	EDUCATION FIELD, particular employee’s background education listed here
•	EMPLOYEE NUMBER, the employee’s number (which is not necessarily needed here)
•	ENVIRONMENT SATISFACTION, GIVES THE RATING FOR THIS AGENDA
•	GENDER, this plays very important role here in order to perform the tasks, since we do not have any employee name/ID so, use it where ever required and it shows the gender of each employee
•	HOURLY RATE, the hourly rate of amount that employees being getting.
•	JOB ROLE, the role of each employees working
•	JOB SATISFACTION, given the rate of job satisfaction
•	MARITAL STATUS, this listed in 3 categories under marital status
•	MONTHLY INCOME, employees getting paid for monthly and the amount has been given in this column
•	MONTHLY RATE, monthly rate of each employee
•	NO. OF COMPANIES WORKED FOR, overall, how many companies the employees had worked for 
•	OVER TIME, here this column gives you the details of over time (OT) using/working by employee
•	% SALARY HIKE, the hike in salary of each employee
•	PERFORMANCE RATING, rating has been given to emp for their overall performance for the year
•	STANDARD HOURS, a fixed standard hour has been given
•	TOTAL WORKING YEARS, total work year experience of employee 
•	YEARS @ COMPANY, experience with the current company has been listed
•	YEARS IN CURRENT ROLE, total number of experiences in current job role of employee
•	YEARS SINCE LAST PROMOTION, as name itself says, total years since last promotion of employee
•	YEARS WITH CURRENT MANAGER, what is the overall of experience/years been working with current manager



### Note:	 Before performing the task, make sure to perform all these steps for better result/output
		 	-Firstly, replace all null values/blank values to 0
 			-Change datatype wherever required 
 			

Now, let us go through the requirements or needed KPIs to perform with the help of this dataset and design a report and include these things, 
visualize the data in any meaningful way to help to analyse the data.
After understanding/visualize the data, design a report for the Hr review information. Make sure to create interactive insight of report.

	

Below are the information/KPIs/demands to be performed in order to meet client’s requirement:

KPIs: 
•	Number of employees by Department and Gender
•	Total employees doing Over Time (Yes/No)
•	Total % of Male and total % of Female (use measure to calculate and then display the value in percentage) 
•	Give the job review with the help of job satisfaction (1 and 2 being BAD else GOOD)
•	Find out best and bottom performers by using performance rate 3 and 4 stars
•	Employees by Business Travel 
•	Count of Marital Status using 3 categories
•	Number of employees left 
•	Use a chart to display average hourly cost(rate) of employees
•	Count of total employees by Job roles
•	How many employees working with the current managers greater than 5 years



### Steps followed 

Data Cleaning:

- Step 1 : Load data into Power BI Desktop, dataset is a csv file.
- Step 2 : Open power query editor & in view tab under Data preview section, check "column distribution", "column quality" & "column profile" options.
- Step 3 : Since there was no null values or errors we directly move on to data preperation 

### Data Preperation
- Step 4 : Calculated Columns :
				 Following Calculated columns are added  with given DAX:

				1) "Male" : Here the Gender column is taken and segregated as  total male employees to eventually count the total number of male employees
				### DAX : Male = if('HR-emp-attrition dataset'[Gender]="male",1,0)

				2) "Female" : Here the Gender column is taken and segregated as  total female employees to eventually count the total number of female employees
				### DAX : Female = if('HR-emp-attrition dataset'[Gender]="female",1,0)

				3)"Job review" = Here Job satisfaction Column is seggregated  on the basis of "Good" and "Bad"
				### DAX : Job Review = IF('HR-emp-attrition dataset'[JobSatisfaction]<3,"Bad","Good")

				4)"Best/Bottom Performer" = Performace Rating Column is seggregated on the basis of "best and bottom performer"
				### DAX : Best/Bottom Performer = IF('HR-emp-attrition dataset'[PerformanceRating]>3,"Best Performer","Bottom Performer")
				
				5)"Emp with Current Managers > 5 Years" = Employees who have completed more than 5 years with the current managers are counted
				### DAX : Emp with Current Mangers >5 Years = if('HR-emp-attrition dataset'[YearsWithCurrManager]>5,1,0)
- Step 5: Measures : 
			1) Total Employees  : 
				### DAX : TotalEmployees = COUNT('HR-emp-attrition dataset'[Gender])

			2) Total Male  :
				### DAX :TotalMale = SUM('HR-emp-attrition dataset'[Male])

			3)Total Female :
				### DAX :TotalFemale = SUM('HR-emp-attrition dataset'[Female]) 
			
			4)Percentage of Male Emp :
				### DAX : Percentage of Male Emp = sum('HR-emp-attrition dataset'[Male])/[TotalEmployees]
			
			5)Percentage of Female Emp :
				### DAX : Percentage of Female Emp = sum('HR-emp-attrition dataset'[Female])/[TotalEmployees]


- Step 6: Data Visualization :
			1) In the report view, under the view tab, theme was selected . along with it Canvas background was selected in the Format Section of the Visualizations Pane
			2) 7 Multirow cards were created to visualize 
				a) "Total Employees" 
				b) "Total Male" 
				c) "Total Female 
				d) "Employee with Managers> years"
				e) " Avg. Hourly rate"
				f) "Percent of Male employee"
				g) " Percent of Female employee"

			3) A Donut Chart where  total male and female employees are visualized department wise 
			4) A Pie Chart  was created to check the Number of employees who work over time 
			5) A horizontal stacked bar chart to  analyze total employees by Job role 
			6) A multirow card to  see the total Best and bottom performers
			7) A Bar chart was created to  visualize the total nuer of employees by "Attrition"
			8) A horizontal stacked bar chart to  see the Total Employees by  Marital Status ,"Married","Single" & "Divorced"
			9)  A Bar chart was created to visualize Total Employees by Job review ,"Good" & "Bad"
			10) Finally a funnel chart was created to show the Total number of Employees by Business Travel mode 


Insights :
1) Out of 1470 employees 882 are male which contitutes 60% of the total employees  and 588 are female which contitutes 40% of the total employees
2) There are total 516 employees who are with their managers for more then 5 years 
3) Average hourly rate of all  the emloyees  is $65.89 

![1st Row](https://github.com/bigit91/PowerBI_HR_Attrition/assets/155818756/2a874903-3598-44a9-8f9a-4a69dab535fe)


4) 416 Employees i.e 28.3% employees work overtime 
5) Max employees (326) are working as sales Executive whereas Min employees(52) work under Human Resource
6) Out of all the employees 226 are best performers 

![2nd row](https://github.com/bigit91/PowerBI_HR_Attrition/assets/155818756/6a6b3f45-43ef-404a-8f2c-fa63c1d430d1)


7) 237 number of employees have left as can be seen in the bar chart
8) There are total 673 - Married  , 460- Single & 327 Divorced employees 
9) 901 employees reviewd the Job as Good 
10) 227 employees travel frequently 

![3rd row](https://github.com/bigit91/PowerBI_HR_Attrition/assets/155818756/23213418-1f38-49dc-bd0f-ff994f1d8adb)			




Dashboard Snap:
![Dashbaord](https://github.com/bigit91/PowerBI_HR_Attrition/assets/155818756/613ed1c6-63db-4c03-a969-aee58d355160)
		
				
