## Me
I have this python code:  

```Python
import re

data_table = []
temp_statement = input("Enter a template SQL statement: ")
data = " "
while data != "":
    data = input("Enter a data row (Enter to finish): ")
    data_row = data.split()
    data_table.append(data_row)

if temp_statement.startswith("INSERT"):
    start_index = temp_statement.rfind("VALUES (")
    for num in range(int(temp_statement.count(",")/2)):
        pattern = r'.{' + str(start_index) + r'}([^,]*)'
        match = re.search(pattern, temp_statement)
        temp_statement.replace(match, data_table[0][num])
        start_index = temp_statement.rfind(match)
    print(temp_statement)
else:
    print("Not found")
```

How can I fix this error:  
```
Traceback (most recent call last):
  File "C:/Users/hakhta26/OneDrive - University of Bradford/Documents/Python_Files/SQl statement gen.py", line 17, in 
    temp_statement.replace(match, data_table[0][num])
TypeError: replace() argument 1 must be str, not re.Match
```  

## Copilot
The error you're encountering is because the replace() method expects a string as its first argument, but you're passing an re.Match object instead. To fix this, you need to extract the matched string from the re.Match object.

Here's a corrected version of your code:

import re

data_table = []
temp_statement = input("Enter a template SQL statement: ")
data = " "
while data != "":
    data = input("Enter a data row (Enter to finish): ")
    data_row = data.split()
    data_table.append(data_row)

if temp_statement.startswith("INSERT"):
    start_index = temp_statement.rfind("VALUES (")
    for num in range(int(temp_statement.count(",")/2)):
        pattern = r'.{' + str(start_index) + r'}([^,]*)'
        match = re.search(pattern, temp_statement)
        if match:
            matched_string = match.group(1)
            temp_statement = temp_statement.replace(matched_string, data_table[num])
            start_index = temp_statement.rfind(data_table[num])
    print(temp_statement)
else:
    print("Not found")


In this version, match.group(1) extracts the matched string, which is then used in the replace() method. This should resolve the TypeError you encountered. Give it a try and let me know if it works!  

*End of this conversation*
