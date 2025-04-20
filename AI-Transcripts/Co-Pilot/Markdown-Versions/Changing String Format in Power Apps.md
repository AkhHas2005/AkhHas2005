# Changing String Format in Power Apps

## Me
In power apps, how can I use string methods to change a string from "aa.bb" to "aa:bb"?

## Co-Pilot
[1]: https://math.stackexchange.com/questions/4101150/automaton-nfa-that-include-substring-aa-and-bb ""
[2]: https://stackoverflow.com/questions/15244501/got-string-aa-bb-cc-would-like-aa-bb-cc-could-i-do-it-smarter ""
[3]: https://www.matthewdevaney.com/power-apps-text-functions-with-examples/ ""
[4]: https://www.youtube.com/watch?v=LVW5MYwSx48 ""
[5]: https://youtu.be/hRW6GATxkpAString ""
[6]: https://youtu.be/QC6fx-bfEA0String ""

Certainly! To change the string "aa.bb" to "aa:bb" in Power Apps, you can use the `Replace` function. Here's how you can do it:

```PowerApps
Set modifiedString = Replace("aa.bb", ".", ":")
```

In this example, `modifiedString` will contain the value "aa:bb". The `Replace` function replaces all occurrences of the specified substring (in this case, the dot) with the replacement string (colon). Feel free to adapt this to your specific use case! 😊[^1^][2] [^2^][3]


