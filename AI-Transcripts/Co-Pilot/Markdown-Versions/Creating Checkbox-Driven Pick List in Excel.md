# Creating Checkbox-Driven Pick List in Excel  

## Me
In excel, how can I create a column (column C, sheet 2) that contains tick boxes and when the box is ticked, it adds a name from a People column (column A, sheet 2) to a pick list on a diffrent sheet (sheet 1)?  

## Co-Pilot
[1]: https://www.youtube.com/watch?v=Jj1iJSnXEG8 ""
[2]: https://trumpexcel.com/insert-checkbox-in-excel/ ""
[3]: https://www.youtube.com/watch?v=ViEHzRPVj-M ""
[4]: https://support.microsoft.com/en-us/office/using-checkboxes-in-excel-da85546d-c110-49b8-b633-9cebadcaf8d4 ""
[5]: https://answers.microsoft.com/en-us/msoffice/forum/all/excel-auto-create-a-tickbox-based-on-whether/b02dc4fb-062c-4ca0-b797-cff0194356c0 ""
[6]: https://www.exceldemy.com/filter-checkboxes-in-excel/ ""
[7]: https://www.howtogeek.com/698565/how-to-create-a-checklist-in-microsoft-excel/ ""

Certainly! Let's break this down into steps:

1. **Insert Checkboxes in Column C (Sheet 2):**
   - Select the range in column C where you want the checkboxes.
   - Go to the **Insert** tab and click on **Checkbox** in the **Form Controls** section.
   - You'll see checkboxes appear in the selected cells.

2. **Link Checkboxes to Names in Column A (Sheet 2):**
   - Now, you want the checkboxes to correspond to names in column A.
   - For each checkbox, right-click it and choose **Format Control**.
   - In the **Control** tab, specify a **Cell link** (e.g., a cell in column D) for each checkbox. This cell will show TRUE when the checkbox is checked and FALSE when unchecked.

3. **Create the Pick List on Sheet 1:**
   - On Sheet 1, create a list (e.g., in column E) with the names you want to include in the pick list.
   - Use a formula to filter this list based on the TRUE/FALSE values from the linked cells in column D (Sheet 2). For example:
     ```
     =IF(Sheet2!D1, Sheet2!A1, "")
     ```
     This formula checks if the checkbox in D1 is checked (TRUE) and returns the corresponding name from A1.

4. **Repeat for Other Rows:**
   - Copy the formula down for other rows in column E to include all names based on the checkboxes.

Now, when you check a box in column C (Sheet 2), the corresponding name from column A (Sheet 2) will appear in your pick list on Sheet 1. 🎉

Remember to adjust cell references based on your actual sheet names and ranges! If you need further assistance, feel free to ask! 😊


