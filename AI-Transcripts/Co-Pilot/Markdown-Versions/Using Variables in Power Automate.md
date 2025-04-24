# Using Variables in Power Automate  

## Me
In power automate, how can I assign variables to store an input from a text box in my app?  

## Co-Pilot
[1]: https://learn.microsoft.com/en-us/power-automate/create-variable-store-values ""
[2]: https://learn.microsoft.com/en-us/power-automate/desktop-flows/manage-variables ""
[3]: https://www.enjoysharepoint.com/how-to-get-value-from-text-input-in-power-apps/ ""
[4]: https://www.enjoysharepoint.com/power-automate-set-variable/ ""
[5]: https://powerusers.microsoft.com/t5/Building-Power-Apps/Setting-a-Text-Box-to-a-Variable-Value/td-p/120940 ""

Certainly! In Power Automate, you can create and work with variables to store values. Here's how you can assign a variable to store an input from a text box in your app:

1. **Initialize a Variable**:
   - Sign in to Power Automate.
   - Create or open a cloud flow.
   - Add an action where you want to add a variable.
   - Search for "Initialize variable" and select it.
   - Provide the variable name and choose its data type (e.g., string).
   - Set the initial value for the variable[^1^][1].

2. **Get Value from Text Input in Power Apps**:
   - Add a button control to your Power Apps screen.
   - Set the button's `OnSelect` property with the following expression:
     ```
     OnSelect = Patch(ColName, Defaults(ColName), {UserName: UserName_txtInput.Text});
     Reset(UserName_txtInput)
     ```
     Replace `ColName` with your collection name and `UserName_txtInput` with your text input control[^2^][3].

3. **Set a Text Box to a Variable Value**:
   - You can use a variable to control the state of a text box.
   - For example, set the `Reset` property of the text input control to a variable:
     ```
     Set(varReset, true);
     Set(varReset, false);
     ```
     Alternatively, use a button with the `OnSelect` property:
     ```
     UpdateContext({Variable1: true});
     UpdateContext({Variable1: false});
     ```
     Modify the `Reset` property of the text input control to use `Variable1`[^3^][5].

Remember that variables exist globally within the cloud flow and persist across loop iterations. Feel free to adapt these steps to your specific scenario! 😊


