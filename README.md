# 1). COLLECT INITIAL DATA FOR THE TELECOM FIRM-

AIM:
To execute a program which collect initial data for the telecom firm.
PROCEDURE:
IMPORT FROM MICROSOFT EXCEL:
STEP1: From the Sources palette, place an Excel node on the stream canvas.
STEP2: Edit the Excel node. Click the Data tab, if not already selected.
STEP 3: In the File type box, ensure that Excel 2007-2016 (*.xlsx) is selected.
STEP 4: In the Import file box, select telco x customer data.xlsx from the location 
where it is stored.
STEP 5: Ensure that the option First row has column names is enabled.
STEP 6: Click Preview.
STEP 7: Close the Preview output window.
STEP 8: Close the Excel dialog box.
IMPORT FROM A TAB-DELIMITED TEXT FILE:
STEP 1: From the Sources palette, add a Var. File node to the stream canvas.
STEP 2: Edit the Var. File node. Click the File tab, if not already selected.
STEP3: In the File box, select telco x products.tab from the location where it is
stored.
STEP4: Ensure that the option Read field names from file is enabled.
STEP5: In the Field delimiters section, click the Comma check box to disable it.
STEP6: In the Field delimiters section, click the Tab check box to enable it.
STEP 7: Click Preview.
STEP 8: Close the Preview output window.
STEP 9: Close the Var. File dialog box.
 

IMPORT FROM IBM SPSS STATISTICS:
STEP 1: From the Sources palette, add a Statistics File node to the stream canvas.
STEP 2: Edit the Statistics File node. Click the Data tab, if not already selected.
STEP 3: In the File box, select telco x tariffs. sav from the location where it is stored.
STEP 4: Click the Use field format information to determine thestorage checkbox to
enable it.
STEP 5: Click Preview.
STEP 6: Close the Preview output window.
STEP 7: Close the Statistics File dialog box.
SET MEASUREMENT LEVELS:
STEP 1:From the Field Ops palette, add a Type node downstream from the
Microsoft Excel node.
STEP 2: Edit the Type node.
STEP3: Click Read Values
STEP 4: Examine the results in the Values and Measurement column.
STEP 5: Click the cell in the POSTAL_CODE row, Measurement column, and then 
Click Categoricalfrom the drop-down.
STEP6: Click the cell in the REGION row, Measurement column, and then Click 
Categorical from thedrop-down.
STEP 7: Click Read Values.
STEP 8: Close the Type dialog box.
OUTPUT:
RESULT:
 Thus, the Collect initial data for the telecom firm Program has been Executed
Successfully.

# 2). UNDERSTAND TELECOMMUNICATIONS DATA-

AIM:
To Create a stream for collecting initial telecom firm data and understand the data 
properties using the IBM SPSS modeler.
ALGORITHM:
STEP 1: From the Sources palette, place an Excel node then import the input file, as 
telco x customer data.xlsx.
Close the Preview output window and Excel dialog box.
STEP 2: From the Field Ops palette, add a Type node and read the values in the type 
node. Then from the Output palette, add a Table node. Then Run the Table node.


Close the Table output window
STEP 3: From the Output palette, add a Data Audit node downstream from 
the Type node. Then run the Data Audit node.
The minimum value for AGE is -1, which is clearly an invalid value.
STEP 4: Edit theType node Click the cell in the Values column, AGE row (where it reads 
[-1.0, 82.0]), and then click Specify the AGE Values sub-dialog box opens.
Click the Specify values and labels option, set then set Lower to 12 and Upper to 90.
Close the AGE Values sub-dialog box.
STEP 5: Click the cell in the Check column, AGE row, and then click Warn from the 
drop-down
STEP 6: Close the Type dialog box. Youwill rerun the Data Audit node to examine the 
effect of specifying a valid range. Run the Data Audit node. The minimum AGE 
value is still -1, so it seems as if nothing has changed. Close the Data 
Audit output window.
STEP 7: Edit the Type node, click the cell in the Check column in 
the END_DATE row, and then set the action to Discard.
Close the Type dialog box.
STEP 8: Run the Table node that is downstream from the Type node.
Scroll to the right so that you can view END_DATE and then scroll down to verify 
that END_DATE is never $null$.
Only 14,698 records are retained. Close the Table output window.
STEP 9: Edit the Type node. Click the cell in the Missing column, AGE row, and 
then click Specify.
STEP 10: Click the Define blanks check box to enable it. And Below Missing 
values, type -1.
Close the AGE Values sub dialog box. And Close the Type dialog box.
Run the Data Audit node.
The minimum value for AGE is 12 instead of -1.
There are no stream messages so no out-of-range values were found.
OUTPUT:
RESULT:
 Thus, the Colleting and Understanding the telecommunication data. Program has 
