# Excel: Retrieve "Meeting About" Based on Day and Week   

## Me
In excel I have a row with 3 columns, day, week and meeting about. Elsewheer on the spreadsheet I also have a grid with the rows being one of the options from Day (Monday, Tuesday, Wednesday, Thursday, Friday) and the columns being one of the options from Week (WC 15/7/24, WC 22/7/24, WC 29/7/24, WC 5/8/24, WC 12/8/24, WC 19/8/24, WC 26/8/24, WC 5/8/24, WC 2/9/24, WC 9/9/24, WC 16/9/24). I want to store the text that is in the meeting about column in teh cell in the grid that correspons to the day and week that is listed in that row also, how can I do it in excel using formulas?  

## Co-Pilot
[1]: https://exceljet.net/formulas/dynamic-calendar-grid ""
[2]: https://www.got-it.ai/solutions/excel-chat/excel-tutorial/date-and-time/dynamic-calendar-grid ""
[3]: https://www.exceldemy.com/excel-display-day-of-week-from-date/ ""
[4]: https://www.ablebits.com/office-addins-blog/excel-weekday-function/ ""

You can achieve this by using a combination of the `INDEX` and `MATCH` functions in Excel. Here's a step-by-step guide to help you set it up:

1. **Assume your data is structured as follows:**
   - **Day** in column A
   - **Week** in column B
   - **Meeting About** in column C

2. **Your grid is located elsewhere in the spreadsheet, with days as rows and weeks as columns.**

3. **Use the following formula in each cell of your grid to pull the corresponding "Meeting About" text:**

   ```excel
   =IFERROR(INDEX($C$2:$C$100, MATCH(1, ($A$2:$A$100=GridRowDay) * ($B$2:$B$100=GridColumnWeek), 0)), "")
   ```

   - Replace `$C$2:$C$100` with the range of your "Meeting About" column.
   - Replace `$A$2:$A$100` with the range of your "Day" column.
   - Replace `$B$2:$B$100` with the range of your "Week" column.
   - Replace `GridRowDay` with the cell reference of the day in your grid.
   - Replace `GridColumnWeek` with the cell reference of the week in your grid.

4. **Enter the formula in the first cell of your grid and drag it across the entire grid.**

Here's an example to illustrate:

- If your "Day" values are in cells `A2:A100`, "Week" values in `B2:B100`, and "Meeting About" values in `C2:C100`.
- Your grid starts at cell `E2` with days in column `E` and weeks in row `2`.

In cell `F3` (where `E3` is "Monday" and `F2` is "WC 15/7/24"), you would enter:

```excel
=IFERROR(INDEX($C$2:$C$100, MATCH(1, ($A$2:$A$100=$E3) * ($B$2:$B$100=F$2), 0)), "")
```

Then drag this formula across your grid.

This formula works by matching the day and week in your data to the corresponding cell in your grid and pulling the "Meeting About" text. The `IFERROR` function ensures that if there is no match, the cell remains blank.

Feel free to ask if you need further clarification or assistance! 😊

Learn more: [1. exceljet.net](https://exceljet.net/formulas/dynamic-calendar-grid) 
[2. www.got-it.ai](https://www.got-it.ai/solutions/excel-chat/excel-tutorial/date-and-time/dynamic-calendar-grid) 
[3. www.exceldemy.com](https://www.exceldemy.com/excel-display-day-of-week-from-date/) 
[4. www.ablebits.com](https://www.ablebits.com/office-addins-blog/excel-weekday-function/)  

## Me
How can I do it if each index can have multiple matches e.g. there are 2 rows with the same day and week but different meeting abouts, I still want to keep only one in the grid if there are multiple rows for the same meeting (i.e. with the same value in the meeting about column)  

## Co-Pilot
To handle multiple matches and ensure that only unique "Meeting About" values are stored in the grid, you can use a combination of `UNIQUE` and `TEXTJOIN` functions along with `FILTER`. Here's how you can do it:

1. **Assume your data is structured as follows:**
   - **Day** in column A
   - **Week** in column B
   - **Meeting About** in column C

2. **Your grid is located elsewhere in the spreadsheet, with days as rows and weeks as columns.**

3. **Use the following formula in each cell of your grid to pull the unique "Meeting About" text:**

   ```excel
   =IFERROR(TEXTJOIN(", ", TRUE, UNIQUE(FILTER($C$2:$C$100, ($A$2:$A$100=GridRowDay) * ($B$2:$B$100=GridColumnWeek)))), "")
   ```

   - Replace `$C$2:$C$100` with the range of your "Meeting About" column.
   - Replace `$A$2:$A$100` with the range of your "Day" column.
   - Replace `$B$2:$B$100` with the range of your "Week" column.
   - Replace `GridRowDay` with the cell reference of the day in your grid.
   - Replace `GridColumnWeek` with the cell reference of the week in your grid.

4. **Enter the formula in the first cell of your grid and drag it across the entire grid.**

Here's an example to illustrate:

- If your "Day" values are in cells `A2:A100`, "Week" values in `B2:B100`, and "Meeting About" values in `C2:C100`.
- Your grid starts at cell `E2` with days in column `E` and weeks in row `2`.

In cell `F3` (where `E3` is "Monday" and `F2` is "WC 15/7/24"), you would enter:

```excel
=IFERROR(TEXTJOIN(", ", TRUE, UNIQUE(FILTER($C$2:$C$100, ($A$2:$A$100=$E3) * ($B$2:$B$100=F$2)))), "")
```

Then drag this formula across your grid.

This formula works by:
1. **Filtering** the "Meeting About" values based on the matching day and week.
2. **Removing duplicates** using the `UNIQUE` function.
3. **Combining** the unique values into a single cell using `TEXTJOIN`.

This way, you ensure that only unique "Meeting About" values are displayed in your grid.

Let me know if you need any further assistance! 😊  

*End of this Conversation*
