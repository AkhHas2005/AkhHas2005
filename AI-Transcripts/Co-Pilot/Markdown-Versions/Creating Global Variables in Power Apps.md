# Creating Global Variables in Power Apps  

## Me
In power apps, how can I create a global variable that stores a dynamic list of strings?  

## Co-Pilot
[1]: https://learn.microsoft.com/en-us/power-apps/maker/canvas-apps/working-with-variables ""
[2]: https://hkrtrainings.com/powerapps-variables ""
[3]: https://learn.microsoft.com/en-us/power-platform/power-fx/reference/function-concatenate ""
[4]: https://www.about365.nl/2020/01/29/using-variables-and-collections-in-power-apps/ ""
[5]: https://www.matthewdevaney.com/strings-a-better-way-to-concatenate-text-strings-in-power-apps/ ""

Certainly! In Power Apps, you can create a global variable to store a dynamic list of strings. Here's how:

1. **Global Variables**:
   - Global variables are accessible across all screens within a Power Apps app.
   - To create a global variable, use the `Set` function. For example:
     ```
     Set(global_variable, "Example")
     ```
   - Replace `"Example"` with your desired string value.

2. **$-String Syntax (Optional)**:
   - If you want to concatenate text strings, consider using the new `$-String` syntax.
   - Place a dollar sign (`$`) in front of the text string's quotation marks and use curly braces (`{}`) for expressions (functions, formulas, or variables) that might change[^1^][5].

Remember to adapt these steps to your specific use case! 😊