been Executed Successfully.

# 3). SET THE UNIT OF ANALYSIS FOR THE TELECOMMUNICATIONS DATA- 


AIM:
To remove duplicate records in the customer dataset and transform a transactional 
dataset into a dataset that has one record per customer using the IBM SPSS modeler.
PROCEDURE TO IMPLEMENTATION:
1. TO REMOVE DUPLICATE RECORDS
STEP 1: Import the data file telco x customer data.xlsx using the Excel source node. 
Then add a Distinct node from the Record Ops palette.
STEP 2: Edit the Distinct node. In the Settings tab. Click the Mode drop-down, to 
view the options. From the Mode, drop-down click Include only the first record 
in each group.
[The Include only the first record in each group option retains only the first
record of the group. You will need this option to remove duplicate records].

STEP 3: Click the Pick from the set of available fields button, click All and then 
click OK.
Connect a Table node and execute it. Check the results.
Starting records – 31,781 and Current result records: 31,769
2. AGGREGATE TRANSACTIONAL DATA
STEP 1: Import the data file telco x products.dat file chose the field delimiter as Tab 
and newline, and add a Table node to it. Then Run this Table node. Close 
the Table output window.
STEP 2: From the Record Ops palette, add an Aggregate node downstream to the 
source node telco x products.dat.
STEP 3: Edit the Aggregate node. Click the Settings tab. In the Key Fields box, 
select CUSTOMER_ID.
STEP 4: In the Basic Aggregates section, in the Aggregate fields sub-section, 
select REVENUES.
Two statistics will be computed by default, mean and sum. Only the sum is required 
in this exercise.
So, Click the check box in the Mean column so that it is disabled.
STEP 5: Ensure that the Include record count in the field check box is enabled and 
then type NUMBER_OF_PRODUCTS in the text box.
STEP 6: Click the Optimization tab. Click the Keys are contiguous check box to 
enable it.
3. CREATE FLAG FIELDS AND AGGREGATE THE DATA
STEP 1: From the Field Ops palette, add a Type node downstream from the Var. 
File node named telco x products.
STEP 2: Edit the Type node. Click the Types tab and then Click Read Values
STEP 3: From the Field Ops palette, add a SetToFlag node downstream from 
the Type node.
STEP 4: Edit the SetToFlag node. In Settings tab click the Set fields drop down and 
then click gadget.
STEP 5: Select all values in the Available set values box and then move them into 
the Create flag fields box.
STEP 6: Click the Aggregate keys check box to enable it. In the Aggregate keys box, 
select CUSTOMER_ID. Click preview
OUTPUT[AGGREGATE]:
OUTPUT [SET TO FLAG]:
RESULT:
 Thus, the Set unit of analysis for the data Remove, Aggregate, Create Program 
has been Executed Successfully.

# 4). IDENTIFY RELATIONSHIPS IN THE TELECOMMUNICATIONS DATA-

AIM:
 To identify relationships between the following:
a) Examine the relationship between categorical.
b) Examine the relationship between a categorical and continuous field.
PROCEDURE TO IMPLEMENTATION:
a) Examine the Relationship between Categorical fields
STEP1: Import the file telco x data.txt. From the Output palette, add a Matrix node 
downstream from the Type node.
STEP 2: Edit the Matrix node.
➢ In the Rows box, select HANDSET.
➢ In the Columns box, select CHURN.
➢ Click the Include missing values check box to disable it.
STEP 3: In the Appearance tab. Click the Percentage of row check box to enable it. 
And also Click the Include row and column totals check box to enable it.
Click Run.
The churn rate for customers with handset ASAD170 is 4.627%, whereas it is 
94.856% for those with handset ASAD90.
Close the Matrix output window.
STEP 4: From the Graphs palette, add a Distribution node downstream from 
the Type node.
STEP 5: Edit the Distribution node.


