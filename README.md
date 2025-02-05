# COMMENTS ON THE DEVELOPED CODE

> [!INFO]
> Please avoid data model changes, but if needed please include them in a install.sql file placed next to the application export file
> After finishing the problems, create a public repository in Github, push your code and send us the Github Public URL
> If for some reason this is not possible, send us a zip folder containing both `first-problem/webapp` and `second-problem/webapp` folders.

    No changes were made to the data model.


## First Problem
The only change made was related to the item P5_HIRE_DATE, changing its data type to Date.

## Second Problem
Some decisions were made due to the flexibility in interpreting the requirements. I will add notes where the interpretations were less clear.

Development Assumptions:
 - All data manipulation to be done on top of APEX Collections
 - Up to the candidate to decide if save is done in each Interactive Grid or at page level
     - Expect to be asked why you made either decision
 Development guidelines:
 - Create application with title 'Manage Employees':
    - Create page manage employee
         - Create region with title 'Dashboards' that includes:
             - 1 badge with total number of employees
             - 1 bar chart with number of employees per department
         - Create region named 'Assign employee', which is expected to contain:
             - 2 interactive grids defined as master / detail
                 - The master interactive grid will have the following functionality:
                     - Data based on department table
                     - Fields:
                         - Name
                         - Cost Center
                     - Remove button in the interactive grid toolbar
                        - Button only available for click once a department record is selected, and only one at a time
                     - Implement remove department with an AJAX callback from master
                         - Remove a department will remove the references to those departments from the employees assigned to it
                 - The detail interactive grid will have the following functionality:
                     - Data based on employees
                     - Fields:
                         - Department name
                         - First Name
                         - Last Name
                         - Email
                         - Hire Date
                         - City
                         - Country
                         - Job
                     - Add/Remove buttons in the interactive grid toolbar
                     - Add button will open a popup dialog to search for an employee and will have a OK button at the bottom right corner and close at the left bottom corner:
                         - OK persists the employee to the collection [PS] - only update is allowed and the department is bounded by the choice selected in the master table
                         - Close, closes the dialog
                         - Form fields:
                             - First Name
                             - Last Name
                             - Email
                             - Hire Date (Date picker)
                             - City
                             - Country
                             - Job (LOV)
                             [PS] - Department is also shown, altough it is disable, for clarity 
                     - Remove button will remove users with an AJAX callback [PS] - removal, as I understood it, from the department; the user remains in the db but with no department assigned