Learn more: [1. www.matthewdevaney.com](https://www.matthewdevaney.com/strings-a-better-way-to-concatenate-text-strings-in-power-apps/) 
[2. learn.microsoft.com](https://learn.microsoft.com/en-us/power-apps/maker/canvas-apps/working-with-variables) 
[3. hkrtrainings.com](https://hkrtrainings.com/powerapps-variables) 
[4. learn.microsoft.com](https://learn.microsoft.com/en-us/power-platform/power-fx/reference/function-concatenate) 
[5. www.about365.nl](https://www.about365.nl/2020/01/29/using-variables-and-collections-in-power-apps/)  

## Me
How do I store an array or list in power apps?  

## Co-Pilot
[1]: https://debajmecrm.com/how-to-get-an-item-from-an-array-collection-or-table-by-index-in-power-apps-canvas-app/ ""
[2]: https://www.spguides.com/powerapps-collection/ ""
[3]: https://www.arrayasolutions.com/insights/blog/2021/step-by-step-sharepoint-list-data-management-with-power-apps/ ""
[4]: https://www.about365.nl/2020/01/29/using-variables-and-collections-in-power-apps/ ""
[5]: https://www.youtube.com/watch?v=eRCnuCxqGk0 ""
[6]: https://learn.microsoft.com/en-us/power-apps/maker/canvas-apps/working-with-variables ""
[7]: https://hkrtrainings.com/powerapps-variables ""
[8]: https://learn.microsoft.com/en-us/power-platform/power-fx/reference/function-concatenate ""
[9]: https://www.matthewdevaney.com/strings-a-better-way-to-concatenate-text-strings-in-power-apps/ ""
[10]: https://bing.com/search?q=Power+Apps+store+array+list ""
[11]: https://www.dmcinfo.com/latest-thinking/blog/id/10544/the-ultimate-guide-to-using-arrays-in-power-automate ""

Certainly! In Power Apps, you can create a **global variable** to store an array or list. Additionally, you can use **collections** to temporarily store data within your app. Let me explain both approaches:

1. **Global Variables**:
   - **Global variables** are accessible across all screens within a Power Apps app.
   - To create a global variable, use the `Set` function. For example:
     ```
     Set(global_variable, ["Item1", "Item2", "Item3"])
     ```
     Replace `["Item1", "Item2", "Item3"]` with your desired list of strings.

2. **Collections**:
   - A **collection** is a group of items or an array that helps store data in Power Apps memory.
   - You can create a collection using the `Collect` function. For instance:
     ```
     Collect(MyCollection, { Name: "John", Age: 30 }, { Name: "Alice", Age: 25 })
     ```
     Replace `{ Name: "John", Age: 30 }, { Name: "Alice", Age: 25 }` with your data records.

Remember to adapt these methods based on your specific use case! 😊[^1^][2] [^2^][7]

Learn more: [1. www.spguides.com](https://www.spguides.com/powerapps-collection/) 
[2. hkrtrainings.com](https://hkrtrainings.com/powerapps-variables) 
[3. debajmecrm.com](https://debajmecrm.com/how-to-get-an-item-from-an-array-collection-or-table-by-index-in-power-apps-canvas-app/) 
[4. www.arrayasolutions.com](https://www.arrayasolutions.com/insights/blog/2021/step-by-step-sharepoint-list-data-management-with-power-apps/) 
[5. www.about365.nl](https://www.about365.nl/2020/01/29/using-variables-and-collections-in-power-apps/) 
[6. www.youtube.com](https://www.youtube.com/watch?v=eRCnuCxqGk0) 
[7. learn.microsoft.com](https://learn.microsoft.com/en-us/power-apps/maker/canvas-apps/working-with-variables) 
[8. learn.microsoft.com](https://learn.microsoft.com/en-us/power-platform/power-fx/reference/function-concatenate) 
[9. www.matthewdevaney.com](https://www.matthewdevaney.com/strings-a-better-way-to-concatenate-text-strings-in-power-apps/) 
[10. bing.com](https://bing.com/search?q=Power+Apps+store+array+list) 
[11. www.dmcinfo.com](https://www.dmcinfo.com/latest-thinking/blog/id/10544/the-ultimate-guide-to-using-arrays-in-power-automate)  

## Me
How do I add or remove from a collection when a button is clicked?  

## Co-Pilot
[1]: https://www.spguides.com/add-item-to-collection-powerapps/ ""
[2]: https://powerusers.microsoft.com/t5/Building-Power-Apps/Issue-to-add-remove-item-to-collection-with-button/td-p/1908276 ""
[3]: https://blog.mydock365.com/a-basic-guide-to-creating-and-using-collections-in-powerapps ""
[4]: https://sharepoint.stackexchange.com/questions/293411/how-to-change-the-combo-box-selected-value-on-button-click-in-power-apps ""
[5]: https://www.spguides.com/powerapps-collection/ ""
[6]: https://bing.com/search?q=Power+Apps+store+array+list ""
[7]: https://www.arrayasolutions.com/insights/blog/2021/step-by-step-sharepoint-list-data-management-with-power-apps/ ""
[8]: https://www.dmcinfo.com/latest-thinking/blog/id/10544/the-ultimate-guide-to-using-arrays-in-power-automate ""
[9]: https://learn.microsoft.com/en-us/power-apps/maker/canvas-apps/working-with-variables ""
[10]: https://hkrtrainings.com/powerapps-variables ""
[11]: https://learn.microsoft.com/en-us/power-platform/power-fx/reference/function-concatenate ""
[12]: https://www.about365.nl/2020/01/29/using-variables-and-collections-in-power-apps/ ""
[13]: https://www.matthewdevaney.com/strings-a-better-way-to-concatenate-text-strings-in-power-apps/ ""

Certainly! To add or remove items from a collection in Power Apps when a button is clicked, follow these steps:

1. **Create a Collection**:
   - First, create a collection to store your data. You can do this in the app's **OnStart** property using the `Collect` function. For example:
     ```PowerApps
     OnStart = Collect(MyCollection, { Name: "John", Age: 30 }, { Name: "Alice", Age: 25 })
     ```
     Replace the sample data with your own records.

2. **Add Items to the Collection**:
   - To add items when a button is clicked, use the `Collect` function again. For instance:
     ```PowerApps
     OnSelect (ButtonAdd) = Collect(MyCollection, { Name: "NewPerson", Age: 40 })
     ```
     This adds a new record to the collection.

3. **Remove Items from the Collection**:
   - To remove an item when a button is clicked, use the `Remove` function. For example:
     ```PowerApps
     OnSelect (ButtonRemove) = Remove(MyCollection, { Name: "Alice" })
     ```
     This removes the record with the specified criteria (in this case, the person named "Alice").

Remember to adjust the collection name and field names according to your specific scenario! 😊[^1^][5] [^2^][7]

Learn more: [1. www.spguides.com](https://www.spguides.com/powerapps-collection/) 
[2. www.arrayasolutions.com](https://www.arrayasolutions.com/insights/blog/2021/step-by-step-sharepoint-list-data-management-with-power-apps/) 
[3. www.spguides.com](https://www.spguides.com/add-item-to-collection-powerapps/) 
[4. powerusers.microsoft.com](https://powerusers.microsoft.com/t5/Building-Power-Apps/Issue-to-add-remove-item-to-collection-with-button/td-p/1908276) 
[5. blog.mydock365.com](https://blog.mydock365.com/a-basic-guide-to-creating-and-using-collections-in-powerapps) 
[6. sharepoint.stackexchange.com](https://sharepoint.stackexchange.com/questions/293411/how-to-change-the-combo-box-selected-value-on-button-click-in-power-apps) 
[7. bing.com](https://bing.com/search?q=Power+Apps+store+array+list) 
[8. www.dmcinfo.com](https://www.dmcinfo.com/latest-thinking/blog/id/10544/the-ultimate-guide-to-using-arrays-in-power-automate) 
[9. learn.microsoft.com](https://learn.microsoft.com/en-us/power-apps/maker/canvas-apps/working-with-variables) 
[10. hkrtrainings.com](https://hkrtrainings.com/powerapps-variables) 
[11. learn.microsoft.com](https://learn.microsoft.com/en-us/power-platform/power-fx/reference/function-concatenate) 
[12. www.about365.nl](https://www.about365.nl/2020/01/29/using-variables-and-collections-in-power-apps/) 
[13. www.matthewdevaney.com](https://www.matthewdevaney.com/strings-a-better-way-to-concatenate-text-strings-in-power-apps/)  

## Me
How can I etrieve the last string in a collectiomn in power apps?  

## Co-Pilot
[1]: https://learn.microsoft.com/en-us/power-platform/power-fx/reference/function-first-last ""
[2]: http://powerappsguide.com/blog/post/how-to-return-the-last-record-from-a-table ""
[3]: https://www.spguides.com/get-last-item-id-in-sharepoint-list-based-on-current-user-in-power-apps/ ""
[4]: https://www.matthewdevaney.com/powerapps-collections-cookbook/get-the-last-rows-of-a-collection/ ""

To retrieve the last record from a collection in Power Apps, you can use the `Last` function. Here's how:

1. **Create a Collection**:
   - First, create a collection to store your data. For example, you can use this formula in the **OnStart** property of a button:
     ```PowerApps
     OnStart = Collect(MyCollection, { Flavor: "Chocolate" }, { Flavor: "Vanilla" }, { Flavor: "Strawberry" })
     ```
     Replace the sample data with your own records.

2. **Retrieve the Last Record**:
   - To get the last record from the collection, use the `Last` function:
     ```PowerApps
     Last(MyCollection)
     ```
     This will return the last record (in this case, the flavor "Strawberry").

Remember to adapt the collection name and field names according to your specific scenario! 😊 [^1^][1] [^2^][2]

Learn more: [1. learn.microsoft.com](https://learn.microsoft.com/en-us/power-platform/power-fx/reference/function-first-last) 
[2. powerappsguide.com](http://powerappsguide.com/blog/post/how-to-return-the-last-record-from-a-table) 
[3. www.spguides.com](https://www.spguides.com/get-last-item-id-in-sharepoint-list-based-on-current-user-in-power-apps/) 
[4. www.matthewdevaney.com](https://www.matthewdevaney.com/powerapps-collections-cookbook/get-the-last-rows-of-a-collection/)  

*End of this Conversation*
