# Creating Dynamic Dependent Drop-Downs in Excel  

## Me
In excel, how can I choose a drop-down based on a dynamically changing list?  

## Co-Pilot
[1]: https://www.youtube.com/watch?v=boQ5p8r63yg ""
[2]: https://www.youtube.com/watch?v=4wr-ns5vvpM ""
[3]: https://trumpexcel.com/excel-drop-down-list/ ""
[4]: https://www.ablebits.com/office-addins-blog/create-dynamic-dependent-drop-down-excel/ ""
[5]: https://www.ablebits.com/office-addins-blog/excel-drop-down-list/ ""
[6]: https://spreadsheetpoint.com/excel/drop-down-list/ ""
[7]: https://www.xelplus.com/excel-dynamic-chart-with-drop-down/ ""
[8]: https://www.youtube.com/watch?v=vh2jdOQ5VLs ""
[9]: https://www.youtube.com/watch?v=v6eT4JlKbS4 ""
[10]: https://www.youtube.com/watch?v=daCvyt9E8s4 ""
[11]: https://www.exceldemy.com/learn-excel/data-validation/drop-down-list/dependent/ ""
[12]: https://www.extendoffice.com/documents/excel/7317-excel-dependent-drop-down-list.html ""

Certainly! To create a dynamic dependent drop-down list in Excel, you can use the new dynamic array functions available in Excel 365 and Excel 2021. Here's how:

1. **Get items for the main drop-down list**:
   - Suppose you have a list of fruit names in column A. Use the `UNIQUE` function to extract unique fruit names from column A. For example:
     ```
     =UNIQUE(A3:A15)
     ```
   - This formula goes into cell G3, and the results will spill into subsequent cells automatically.

2. **Create the main drop-down**:
   - Select a cell where you want the primary drop-down to appear (e.g., D3).
   - Go to the **Data** tab, click **Data Validation** in the **Data Tools** group.
   - In the **Data Validation** dialog box:
     - Under **Allow**, select **List**.
     - In the **Source** box, enter the reference to the spill range output by the `UNIQUE` formula[^1^][4].

Now, when you select a fruit from the main drop-down, the dependent drop-down will show relevant exporters based on your selection. Remember that this dynamic array approach works only in Excel 365 and Excel 2021. For older versions, you'll need to follow a different method[^1^][4]. Let me know if you need further assistance! 😊

Learn more: [1. www.ablebits.com](https://www.ablebits.com/office-addins-blog/create-dynamic-dependent-drop-down-excel/) 
[2. www.youtube.com](https://www.youtube.com/watch?v=boQ5p8r63yg) 
[3. www.youtube.com](https://www.youtube.com/watch?v=4wr-ns5vvpM) 
[4. trumpexcel.com](https://trumpexcel.com/excel-drop-down-list/) 
[5. www.ablebits.com](https://www.ablebits.com/office-addins-blog/excel-drop-down-list/) 
[6. spreadsheetpoint.com](https://spreadsheetpoint.com/excel/drop-down-list/) 
[7. www.xelplus.com](https://www.xelplus.com/excel-dynamic-chart-with-drop-down/) 
[8. www.youtube.com](https://www.youtube.com/watch?v=vh2jdOQ5VLs) 
[9. www.youtube.com](https://www.youtube.com/watch?v=v6eT4JlKbS4) 
[10. www.youtube.com](https://www.youtube.com/watch?v=daCvyt9E8s4) 
[11. www.exceldemy.com](https://www.exceldemy.com/learn-excel/data-validation/drop-down-list/dependent/) 
[12. www.extendoffice.com](https://www.extendoffice.com/documents/excel/7317-excel-dependent-drop-down-list.html)  

## Me
How can I format text across multiple lines in one cell?  

## Co-Pilot
[1]: https://www.youtube.com/watch?v=ySf8ERtH2kU ""
[2]: https://www.youtube.com/watch?v=kiqkCRELrls ""
[3]: https://www.youtube.com/watch?v=9lyDuDUJRzM ""
[4]: https://www.exceldemy.com/how-to-make-two-lines-in-one-cell-in-excel/ ""
[5]: https://www.extendoffice.com/documents/excel/3614-excel-text-on-multiple-lines-in-one-cell.html ""
[6]: https://learnexcel.io/type-multiple-lines-cell-excel/ ""
[7]: https://www.exceldemy.com/excel-wrap-text-across-multiple-cells-without-merging/ ""

Certainly! You can format text across multiple lines in a single cell in Excel using the following methods:

1. **Insert Line Breaks**:
   - Select the cell where you want to create multiple lines (e.g., Cell B5).
   - In the formula bar, type your text and press `Alt + Enter` to add a line break within the same cell.
   - Adjust the cell height by double-clicking the bottom bar of the corresponding row number to ensure both lines are visible[^1^][4].

2. **Wrap Text**:
   - Select the cell (e.g., Cell B6).
   - Go to the **Home** tab and click **Wrap Text** in the **Alignment** group.
   - This will display the content on two lines within the cell[^2^][5].

3. **Create a Line Break After a Specific Character**:
   - Insert a comma (", ") after the first part of your text (e.g., "John, Class 5").
   - Press `Ctrl + H` to open the **Find and Replace** window.
   - In the **Find what** box, enter a comma (", ").
   - In the **Replace with** box, press `Ctrl + J` to represent a line break.
   - Click **Replace All** and adjust the row height as needed[^1^][4].

4. **Merge & Center** (for two lines only):
   - Type your text in two adjacent cells (e.g., A1 and B1).
   - Select both cells, right-click, and choose **Format Cells**.
   - In the **Alignment** tab, select **Merge cells** and **Center across selection**.
   - This will create two lines within a single cell[^1^][4].

Feel free to choose the method that best suits your needs! 😊

Learn more: [1. www.exceldemy.com](https://www.exceldemy.com/how-to-make-two-lines-in-one-cell-in-excel/) 
[2. www.extendoffice.com](https://www.extendoffice.com/documents/excel/3614-excel-text-on-multiple-lines-in-one-cell.html) 
[3. www.youtube.com](https://www.youtube.com/watch?v=ySf8ERtH2kU) 
[4. www.youtube.com](https://www.youtube.com/watch?v=kiqkCRELrls) 
[5. www.youtube.com](https://www.youtube.com/watch?v=9lyDuDUJRzM) 
[6. learnexcel.io](https://learnexcel.io/type-multiple-lines-cell-excel/)
[7. www.exceldemy.com](https://www.exceldemy.com/excel-wrap-text-across-multiple-cells-without-merging/)  

*End of this Conversation*
