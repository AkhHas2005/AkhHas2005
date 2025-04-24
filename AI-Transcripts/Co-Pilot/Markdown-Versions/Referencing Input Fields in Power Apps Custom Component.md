# Referencing Input Fields in Power Apps Custom Component  

## Me
in power apps, I have a custom component that has multiple input fields inside of it. The names of the input fields are apparently: startTime1_9, endTime1_9, lunchStart1_9 and lunchEnd1_9. I'm using a button where I want the following code to set variables and perform calculations:  

    // Convert time values to date/time format  
    Set(convertedST, TimeValue(startTime1.Value));  
    Set(convertedET, TimeValue(endTime1.Value));  
    Set(convertedLS, TimeValue(lunchStart1.Value));  
    Set(convertedLE, TimeValue(lunchEnd1.Value));  

    // Calculate time differences  
    Set(mainDiffHours, DateDiff(convertedST, convertedET, TimeUnit.Hours));  
    Set(lunchDiffMinutes, DateDiff(convertedLS, convertedLE, TimeUnit.Minutes));  

    Set(  
      adjustedWorkHours,  
      mainDiffHours - (lunchDiffMinutes / 60)  
    );  

    Set(workHours, Int(adjustedWorkHours));  
    Set(workMinutes, (adjustedWorkHours - workHours) * 60);  
    Set(totalHours, totalHours + workHours);  
    Set(totalMinutes, totalMinutes + workMinutes);  

How can I make it so that the values set in teh first four variables are based on the values from the input fields taht are situated in teh custom component of whose names I have already mentioned. The custom component is called Day_11  

## Co-Pilot
[1]: https://www.youtube.com/watch?v=MQGqHwZdUes ""
[2]: https://www.youtube.com/watch?v=u_iRQYCrfpQ ""
[3]: https://learn.microsoft.com/en-us/power-apps/developer/component-framework/overview ""
[4]: https://learn.microsoft.com/en-us/power-apps/maker/canvas-apps/map-component-input-fields ""
[5]: https://www.matthewdevaney.com/make-your-first-power-apps-canvas-component/ ""
[6]: https://github.com/MicrosoftDocs/powerapps-docs/blob/main/powerapps-docs/maker/canvas-apps/map-component-input-fields.md ""

To ensure that the values from the input fields within your custom component `Day_11` are correctly referenced in your code, you need to access the properties of the component. Here's how you can modify your code to achieve this:

```powerapps
// Convert time values to date/time format
Set(convertedST, TimeValue(Day_11.startTime1_9.Value));
Set(convertedET, TimeValue(Day_11.endTime1_9.Value));
Set(convertedLS, TimeValue(Day_11.lunchStart1_9.Value));
Set(convertedLE, TimeValue(Day_11.lunchEnd1_9.Value));

// Calculate time differences
Set(mainDiffHours, DateDiff(convertedST, convertedET, TimeUnit.Hours));
Set(lunchDiffMinutes, DateDiff(convertedLS, convertedLE, TimeUnit.Minutes));

Set(
    adjustedWorkHours,
    mainDiffHours - (lunchDiffMinutes / 60)
);
Set(workHours, Int(adjustedWorkHours));
Set(workMinutes, (adjustedWorkHours - workHours) * 60);
Set(totalHours, totalHours + workHours);
Set(totalMinutes, totalMinutes + workMinutes);
```

In this updated code, I've prefixed each input field with `Day_11` to reference the custom component. This way, the values from the input fields within the `Day_11` component are used in your calculations.

Does this help with what you were trying to achieve? If you have any more questions or need further assistance, feel free to ask!