In the Field box, select HANDSET. In the Color box, select CHURN.
Click the Normalize by color check box to enable it. Click Run.
b) Examine the Relationship between Categorical and Continuous field
STEP 1: From the Output palette, add a Means node downstream from 
the Type node.
STEP 2: Edit the Means node. In the Grouping field box, select CHURN.
Similary In the Test field(s) box, select DROPPED_CALLS. Click Run.
Close the Means output window.
STEP 4: From the Graphs palette, add a Histogram node downstream from 
the Type node
STEP 5: Edit the Histogram node. In the Field box, select DROPPED_CALLS. In 
the Color box, select CHURN. Click Run.
OUTPUT:
RESULT:
 Thus, the Predict Customer churn in the telecom data Program has been Executed 
Successfully.

# 5). PREDICT CUSTOMER CHURN IN THE TELECOM DATASET-

AIM:
To Write a Program to Predict Customer churn in the telecom dataset.
a) Build Model using CHAID
b) Examine the CHAID Model
c) Apply the model to new data

PROCEDURE TO IMPLEMENTATION:
IMPORT DATASET:
STEP 1: Import the dataset telco x modeling data. Excel
STEP 2: Insert a Select node which will only keep the valid records You can insert a
Table node and checkthe output.
STEP 3: From the Field Ops palette, add a Type node downstream from the Select
node.STEP 4: Edit the Type node.
STEP 5: Click the Types tab, if not already selected. Click the Read Values button.
STEP 6: Click the cell in the CHURN row, Role column and then click Target from 
the drop down. STEP 7: Click the cell in the RETENTION row, Role column and
then click None from the drop down.
STEP 8: Click the cell in the DATA_KNOWN row, Role column and then click 
None from the drop down.STEP 9: Close the Type dialog box.
BUILD MODEL:
STEP 1: Click the Modeling tab, Add the CHAID node, located at the far right in
the palette, downstreamfrom the Type node.
STEP 2: Run the CHAID node (right-click it and then click Run).

EXAMINE THE MODEL:
STEP 1: Edit the CHAID model nugget (the yellow diamond)
STEP 2: Click the Model tab, if not already selected.
STEP 3: Click the Viewer tab. Navigate to the root of the tree.
STEP 4: Click Preview.
STEP 5: Scroll all the way to the right in the Table output window.
STEP 6: Close the CHAID model nugget; you will return to the stream.
STEP 7: You can also add an Analysis node from the Output palette in order to
check accuracy.
STEP 8: Run the Analysis Node.
OUTPUT:
Build Model using CHAID:
Examine the CHAID model:
Apply the model to new data:
RESULT:
Thus, the Predict Customer churn in the telecom data Program has been Executed
Successfully.


# 6). CREATE HOMOGENEOUS GROUPS (CLUSTERS) OF CUSTOMERS BASED ON USAGE PATTERNS-

AIM:
To Create homogeneous groups of customers using Segmentation model
in IBM SPSS Modeler.
PROCEDURE TO IMPLEMENTATION:
STEP 1: Insert Type node after importing telco x modeling data.csv
STEP 2: View the Type node. BILL_PEAK and BILL_OFFPEAK have role Input, 
so the clusters will be based on these two fields. 
Records with similar values for BILL_PEAK and BILL_OFFPEAK will be put into 
the same cluster.
STEP 3: Click the Modeling palette, if not already selected. Click 
the Segmentation sub palette at the left side.
STEP 4: Add a Two Step node downstream from the Type node in the lower stream.
STEP 5: Run the Two Step node. STEP 7: Edit the Two Step model nugget that was 
generated.

OUTPUT:
RESULT:
Thus, the Creating homogeneous groups of customers using Segmentation model 
Program has been Executed Successfully.

# 7). USING FUNCTIONS IN IBM SPSS MODELE-

AIM:
To derive new fields using Date Functions and String Function to cleanse and 
enrich a dataset that stores demographic and churn data on the company's customers 
in IBM SPSS Modeler.
ALGORITHM:
Use date functions to derive fields:
STEP1: From the Sources palette, double click the Var. File node to add it to the 
stream canvas.
STEP 2: Double-click the Var. File node to edit the Var. File node.
STEP 3: To the right of the File field, click the Browse for file button, navigate to 
the relevant folder, click the telco x subset.csv file, and then click Open to import the 
data. Do not close the Var. File dialog box.
STEP 4: In the Var. File dialog box, click Preview, and then scroll to the last fields 
in the Preview output window.
STEP 5: Click OK to close the Preview output window and Click OK to close 
the Var. File dialog box.
STEP 6: From the Field Ops palette, double-click the Derive node to add it 
downstream from the Var. File node.
STEP 7: Note: Placing node B downstream from node A means that the data flows 
from A to B.
STEP 8: Edit the Derive node.Under Derive field, type MONTHS_CUSTOMER.

