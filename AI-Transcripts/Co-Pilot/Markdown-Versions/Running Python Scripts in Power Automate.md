# Running Python Scripts in Power Automate  

## Me
I'm trying to run a python script through a power automate flow, however, all the apps that can run python are premium, how can I run the python code for free or adapt it so it can run using the free apps?  

## Co-Pilot
[1]: https://www.process.st/how-to/run-python-script-in-power-automate/ ""
[2]: https://stackoverflow.com/questions/46718344/is-it-possible-to-automate-the-execution-of-a-python-script-using-microsoft-flow ""
[3]: https://powerusers.microsoft.com/t5/General-Power-Automate/Execute-python-script-from-Power-Automate-Flow/td-p/550328 ""
[4]: https://stackoverflow.com/questions/77751515/running-python-scripts-in-microsoft-power-automate-cloud ""

Running a Python script in Power Automate can be quite useful for automating tasks and integrating with other systems. While some premium apps support Python execution, there are ways to achieve this without additional costs. Here are a couple of approaches:

1. **Azure Functions**:
   - Create an Azure Function using Python as the language.
   - Define an API using this function.
   - Export the API definition to Power Automate.
   - Add the function to your app as a data source or directly to your flow[^1^][2].

2. **Local Execution with PowerShell**:
   - Store the path to your Python script in a variable (let's call it "x").
   - Use the "Run PowerShell Script" action in Power Automate.
   - Inside the action, type: `python %x%`[^2^][3].

Remember that the online browser version of Power Automate doesn't have a Python script connector. If you prefer cloud-based execution, consider running your Python script in an Azure Automation account or an Azure Function and then call it from your Power Automate flow[^3^][4]. Happy automating! 🐍✨

Learn more: [1. stackoverflow.com](https://stackoverflow.com/questions/46718344/is-it-possible-to-automate-the-execution-of-a-python-script-using-microsoft-flow) 
[2. powerusers.microsoft.com](https://powerusers.microsoft.com/t5/General-Power-Automate/Execute-python-script-from-Power-Automate-Flow/td-p/550328) 
[3. stackoverflow.com](https://stackoverflow.com/questions/77751515/running-python-scripts-in-microsoft-power-automate-cloud) 
[4. www.process.st](https://www.process.st/how-to/run-python-script-in-power-automate/)  

*End of this Conversation*
