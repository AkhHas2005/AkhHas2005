# Restarting Loop on None Value in Python  

## Me
I have the following system in place in Python where I want to stop the loop when a None is received (it is recieved when I want to receive a file download as this doesn't complete in a loop) but then I want to reinstate the loop and do this everytime the None value is received, how can I modify my code:  

```Python
def run(self):
  print("Welcome to the Bradford Patient's Recording System (now with AI features!)")
  print()
  continue_menu = self.handle_menu_choice()
  while continue_menu:
    continue_menu = self.handle_menu_choice()
    if continue_menu is None:
      break
    if not continue_menu:
      break
  print("Thank you for using the Bradford Patient's Recording System!")
```

## Co-Pilot
To achieve the desired behavior, you can use a loop that restarts the process when `None` is received. You can incorporate an outer `while True` loop to achieve this. Here's how you can modify your code:

```python
def run(self):
    print("Welcome to the Bradford Patient's Recording System (now with AI features!)")
    print()
    
    while True:
        continue_menu = self.handle_menu_choice()
        while continue_menu:
            if continue_menu is None:
                print("Received None, handling file download...")
                break
            continue_menu = self.handle_menu_choice()
            if not continue_menu:
                break
        else:
            continue
        break

    print("Thank you for using the Bradford Patient's Recording System!")
```

This way, the outer `while True` loop will ensure that the process restarts when `None` is received. The `else` clause in the inner `while` loop will only be executed if the loop is not exited via a `break` statement. If the `continue_menu` is `None`, it will break out of the inner loop and handle the `None` case, and then the outer loop will continue, effectively restarting the process. If the user chooses to exit the menu (`continue_menu` is `False`), the outer loop will break, and the program will finish.

This should give you the desired behavior where the system restarts the loop when `None` is received and handles file downloads accordingly.  

## Me
It still terminates teh program, it does reinstate teh loop  

## Co-Pilot
It looks like we need to modify the logic to ensure the loop reinstates after handling the `None` value. Let’s adjust your code to re-enter the outer loop after handling the file download:

```python
def run(self):
    print("Welcome to the Bradford Patient's Recording System (now with AI features!)")
    print()
    
    while True:
        continue_menu = self.handle_menu_choice()
        while continue_menu is not None:
            if continue_menu is None:
                print("Received None, handling file download...")
                # Handle the file download here
                break
            if not continue_menu:
                break
            continue_menu = self.handle_menu_choice()
        
        # If continue_menu is None, it will break the inner loop and continue the outer loop
        if continue_menu is None:
            continue
        
        # If continue_menu is False, it will break the outer loop and end the program
        break

    print("Thank you for using the Bradford Patient's Recording System!")
```

In this version, the outer `while True` loop ensures the process restarts whenever `None` is received. The `continue_menu is not None` condition in the inner loop keeps it running until `None` is received. If `None` is received, it breaks the inner loop but then continues the outer loop, effectively reinstating the process. If `False` is received, it breaks the outer loop and ends the program. Give this a try and see if it works as expected.  

## Me
Ok so I tried this and teh loops stops then getsreinstated. However, the file doesn't download, I'm in Google Colab and trying tio download the file via the method from the files class in Colab, what else can I do?  

## Co-Pilot
It sounds like the file download may not be properly handled within the loop. Let’s ensure that the file download process is correctly integrated within your system. Here’s how you can modify the code to handle the file download using the `files` class in Google Colab:

First, you need to make sure you import the necessary module for handling files in Google Colab:

```python
from google.colab import files
```

Then, modify your `run` method to handle the file download when `None` is received:

```python
from google.colab import files

def run(self):
    print("Welcome to the Bradford Patient's Recording System (now with AI features!)")
    print()
    
    while True:
        continue_menu = self.handle_menu_choice()
        while continue_menu is not None:
            if continue_menu is None:
                print("Received None, handling file download...")
                # Handle the file download here
                files.download('your_file.txt')  # Replace 'your_file.txt' with the actual file name
                break
            if not continue_menu:
                break
            continue_menu = self.handle_menu_choice()
        
        # If continue_menu is None, it will break the inner loop and continue the outer loop
        if continue_menu is None:
            continue
        
        # If continue_menu is False, it will break the outer loop and end the program
        break

    print("Thank you for using the Bradford Patient's Recording System!")
```

This code will ensure that when `None` is received, it handles the file download using the `files.download` method from the `google.colab` module. Replace `'your_file.txt'` with the actual file name you want to download.

Give this a try and see if it resolves the issue with the file download in Google Colab. If you encounter any specific errors or problems, feel free to share them, and I’ll be happy to help!  

*End of this Conversation*