STEP 9: Under Formula,enter date_months_difference(CONNECT_DATE, 
END_DATE).
STEP 10: Note: Type the expression or use the Expression Builder to construct the 
expression. In this course "enter" refers to typing or using the Expression Builder, 
according to your preference. Here, when you use the Expression Builder, look for 
the date_months_difference function in the Date and Time function group.
STEP 11: Click Preview, and then scroll to the last fields in the Preview output 
window. The new field stores the number of months that elapsed between the two 
dates, as a real number. If you want the result as an integer, use a function such as 
round, intof or to_integer.
STEP 12: Close the Preview output window. Close the Derive dialog box.
STEP 13: From the Field Ops palette, add a Derive node downstream from 
the Derive node named MONTHS_CUSTOMER.
STEP 14: Edit the Derive node, and then set the Mode to Multiple.
STEP 15: The Derive dialog box reflects the change. The Derive field box is 
replaced by a Derive from box where the source fields are selected.
STEP 16: Under Derive from, click the Pick from the set of available fields button, 
Ctrl+click CONNECT_DATE and END_DATE, and then click OK.
STEP 17: Beside Field name extension, replace the current extension by _MONTH.
STEP 18: Under Formula, enter datetime_month_name (datetime_month 
(@FIELD)). If you use the Expression Builder, locate 
the datetime_month and datetime_month_name function in the Date and 
Time function group. Locate the @FIELD function in the @ Functions function 
group.
STEP 19: Click Preview, and then scroll to the last fields in the Preview output 
window.
STEP 20: Close the Preview output window. Close the Derive dialog box.
Use string functions to derive fields:
STEP 1: From the Output palette, add a Table node downstream from 
the Derive node named _MONTH.
STEP 2: Right-click the Table node and then click Run then Close the Table output 
window.
STEP 3: From the Field Ops palette, add a Derive node downstream from 
the Derive node named _MONTH (make room by repositioning the Table node, if 
preferred).
STEP 4: Edit the Derive node. Under Derive field, type E-MAIL ADDRESS OK.
STEP 5: Beside Derive as, click Flag from the list.
STEP 6: Under True when, enter count_substring('E-MAIL ADDRESS', "@") = 
1. If you use the Expression Builder, locate the count_substring function in 
the String function group.
STEP 7: Click Preview, and then move E-MAIL ADDRESS OK next to EMAIL_ADDRESS in the Preview output window. (Note: move E-MAIL ADDRESS 
OK by dragging it to the left, until it is just right from E-MAIL ADDRESS.)
STEP 8: Close the Preview output window. Close the Derive dialog box.
STEP 9: From the Field Ops palette, add a Derive node downstream from 
the Derive node named E-MAIL ADDRESS OK.
STEP 10: Edit the Derive node. Under Derive field, type NO E-MAIL ADDRESS.
STEP 11: Beside Derive as, click Flag from the list.
STEP 12: Under True when, enter length ('E-MAIL ADDRESS') = 0. If you use 
the Expression Builder, locate the length function in the String function group.
STEP13: Click Preview, and then move NO E-MAIL ADDRESS next to E-MAIL 
ADDRESS.
STEP 14: Close the Preview output window.
STEP15: Under True when, enter length (trim ('E-MAIL ADDRESS')) = 0. If you 
use the Expression Builder, locate the length and trim function in 
the String function group.
Click Preview.
STEP 16: Close the Preview output window. Then Close the Derive dialog box.
STEP 17: From the Field Ops palette, add a Derive node downstream from 
the Derive node named NO E-MAIL ADDRESS.
STEP 18: Edit the Derive node. Under Derive field, type POSITION PERIOD.
STEP 19: Under Formula, enter locchar_back (., length ('E-MAIL ADDRESS'), 
'E-MAIL ADDRESS'). If you use the Expression Builder, locate 
the locchar_back and length function in the String function group.
STEP 20: Click Preview, and then move POSITION PERIOD next to E-MAIL 
ADDRESS.
STEP 21: Close the Preview output window. Close the Derive dialog box.
STEP 22: From the Field Ops palette, add a Derive node downstream from 
the Derive node named POSITION PERIOD.
STEP 23: Edit the Derive node. Under Derive field type DOMAIN NAME.
STEP 24: Beside Derive as, click Conditional from the list.
STEP 25: Under If, enter 'POSITION PERIOD' > 0.
STEP 26: Under Then, enter substring_between ('POSITION PERIOD' + 1, 
length ('E-MAIL ADDRESS'), 'E-MAIL ADDRESS'). If you use the Expression 
Builder, locate the substring_between and length function in the String function 
group.
STEP 27: Under Else, type undef.
Click Preview, and then scroll to the last fields in the Preview output window.
STEP 28: Close the Preview output window. Then Close the Derive dialog box.
OUTPUT:
Use date functions to derive fields:
Use string functions to derive fields:
RESULT:
 Thus, the Create Segmentation Model Program has been Executed Successfully.