Learn more: [1. www.youtube.com](https://www.youtube.com/watch?v=Jj1iJSnXEG8) 
[2. trumpexcel.com](https://trumpexcel.com/insert-checkbox-in-excel/) 
[3. www.youtube.com](https://www.youtube.com/watch?v=ViEHzRPVj-M) 
[4. support.microsoft.com](https://support.microsoft.com/en-us/office/using-checkboxes-in-excel-da85546d-c110-49b8-b633-9cebadcaf8d4) 
[5. answers.microsoft.com](https://answers.microsoft.com/en-us/msoffice/forum/all/excel-auto-create-a-tickbox-based-on-whether/b02dc4fb-062c-4ca0-b797-cff0194356c0) 
[6. www.exceldemy.com](https://www.exceldemy.com/filter-checkboxes-in-excel/) 
[7. www.howtogeek.com](https://www.howtogeek.com/698565/how-to-create-a-checklist-in-microsoft-excel/)  

## Me
Thank you! Can I also add a dropdown list for the pick list?  

## Co-Pilot
Certainly! You can create a dropdown list for the pick list on Sheet 1. Here's how:

1. **Create the Dropdown List:**
   - On Sheet 1, choose a cell where you want the dropdown list.
   - Go to the **Data** tab and click on **Data Validation**.
   - In the **Settings** tab:
     - Set **Allow** to **List**.
     - In the **Source** field, enter the range of names from column E (where you filtered the names based on checkboxes).
   - Click **OK**.

2. **Link the Dropdown to the Pick List:**
   - Now, when you select a name from the dropdown, it will show the corresponding name from your filtered list.

Remember to adjust cell references based on your actual sheet names and ranges! If you need further assistance, feel free to ask! 😊  

## Me
What about when creating the pick list, if I want to concatenate 2 cells e.g. if sheet 2 cell A1 says "Hasan Akhtar" and sheet 2 cell B1 says "AI Research Intern" then I want the output to be "Hasan Akhtar - AI Research Intern". Bear in mind, I still want the condition to be if sheet 2 cell D1 is True then show the name  

## Co-Pilot
Certainly! To create the concatenated output based on the conditions you've described, follow these steps:

1. **Concatenate Names (Sheet 2):**
   - In Sheet 2, create a new column (let's say column E) where you want the concatenated names.
   - Use the following formula in cell E1 (assuming A1 contains the name and B1 contains the role):
     ```
     =IF(Sheet2!D1, Sheet2!A1 & " - " & Sheet2!B1, "")
     ```
     This formula checks if the checkbox in D1 is checked (TRUE). If it is, it concatenates the name from A1 with the role from B1, separated by " - ". Otherwise, it leaves the cell blank.

2. **Create the Pick List on Sheet 1:**
   - On Sheet 1, create a list (e.g., in column F) with the concatenated names from column E (where the checkboxes are TRUE).
   - Use a formula similar to the previous one to filter this list based on the TRUE/FALSE values from the linked cells in column D (Sheet 2).

Now, when you check a box in column C (Sheet 2), the corresponding concatenated name will appear in your pick list on Sheet 1. 🎉

Remember to adjust cell references based on your actual sheet names and ranges! If you need further assistance, feel free to ask! 😊  

## Me
How do I create a dropdown list based on data already in my spreadsheet?  

## Co-Pilot
[1]: https://www.exceldemy.com/excel-drop-down-list-from-another-sheet/ ""
[2]: https://support.google.com/docs/answer/186103?hl=en&co=GENIE.Platform%3DDesktop ""
[3]: https://support.google.com/docs/answer/186103?hl=en-GB&co=GENIE.Platform%3DDesktop ""
[4]: https://www.spreadsheetclass.com/create-drop-down-list-in-google-sheets-data-validation-lesson/ ""
[5]: https://support.microsoft.com/en-us/office/create-a-drop-down-list-7693307a-59ef-400a-b769-c5402dce407b ""

Certainly! You can create a dropdown list in Excel or Google Sheets based on data already in your spreadsheet. Here's how:

### In Excel:
1. **Select the Cell Range:**
   - Choose the cell or range of cells where you want to create the dropdown list.

2. **Data Validation:**
   - Go to the **Data** tab.
   - Click on **Data Validation**.
   - In the **Settings** tab:
     - Set **Allow** to **List**.
     - Click on the source icon to select the data for your dropdown list.
     - Confirm your selection.
     - Click **OK**.

3. **Dropdown List Ready:**
   - Now, when you click on the cell, a dropdown arrow will appear, showing the available options from your data[^1^][1].

### In Google Sheets:
1. **Select the Cell Range:**
   - Choose the cell or cells with existing data.

2. **Data Validation:**
   - Right-click and select **Dropdown** (or **Drop-down** in some versions).
   - Make sure to check **Ignore Blank** and **In-Cell Dropdown**.

3. **Choose Data Source:**
   - Click on the source icon to select the data for your dropdown list.
   - Confirm your selection.

Now you have a dropdown list based on your existing data! Feel free to ask if you need further assistance 😊👍[^2^][2] [^3^][3] [^4^][4] [^5^][5].

Learn more: [1. www.exceldemy.com](https://www.exceldemy.com/excel-drop-down-list-from-another-sheet/) 
[2. support.google.com](https://support.google.com/docs/answer/186103?hl=en&co=GENIE.Platform%3DDesktop) 
[3. support.google.com](https://support.google.com/docs/answer/186103?hl=en-GB&co=GENIE.Platform%3DDesktop)
[4. www.spreadsheetclass.com](https://www.spreadsheetclass.com/create-drop-down-list-in-google-sheets-data-validation-lesson/)
[5. support.microsoft.com](https://support.microsoft.com/en-us/office/create-a-drop-down-list-7693307a-59ef-400a-b769-c5402dce407b)  

## Me
There is no data validation in the data tab, what dfo I do?  

## Co-Pilot
[1]: https://answers.microsoft.com/en-us/msoffice/forum/all/excel-office-365-no-data-validation-available-on/171f8713-609e-4e34-a511-2d99c42e41a6 ""
[2]: https://www.contextures.com/xldataval08.html ""
[3]: https://answers.microsoft.com/en-us/msoffice/forum/all/excel-office-365-data-validation-is-not-available/217b205c-396c-47ef-8bf2-e85e37acecf1 ""
[4]: https://www.excelforum.com/excel-general/609038-data-validation-drop-down-list-disappeared.html ""

I apologize for the inconvenience. If you're unable to find the data validation option in the Data tab, let's troubleshoot this:

1. **Check for Disabled Data Validation Button:**
   - Go to **File > Options > Customize Ribbon**.
   - Change to **All Commands**.
   - Look for the **Data Validation** button and add it to the ribbon[^1^][3].

2. **Update Office (Excel 365):**
   - Check for updates by going to **File > Account**.
   - Update your Office if any updates are available.
   - If already up-to-date, try using **Online Repair** to fix the issue.

3. **Verify Version and Build:**
   - Share a screenshot of the product information from **File > Account** (including Version and Build number).
   - Also, provide a screenshot of the Data tab ribbon.

Let's troubleshoot step by step, and we'll get this sorted out! 😊👍


Learn more: [1. answers.microsoft.com](https://answers.microsoft.com/en-us/msoffice/forum/all/excel-office-365-data-validation-is-not-available/217b205c-396c-47ef-8bf2-e85e37acecf1) 
[2. answers.microsoft.com](https://answers.microsoft.com/en-us/msoffice/forum/all/excel-office-365-no-data-validation-available-on/171f8713-609e-4e34-a511-2d99c42e41a6) 
[3. www.contextures.com](https://www.contextures.com/xldataval08.html) 
[4. www.excelforum.com](https://www.excelforum.com/excel-general/609038-data-validation-drop-down-list-disappeared.html)  

*End of this Conversation*
