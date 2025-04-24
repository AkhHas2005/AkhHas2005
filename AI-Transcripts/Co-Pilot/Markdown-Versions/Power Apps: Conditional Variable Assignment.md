# Power Apps: Conditional Variable Assignment  

## Me
how can I write an if statement for a formula in power apps: I want the formula to set a variable called hours to Textbox2.value if the selected item in ComboBox1 is per day and if it's per week divide this value by 5?  

## Co-Pilot
[1]: https://www.youtube.com/watch?v=9aXP48XECDc ""
[2]: https://www.youtube.com/watch?v=H1ib-qbAuXQ ""
[3]: https://www.youtube.com/watch?v=HQ4RNJiVurI ""
[4]: https://www.matthewdevaney.com/25-power-apps-if-function-examples/ ""
[5]: https://zeitgeistcode.com/powerapps-if-statements/ ""
[6]: https://www.spguides.com/powerapps-if-statement/ ""
[7]: https://www.spguides.com/power-automate-if/ ""
[8]: https://www.youtube.com/watch?v=8pYbbqv-Hl0 ""
[9]: https://manueltgomes.com/reference/powerapps-function-reference/powerapps-if-function/ ""
[10]: https://powerusers.microsoft.com/t5/Building-Power-Apps/What-is-the-syntax-for-writing-an-IF-statement-for-the-quot/td-p/368639 ""

Certainly! In Power Apps, you can use the `If` function to create conditional statements. Let's break down your requirement:

1. If the selected item in `ComboBox1` is "per day," set the `hours` variable to `Textbox2.Value`.
2. If the selected item in `ComboBox1` is "per week," divide `Textbox2.Value` by 5.

Here's how you can write this in Power Apps:

```PowerApps
Set(hours,
    If(ComboBox1.Selected.Value = "per day",
        Textbox2.Value,
        Textbox2.Value / 5
    )
)
```

Explanation:
- The `If` function checks the condition (whether the selected item is "per day").
- If true, it assigns `Textbox2.Value` to the `hours` variable.
- If false (i.e., "per week"), it divides `Textbox2.Value` by 5.

Feel free to adjust the field names and values according to your specific app setup! 😊

For more examples and details, you can refer to [this tutorial](https://www.matthewdevaney.com/25-power-apps-if-function-examples/)[^1^][4].[^2^][1]


Learn more: [1. www.matthewdevaney.com](https://www.matthewdevaney.com/25-power-apps-if-function-examples/) 
[2. www.youtube.com](https://www.youtube.com/watch?v=9aXP48XECDc) 
[3. www.youtube.com](https://www.youtube.com/watch?v=H1ib-qbAuXQ) 
[4. www.youtube.com](https://www.youtube.com/watch?v=HQ4RNJiVurI) 
[5. zeitgeistcode.com](https://zeitgeistcode.com/powerapps-if-statements/) 
[6. www.spguides.com](https://www.spguides.com/powerapps-if-statement/) 
[7. www.spguides.com](https://www.spguides.com/power-automate-if/) 
[8. www.youtube.com](https://www.youtube.com/watch?v=8pYbbqv-Hl0) 
[9. manueltgomes.com](https://manueltgomes.com/reference/powerapps-function-reference/powerapps-if-function/) 
[10. powerusers.microsoft.com](https://powerusers.microsoft.com/t5/Building-Power-Apps/What-is-the-syntax-for-writing-an-IF-statement-for-the-quot/td-p/368639)  

## Me
How can I declare/assign a new variable called hours?  

## Co-Pilot
Certainly! To declare and assign a new variable called `hours` in Power Apps, you can use the `Set` function. Here's how you can do it:

```PowerApps
Set(hours, 0)  // Initialize the variable with a default value (e.g., 0)
```

Replace `0` with the appropriate initial value if needed. Now you can use the `hours` variable in your app! 😊  

*End of this Conversation*