# 8). ADD FIELDS TO THE TELECOMMUNICATIONS DATA-

AIM:
 To write a Program for Add Fields to the Telecommunication data.
a) Drive fields as formula
b) Derive fields as flag or nominal.
ALGORITHM:
 Derive fields as formula:
STEP 1: Import the dataset telco x data.txt
STEP 2: From the Field Ops palette, add a Derive node downstream from 
the Type node.
STEP 3: Edit the Derive node. Click the Settings tab, if not already selected.
STEP 4: In the Derive field box, type BILL_PEAK.
STEP 5: Click the Derive as drop down. From the Derive as drop down, 
click Formula, if not already selected.
STEP 6: Click the Field type drop down. Click the Launch expression 
builder button.
STEP 7: In the Formula box, enter PEAK_MINS * PEAK_RATE/100, by typing it 
or by pasting the field names from the list of fields, whatever you feel comfortable 
with.
STEP 8: Click the Check button. Click OK to close the Expression Builder.
STEP 9: From the Field Ops palette, add a Derive node downstream from 
the Derive node named BILL_PEAK.

STEP 10: Edit the Derive node. Click the Settings tab, if not already selected.
STEP 11: Derive field box: BILL_OFFPEAK
STEP 12: Derive as: Formula (the default)
STEP 13: Field type: <Default>; the field will then be auto-typed as Continuous
STEP 14: Expression: OFFPEAK_MINS * OFFPEAK_RATE/100 (if preferred, 
use the Expression Builder)
Close the Derive dialog box.
STEP 15: From the Field Ops palette, add a Derive node downstream from 
the Derive node named BILL_OFFPEAK.
STEP 16: Edit the Derive node. Click the Settings tab, if not already selected.
STEP 17: Derive field box: BILL_TOTAL
STEP 18: Derive as: Formula (the default)
STEP 19: Field type:<Default>; the field will then be auto-typed as Continuous
STEP 20: Expression: BILL_PEAK + BILL_OFFPEAK (if preferred, use the 
Expression Builder)
STEP 21: Click Preview. Then Close the Preview output window.
Close the Derive dialog box.
 Derive fields as flag or nominal:
STEP 1: From the Field Ops palette, add a Derive node downstream from 
the Derive node named BILL_TOTAL.
STEP 2: Edit the Derive node. Click the Settings tab, if not already selected.
STEP 3: Derive field box: BILL_GT_0
STEP 4: Derive as: Flag
STEP 5: Field type: Flag (should be set automatically to Flag when you choose 
Derive as: Flag)
STEP 6: True value: T (the default) and False value: F (the default)
STEP 7: True when box: BILL_TOTAL > 0. Close the Derive dialog box.
STEP 8: From the Field Ops palette, add a Derive node downstream from 
the Derive node named BILL_GT_0.
STEP 9: Edit the Derive node Click the Settings tab, if not already selected.
STEP 10: Derive field box: SEGMENT
STEP 11: Derive as: Nominal and Field type: Ordinal
STEP 12: Click the cell in the Set field to column and then type 1.
STEP 13: Click the cell in the If this condition is true column and then 
type BILL_TOTAL <= 100.
STEP 14: Repeat the previous two steps for the following values and expressions:
STEP 15: Set field to: 2 If this condition is true: BILL_TOTAL <= 200
STEP 16: Set field to: 3 If this condition is true: BILL_TOTAL > 200
STEP 17: In the Default value box, type undef. Then Close the Derive dialog box.
OUTPUT:
Drive fields as formula:
Derive fields as flag or nominal:
RESULT:
 Thus, the Add fields to the Telecommunication data Program have been 
Executed Successfully.

# 9). CREATE A LINEAR REGRESSION MODEL TO PREDICT EMPLOYEE SALARIES-


AIM:
 To Create a Linear Regression Model to predict Employee Salaries.