Learn more: [1. stackoverflow.com](https://stackoverflow.com/questions/15244501/got-string-aa-bb-cc-would-like-aa-bb-cc-could-i-do-it-smarter) 
[2. www.matthewdevaney.com](https://www.matthewdevaney.com/power-apps-text-functions-with-examples/) 
[3. math.stackexchange.com](https://math.stackexchange.com/questions/4101150/automaton-nfa-that-include-substring-aa-and-bb) 
[4. www.youtube.com](https://www.youtube.com/watch?v=LVW5MYwSx48) 
[5. youtu.be](https://youtu.be/hRW6GATxkpAString) 
[6. youtu.be](https://youtu.be/QC6fx-bfEA0String)  

## Me
In power apps, how can I make it so that when I click a button, a new component appears underneath it?

## Co-Pilot
[1]: http://powerappsguide.com/blog/post/show-or-hide-controls-based-on-other-controls-or-on-a-button-click ""
[2]: https://www.matthewdevaney.com/power-apps-component-with-an-onselect-property/ ""
[3]: https://www.spguides.com/power-apps-button-onselect/ ""

Certainly! To achieve this in Power Apps, you can follow these steps:

1. **Create a Button:**
   - Open your screen and add a large button in the center with the text "Go to Screen 2."

2. **Set OnSelect Property:**
   - Add the following code to the `OnSelect` property of the button:
     ```PowerApps
     UpdateContext({locMoreVisible: true})
     ```

3. **Declare a Variable:**
   - Declare a variable called `locMoreVisible` with an initial value of `false` in the `OnVisible` property of the screen:
     ```PowerApps
     UpdateContext({locMoreVisible: false})
     ```

4. **Toggle Visibility:**
   - Set the `Visible` property of the component you want to show/hide (e.g., a section) to the `locMoreVisible` variable:
     ```PowerApps
     locMoreVisible
     ```

Now, when the user clicks the button, the hidden section will appear or disappear based on the value of the `locMoreVisible` variable. Adjust the component names and properties as needed for your specific scenario! 😊 [^1^][2]


Learn more: [1. www.matthewdevaney.com](https://www.matthewdevaney.com/power-apps-component-with-an-onselect-property/) 
[2. powerappsguide.com](http://powerappsguide.com/blog/post/show-or-hide-controls-based-on-other-controls-or-on-a-button-click) 
[3. www.spguides.com](https://www.spguides.com/power-apps-button-onselect/)

## Me
In power apps, how can I make it so that I keep adding components on the screen and sdo that when I reach the end of the screen, the screen extends and the user can scroll down?

## Co-Pilot
[1]: https://www.youtube.com/watch?v=0lNK9Bx4QKE ""
[2]: https://www.youtube.com/watch?v=MQGqHwZdUes ""
[3]: https://www.youtube.com/watch?v=t4ze8VnGuOk ""
[4]: https://www.matthewdevaney.com/easy-power-apps-scrollable-screen-using-a-vertical-container/ ""
[5]: https://www.matthewdevaney.com/power-apps-navigation-menu-component/ ""
[6]: https://www.richardawilson.com/2021/03/horizontally-scroll-large-power-apps.html ""

Certainly! To achieve this in Power Apps, you can follow these steps:

1. **Create a Scrollable Screen:**
   - Open Power Apps Studio and create a new tablet or canvas app.
   - Insert a vertical container at the top of the screen. You can add a label with the title (e.g., "Projects Backlog") above the container.
   - Set the vertical container's `VerticalOverflow` property to "Scroll." This makes the container scrollable.

2. **Add Components Dynamically:**
   - Inside the vertical container, add the components you want to display (e.g., labels, galleries, buttons).
   - As you add more components, the screen will automatically extend vertically, and users can scroll down to see all the content.

3. **Adjust Layout and Positioning:**
   - Arrange the components vertically within the container.
   - Use the `Y` property of each component to position them relative to each other.

4. **Test and Refine:**
   - Preview your app to ensure that the screen extends as you add more components.
   - Adjust the layout and styling as needed to achieve the desired look.

Remember to customize the components and layout based on your specific requirements. Happy app building! 😊 [^1^][4]


Learn more: [1. www.matthewdevaney.com](https://www.matthewdevaney.com/easy-power-apps-scrollable-screen-using-a-vertical-container/) 
[2. www.youtube.com](https://www.youtube.com/watch?v=0lNK9Bx4QKE) 
[3. www.youtube.com](https://www.youtube.com/watch?v=MQGqHwZdUes) 
[4. www.youtube.com](https://www.youtube.com/watch?v=t4ze8VnGuOk) 
[5. www.matthewdevaney.com](https://www.matthewdevaney.com/power-apps-navigation-menu-component/) 
[6. www.richardawilson.com](https://www.richardawilson.com/2021/03/horizontally-scroll-large-power-apps.html)  

## Me
In power apps, how can I add a component when a user selects a button and so that one of the text labels in the component contains teh name of the component (e.g. Day_3) formatted in a readable format (e.g. Day 3) and keep the new component name following the pattern Day_3, Day_4, Day_5 etc. where the number at the end is incremented each time a new component is created?

## Copilot
[1]: https://www.matthewdevaney.com/all-power-apps-date-time-functions-with-examples/ ""
[2]: https://learn.microsoft.com/en-us/power-apps/maker/canvas-apps/show-text-dates-times ""
[3]: https://learn.microsoft.com/en-us/power-platform/power-fx/reference/function-dateadd-datediff ""

Certainly! To achieve this in Power Apps, follow these steps:

1. **Create a Button:**
   - Add a button to your screen (e.g., "Add Component").
   - Set its `OnSelect` property to create a new component.

2. **Increment Component Name:**
   - Declare a variable (e.g., `componentCounter`) to keep track of the component number.
   - Initialize it to 3 (since you mentioned "Day_3" as the starting pattern).

3. **Add Component:**
   - In the button's `OnSelect` property, add the following code:
     ```PowerApps
     ClearCollect(MyComponents, { Name: "Day_" & Text(componentCounter, "[$-en-US]0") })
     UpdateContext({ componentCounter: componentCounter + 1 })
     ```

4. **Display Component Name:**
   - Create a label within your component.
   - Set its `Text` property to:
     ```PowerApps
     "Day " & Text(Value(Right(ThisItem.Name, Len(ThisItem.Name) - 4)), "[$-en-US]0")
     ```
   - This extracts the numeric part from the component name and formats it as "Day X."

5. **Repeat:**
   - Each time the button is clicked, a new component will be added with an incremented name (e.g., "Day_4," "Day_5," etc.).

Remember to adjust component names and styling as needed for your specific use case! 😊 [^1^][2] [^2^][3]


Learn more: [1. learn.microsoft.com](https://learn.microsoft.com/en-us/power-apps/maker/canvas-apps/show-text-dates-times) 
[2. learn.microsoft.com](https://learn.microsoft.com/en-us/power-platform/power-fx/reference/function-dateadd-datediff) 
[3. www.matthewdevaney.com](https://www.matthewdevaney.com/all-power-apps-date-time-functions-with-examples/)  

## Me
How can I get the name of the component in power apps, the statement "ThisItem.Name" doesn't work  

## Copilot
[1]: https://powerusers.microsoft.com/t5/Building-Power-Apps/ThisItem-Field-Name-doesnt-work-for-a-particularly-drop-down/td-p/1713686 ""
[2]: https://powerusers.microsoft.com/t5/Building-Power-Apps/quot-ThisItem-quot-operator-not-recognized-in-PowerApps-editor/td-p/762964 ""
[3]: https://www.enjoysharepoint.com/power-apps-set-thisitem-value/ ""
[4]: https://bing.com/search?q= ""
[5]: https://www.youtube.com/channel/UChmFBGU1YKIU91sNMQ7buGg ""
[6]: https://twitter.com/phipps0218 ""
[7]: https://powerusers.microsoft.com/t5/Building-Power-Apps/Patch-error-Name-isnt-Valid-ThisItem-is-not-recognized/td-p/2343839 ""
[8]: https://sharepoint.stackexchange.com/questions/301576/powerapps-thisitem-field-not-working-when-trying-to-use-sendemailv2 ""

Certainly! When working with Power Apps, the `ThisItem` object refers to the properties of the currently selected item, such as its ID or name, within formulas and expressions throughout your app. However, there are scenarios where `ThisItem.Name` might not work as expected. Let's troubleshoot:

1. **Gallery vs. Form:**
   - If you're using a gallery, `ThisItem.Name` should work as expected. However, in a form, you might encounter issues.
   - In a form, use `Parent.Default` to refer to the current item being edited. For example:
     ```PowerApps
     Patch('Data Source', { ID: Parent.Default.ID, 'impact comment': TextInput1.Text })
     ```

2. **Datacard Context:**
   - Ensure that the control (e.g., dropdown, text input) is placed inside a datacard.
   - Datacards have access to `Parent.Default`, allowing you to reference the current item's properties.

3. **Refresh Behavior:**
   - Sometimes, refreshing a datacard can cause issues. Make sure the datacard isn't set to refresh automatically.
   - If you're using a dropdown, check its `Items` property. It should be based on a valid data source.

4. **Check Field Names:**
   - Verify that the field name (e.g., `'impact comment'`) matches the actual field name in your data source.

Remember to adapt these suggestions based on your specific app structure and requirements. If you encounter any further issues, feel free to share more details, and we'll troubleshoot together! 😊 [^1^][7] [^2^][8]

Learn more: [1. powerusers.microsoft.com](https://powerusers.microsoft.com/t5/Building-Power-Apps/Patch-error-Name-isnt-Valid-ThisItem-is-not-recognized/td-p/2343839) 
[2. sharepoint.stackexchange.com](https://sharepoint.stackexchange.com/questions/301576/powerapps-thisitem-field-not-working-when-trying-to-use-sendemailv2) 
[3. powerusers.microsoft.com](https://powerusers.microsoft.com/t5/Building-Power-Apps/ThisItem-Field-Name-doesnt-work-for-a-particularly-drop-down/td-p/1713686) 
[4. powerusers.microsoft.com](https://powerusers.microsoft.com/t5/Building-Power-Apps/quot-ThisItem-quot-operator-not-recognized-in-PowerApps-editor/td-p/762964) 
[5. www.enjoysharepoint.com](https://www.enjoysharepoint.com/power-apps-set-thisitem-value/) 
[6. bing.com](https://bing.com/search?q=) 
[7. www.youtube.com](https://www.youtube.com/channel/UChmFBGU1YKIU91sNMQ7buGg) 
[8. twitter.com](https://twitter.com/phipps0218)  

*End of this Conversation*