Learn more: [1. www.youtube.com](https://www.youtube.com/watch?v=MQGqHwZdUes) 
[2. www.youtube.com](https://www.youtube.com/watch?v=u_iRQYCrfpQ) 
[3. learn.microsoft.com](https://learn.microsoft.com/en-us/power-apps/developer/component-framework/overview) 
[4. learn.microsoft.com](https://learn.microsoft.com/en-us/power-apps/maker/canvas-apps/map-component-input-fields) 
[5. www.matthewdevaney.com](https://www.matthewdevaney.com/make-your-first-power-apps-canvas-component/) 
[6. github.com](https://github.com/MicrosoftDocs/powerapps-docs/blob/main/powerapps-docs/maker/canvas-apps/map-component-input-fields.md)  

## Me
When I write the syntax: Day_11.startTime1_9.Value, I get the following syntax errors: "Name isn't valid. 'startTime1_9' isn't recognized." and "The '.' operator cannot be used on Error values." How do I access the values of the input fields from within the custom component?  

## Co-Pilot
[1]: https://learn.microsoft.com/en-us/power-apps/maker/canvas-apps/map-component-input-fields ""
[2]: https://www.youtube.com/watch?v=j0V2KtujO9Q ""
[3]: https://github.com/MicrosoftDocs/powerapps-docs/blob/main/powerapps-docs/maker/canvas-apps/map-component-input-fields.md ""
[4]: https://learn.microsoft.com/en-us/power-apps/maker/canvas-apps/create-component ""

To access the values of input fields within a custom component in Power Apps, you need to use custom properties. Here's how you can set it up:

1. **Define Custom Properties in Your Component**:
   - Open your custom component (`Day_11`).
   - Add custom properties for each input field (e.g., `startTime1_9`, `endTime1_9`, `lunchStart1_9`, `lunchEnd1_9`).

2. **Set Up Custom Properties**:
   - For each custom property, set the **Property Type** to **Input** and the **Data Type** to **Text**.

3. **Bind the Input Fields to Custom Properties**:
   - In your component, bind the input fields to these custom properties. For example, set the `Default` property of `startTime1_9` to `Parent.startTime1_9`.

4. **Use the Custom Properties in Your App**:
   - When you use the component in your app, you can set these properties to the values of the input fields.

Here's an example of how you can modify your code:

```powerapps
// Convert time values to date/time format
Set(convertedST, TimeValue(Day_11.startTime1_9));
Set(convertedET, TimeValue(Day_11.endTime1_9));
Set(convertedLS, TimeValue(Day_11.lunchStart1_9));
Set(convertedLE, TimeValue(Day_11.lunchEnd1_9));

// Calculate time differences
Set(mainDiffHours, DateDiff(convertedST, convertedET, TimeUnit.Hours));
Set(lunchDiffMinutes, DateDiff(convertedLS, convertedLE, TimeUnit.Minutes));

Set(
    adjustedWorkHours,
    mainDiffHours - (lunchDiffMinutes / 60)
);
Set(workHours, Int(adjustedWorkHours));
Set(workMinutes, (adjustedWorkHours - workHours) * 60);
Set(totalHours, totalHours + workHours);
Set(totalMinutes, totalMinutes + workMinutes);
```

In this updated code, `Day_11.startTime1_9`, `Day_11.endTime1_9`, `Day_11.lunchStart1_9`, and `Day_11.lunchEnd1_9` are custom properties of the `Day_11` component.

If you need more detailed guidance on setting up custom properties, you can refer to the [Power Apps documentation on mapping component input fields](https://learn.microsoft.com/en-us/power-apps/maker/canvas-apps/map-component-input-fields)[^1^][1].

Does this help resolve the issue? If you have any more questions or need further assistance, feel free to ask!

Learn more: [1. learn.microsoft.com](https://learn.microsoft.com/en-us/power-apps/maker/canvas-apps/map-component-input-fields) 
[2. www.youtube.com](https://www.youtube.com/watch?v=j0V2KtujO9Q) 
[3. github.com](https://github.com/MicrosoftDocs/powerapps-docs/blob/main/powerapps-docs/maker/canvas-apps/map-component-input-fields.md) 
[4. learn.microsoft.com](https://learn.microsoft.com/en-us/power-apps/maker/canvas-apps/create-component)  

## Me
I tried this but I keep getting the following error when I click the button: "The value 'Text' cannot be converted to a date or time value" How can I fix this, my ocde is exactly as suggested before?  

## Co-Pilot
It sounds like the issue might be with the format of the text values being converted to date/time. Let's ensure that the text values are in a format that `TimeValue` can interpret correctly. Here are a few steps to troubleshoot and fix this issue:

1. **Check the Format of Input Values**:
   - Ensure that the input values are in a recognizable time format (e.g., "HH:MM AM/PM" or "HH:MM").

2. **Use `Text` Function to Format Input Values**:
   - Use the `Text` function to format the input values before converting them to time values.

Here's an updated version of your code with additional formatting:

```powerapps
// Convert time values to date/time format
Set(convertedST, TimeValue(Text(Day_11.startTime1_9, "[$-en-US]hh:mm AM/PM")));
Set(convertedET, TimeValue(Text(Day_11.endTime1_9, "[$-en-US]hh:mm AM/PM")));
Set(convertedLS, TimeValue(Text(Day_11.lunchStart1_9, "[$-en-US]hh:mm AM/PM")));
Set(convertedLE, TimeValue(Text(Day_11.lunchEnd1_9, "[$-en-US]hh:mm AM/PM")));

// Calculate time differences
Set(mainDiffHours, DateDiff(convertedST, convertedET, TimeUnit.Hours));
Set(lunchDiffMinutes, DateDiff(convertedLS, convertedLE, TimeUnit.Minutes));

Set(
    adjustedWorkHours,
    mainDiffHours - (lunchDiffMinutes / 60)
);
Set(workHours, Int(adjustedWorkHours));
Set(workMinutes, (adjustedWorkHours - workHours) * 60);
Set(totalHours, totalHours + workHours);
Set(totalMinutes, totalMinutes + workMinutes);
```

In this code, the `Text` function is used to ensure that the input values are formatted correctly before being converted to time values. The format "[$-en-US]hh:mm AM/PM" is used to specify the time format.

If the input values are in a different format, you can adjust the format string accordingly. 

Give this a try and let me know if it resolves the issue. If you still encounter problems, please share the exact format of the input values, and we can further refine the solution.  

*End of this Conversation*