ALGORITHM:
Import and examine the data
STEP1: From the Sources palette, add a Var. File node to a blank stream canvas, 
edit the node, point to employee_data.txt, and then close the Var. File dialog 
box.
STEP2: From the Output palette, add a Table node downstream from the Var. 
File node, run it, and then examine the output. The dataset is comprised of 474 
employees.
Close the Table output window.
STEP 3: From the Output palette, add a Data Audit node downstream from 
the Var. File node, run it, and then examine the output.
Set measurement levels and roles:
STEP 1: From Field Ops, add a Type node downstream from the Var. File node.
STEP 2: Edit the Type node. Click Read Values
STEP 3: set the Measurement for educational_level to Ordinal
STEP 4: The Role from gender to months_previous_experience is set to Input
STEP 5: set the Role for current_salary to Target

Create Linear Regression Model:
STEP 1: From the Modeling palette, add a Linear node downstream from 
the Type node.
STEP 2: Edit the Linear node. Click the Build Options tab
STEP 3: click the Basics item and clear the Automatically prepare data check box
STEP 4: click the Model Selection item and set the Model Selection method 
to Include all predictors
STEP 5: click Run
STEP 6: Edit the generated model nugget, and then click the Model Summary item in 
the pane on the left.
STEP 7: Click the Predictor Importance item in the pane on the left.
STEP 8: The job_category field is by far the most important predictor. Gender is the 
second most important field. Region and age are least important.
STEP 9: Click the Predicted by Observed item in the pane on the left.
STEP 10: The points are not scattered around the diagonal and the predicted values 
seem to break up in two categories.
STEP 11: Click the Coefficients by Observed item in the pane on the left, and then, 
from the Style list, select Table.
OUTPUT:
RESULT:
 Thus, the Create Linear regression model to predict Employee Salaries Program 
has been Executed Successfully.


# 10). USE LOGISTIC REGRESSION TO PREDICT RESPONSE TO A CHARITY PROMOTION CAMPAIGN-


AIM: 
 To write a Use Logistic Regression to Predict Response to a Charity Promotion 
Campaign
ALGORITHM: 
Import and examine the data
STEP 1: From the Sources palette, double-click the Var. File node to add it to the 
stream. Import the dataset charity.csv
STEP 2: From the Output palette, add a Data Audit node downstream from 
the Var. File node, run the Data Audit node
STEP 3: double-click the Sample Graph for the response to campaign field.
Partition the data and set the roles:
STEP 1: From the Field Ops palette, add a Partition node downstream from 
the Var. File node,
STEP 2: Set the Training partition size to 70% and the Testing partition size to 
30%. Ensure that the Repeatable partition assignment option is enabled, with seed 
value 1234567.
STEP 3: From the Field Ops palette, add a Type node downstream from the Partition 
node.
STEP 4: Edit the Type node, and then click the Read Values button. The Values 
column is populated with values from the data.

STEP 5: Set the Role for gender, age, mosaic bands, pre-campaign expenditure, 
and pre-campaign visits to Input
STEP 6: Set the Role for response to campaign to Target
STEP 7: Ensure that the Role for the Partition field is set to Partition
STEP 8: Set the Role for all other fields to None
Create the Logistic Regression Models:
STEP 1: From the Modeling palette, add a Logistic node downstream from 
the Type node.
STEP 2: Edit the Logistic node and click the Model tab
STEP 3: For Procedure, select the Binomial option
STEP 4: close the Logistic dialog box
STEP 5: Add a second Logistic node downstream from the Type node.
STEP 6: Edit the second Logistic node, and then: click the Model tab
STEP 7: For Procedure, select the Binomial option
STEP 8: below Categorical inputs, select mosaic bands, and for Base Category, 
select First
STEP 9: click the Annotations tab, select the Custom option, and type custom close 
the Logistic dialog box
STEP 10: Select the two Logistic nodes, right-click one of them, and click Run 
Selection.
STEP 11: Edit the Logistic model nugget named response to campaign, click the 
Advanced tab, and scroll down to the Variables in the Equation table (the last table in 
the output).
STEP 12: Close the Logistic output window.
STEP 13: Edit the Logistic model nugget named custom, click the Advanced tab, and 
scroll to the Categorical Variables Coding’s table.
STEP 14: You can add an Analysis node at the end and check accuracy levels.
OUTPUT:
RESULT:
 Thus, the Use of Logistic Regression to Predict Response to a Charity Promotion 
Campaign Program has been Executed Successfully.