Learn more: [1. learn.microsoft.com](https://learn.microsoft.com/en-us/power-automate/create-variable-store-values) 
[2. www.enjoysharepoint.com](https://www.enjoysharepoint.com/how-to-get-value-from-text-input-in-power-apps/) 
[3. powerusers.microsoft.com](https://powerusers.microsoft.com/t5/Building-Power-Apps/Setting-a-Text-Box-to-a-Variable-Value/td-p/120940) 
[4. learn.microsoft.com](https://learn.microsoft.com/en-us/power-automate/desktop-flows/manage-variables) 
[5. www.enjoysharepoint.com](https://www.enjoysharepoint.com/power-automate-set-variable/)  

## Me
How can I create a collection in power apps (August 2024)?  

## Co-Pilot
[1]: https://learn.microsoft.com/en-us/power-apps/maker/canvas-apps/create-update-collection ""
[2]: https://www.spguides.com/powerapps-collection/ ""
[3]: https://www.matthewdevaney.com/powerapps-collections-cookbook/create-a-collection-from-datasource/ ""

Certainly! To create a collection in Power Apps, follow these steps:

1. **Initialize a Collection**:
   - Open your app in Power Apps.
   - In the left navigation pane, select the App object.
   - Set its `OnStart` property to the following code:
     ```
     OnStart = Collect(MyCollection, { BookName: "The Testaments", Author: "Margaret Atwood" })
     ```
   - Save and publish the app.

2. **Verify the Collection**:
   - Now, the collection named `MyCollection` has been created.
   - You can access it with all the records you added.

Remember to replace the book details in the example with your own data! 😊 [^1^][2]


Learn more: [1. www.spguides.com](https://www.spguides.com/powerapps-collection/) 
[2. learn.microsoft.com](https://learn.microsoft.com/en-us/power-apps/maker/canvas-apps/create-update-collection) 
[3. www.matthewdevaney.com](https://www.matthewdevaney.com/powerapps-collections-cookbook/create-a-collection-from-datasource/)  

## Me
It won't work, the collection is empty when I use that code  

## Co-Pilot
I apologize for the oversight. Let's troubleshoot this together. Here are some steps to ensure your collection is initialized correctly:

1. **Check Collection Name**:
   - Confirm that the collection name you're using (`MyCollection`) matches the one in your app.
   - Make sure there are no typos or discrepancies.

2. **Verify the `OnStart` Property**:
   - Go to the App object in the left navigation pane.
   - Double-check the `OnStart` property. It should be set to:
     ```
     OnStart = Collect(MyCollection, { BookName: "The Testaments", Author: "Margaret Atwood" })
     ```
   - Save your changes.

3. **Test the Collection**:
   - Run your app (you can preview it in the Power Apps Studio).
   - Check if the collection contains the record with the book details.
   - If not, try creating a new collection with a different name and test again.

Remember to replace the book details in the example with your own data. If you encounter any issues, feel free to ask for further assistance! 😊  

## Me
How can I concatenate a string with a variable taken from an inputbox in power apps? (Friday, Aug 2 now)  

## Co-Pilot
[1]: https://www.matthewdevaney.com/strings-a-better-way-to-concatenate-text-strings-in-power-apps/ ""
[2]: https://softwarezone365.com/power-apps-text-concatenation-guide ""
[3]: https://devpixi.com/powerapps-examples/powerapps-string-examples-including-replace-and-concatenate/ ""

Certainly! In Power Apps, you have a few options for concatenating strings with variables or input values:

1. **Using $-Strings (String Interpolation)**:
   - The new $-String syntax allows you to easily concatenate text strings with expressions (functions, formulas, or variables) inside curly braces.
   - Example:
     ```
     $\"Hello {User().FullName}. The current date is {Today()}.\"
     ```
     This will display a message with the user's name and the current date[^1^][1].

2. **Using the & Operator**:
   - You can join text strings using the & operator.
   - Example:
     ```
     \"Hello my name is\" & User().FullName & \". The current date is\" & Today() & \".\"
     ```
     This approach is more readable during code review but requires extra typing[^1^][1].

3. **Using the Concatenate Function**:
   - If you prefer a function-based approach, use the Concatenate function.
   - Example:
     ```
     Concatenate(\"Hello my name is\", User().FullName, \". The current date is\", Today(), \".\")
     ```
     Each section of text or expression is supplied as a separate argument[^2^][3].

Choose the method that best suits your preference and readability! 😊


Learn more: [1. www.matthewdevaney.com](https://www.matthewdevaney.com/strings-a-better-way-to-concatenate-text-strings-in-power-apps/) 
[2. devpixi.com](https://devpixi.com/powerapps-examples/powerapps-string-examples-including-replace-and-concatenate/)
[3. softwarezone365.com](https://softwarezone365.com/power-apps-text-concatenation-guide)  

## Me
How can I concatenate a string ("Your work hours per day are: ") with a variable taken from an inputbox (TextBox2.Value) in power apps?  

## Co-Pilot
Certainly! To concatenate a string with a variable from an input box in Power Apps, follow these steps:

1. **Create a Label or Text Control**:
   - Add a label or text control to your screen where you want to display the concatenated result.

2. **Set the Text Property**:
   - Select the label or text control.
   - In the Properties pane, find the `Text` property.
   - Set the property to the following formula:
     ```
     "Your work hours per day are: " & TextBox2.Text
     ```
     Replace `TextBox2` with the actual name of your input box control.

3. **Test Your App**:
   - Run your app to see the concatenated result in the label or text control.

This will display the combined string with the value from the input box. 😊  

*End of this Conversation*
