# File Path Issue with Python Code  

## Me
This is my code but I get an error:  
Python code:  

    def extractHoursFromFile(fileName):  
      hoursArray = []  
      with open(fileName, 'r') as f:  
        print("The contents of the work hours file is as follows:")  
        for line in f.readlines():  
          print(line)  
          hoursArray.append(line)  
      return hoursArray  
      
    print("Please note that the file has to be a plaintext file (.txt)")  
    filePath = input("What is the path of your work hours file? ")  
    hoursArray = extractHoursFromFile(filePath)  

And this is teh output (including the error):  
Please note that the file has to be a plaintext file (.txt)  
What is the path of your work hours file? "C:\Users\HasanAkh1\OneDrive - bradford.gov.uk\Word docs\WorkHours-History.txt"  

    Traceback (most recent call last):  
    File "c:\Users\HasanAkh1\OneDrive - bradford.gov.uk\Markdown and Python\basichourscalculatorv5.py", line 361, in <module>  
    uploadApp.getUpload()  
    File "c:\Users\HasanAkh1\OneDrive - bradford.gov.uk\Markdown and Python\basichourscalculatorv5.py", line 185, in getUpload  
    hoursArray = self.extractHoursFromFile(filePath)  
                 ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^  
    File "c:\Users\HasanAkh1\OneDrive - bradford.gov.uk\Markdown and Python\basichourscalculatorv5.py", line 163, in extractHoursFromFile  
    with open(fileName, 'r') as f:  
         ^^^^^^^^^^^^^^^^^^^  
    OSError: [Errno 22] Invalid argument: '"C:\\Users\\HasanAkh1\\OneDrive - bradford.gov.uk\\Word docs\\WorkHours-History.txt"'  

## Co-Pilot
[1]: https://python.land/deep-dives/python-try-except ""
[2]: https://stackoverflow.com/questions/45539614/extract-hour-from-timestamp-in-python ""
[3]: https://blog.finxter.com/5-best-ways-to-extract-the-hour-from-time-in-python/ ""

It looks like the issue is with the file path you provided. The error `OSError: [Errno 22] Invalid argument` typically occurs when the file path is not correctly formatted. In your case, the double quotes around the file path are causing the problem.

Here's a revised version of your code that removes the double quotes from the input:

```python
def extractHoursFromFile(fileName):
    hoursArray = []
    with open(fileName, 'r') as f:
        print("The contents of the work hours file is as follows:")
        for line in f.readlines():
            print(line)
            hoursArray.append(line)
    return hoursArray

print("Please note that the file has to be a plaintext file (.txt)")
filePath = input("What is the path of your work hours file? ").strip('"')
hoursArray = extractHoursFromFile(filePath)
```

The `strip('"')` method removes any leading and trailing double quotes from the file path input. This should resolve the `OSError` you're encountering.

Give this a try and let me know if it works! If you encounter any other issues, feel free to ask.

Learn more: [1. python.land](https://python.land/deep-dives/python-try-except) 
[2. stackoverflow.com](https://stackoverflow.com/questions/45539614/extract-hour-from-timestamp-in-python)
[3. blog.finxter.com](https://blog.finxter.com/5-best-ways-to-extract-the-hour-from-time-in-python/)  

*End of this Conversation*
