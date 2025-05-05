# Integrating code to make textbox that can scroll in Python Tkinter  

## Me
How can I integrate teh following into my code to make a textbox that can be scrolled down and across if the input overflows  
Code to integrate:  

    # Python Program to make a scrollable frame using Tkinter  
    
    from tkinter import *

    class ScrollBar: 
      # constructor 
      def __init__(self):  
        # create root window 
        root = Tk() 
        # create a horizontal scrollbar by setting orient to horizontal 
        h = Scrollbar(root, orient = 'horizontal')  

        # attach Scrollbar to root window at the bootom 
        h.pack(side = BOTTOM, fill = X) 
        
        # create a vertical scrollbar-no need to write orient as it is by default vertical 
        v = Scrollbar(root) 
        
        # attach Scrollbar to root window on the side 
        v.pack(side = RIGHT, fill = Y) 
        
        # create a Text widget with 15 chars width and 15 lines height 
        # here xscrollcomannd is used to attach Text widget to the horizontal scrollbar 
        # here yscrollcomannd is used to attach Text widget to the vertical scrollbar 
        t = Text(root, width = 15, height = 15, wrap = NONE, 
                 xscrollcommand = h.set, yscrollcommand = v.set)  

        # insert some text into the text widget 
        for i in range(20): 
          t.insert(END,"this is some text\n") 
          
        # attach Text widget to root window at top 
        t.pack(side=TOP, fill=X) 
        
        # here command represents the method to be executed 
        # xview is executed on object 't' 
        # Here t may represent any widget 
        h.config(command=t.xview) 
        
        # here command represents the method to be executed 
        # yview is executed on object 't' 
        # Here t may represent any widget 
        v.config(command=t.yview) 
        
        # the root window handles the mouse click event 
        root.mainloop()  
        
    # create an object to Scrollbar class 
    s = ScrollBar() 
    
My code: 

    #Importing the modules 
    import vertexai from vertexai.generative_models 
    import GenerativeModel 
    import google.auth 
    from tkinter import * 
    
    credentials, project_id = google.auth.default() 
    vertexai.init(project="generalpurposeai", location="us-central1") 
    model = GenerativeModel(model_name="gemini-1.0-pro")  

    class ChatbotWindow(Tk): 
      def __init__(self): 
        super().__init__() 
        self.title('AI Cover Letter Writer') 
        
        # Create text widget for conversation 
        self.conversation = Text(self, state='disabled') 
        self.conversation.pack(expand=True, fill='both') 
        
        # Create entry widget for user input 
        self.user_input = Entry(self) 
        self.user_input.pack(side='left', expand=True, fill='x') 
        
        # Create send button 
        self.send_button = Button(self, text='Send', command=self.send_message) 
        self.send_button.pack(side='right')  

        def send_message(self): 
          prompt = self.user_input.get() 
            if prompt: 
              # Add user message to conversation 
              self.conversation.configure(state='normal') 
              plaintext_prompt = f"""Given the contents of my CV (Resume) and the job description which are below: 
              \nMy Resume/CV is as follows: {prompt} 
              The job description is as follows: {prompt} \
              nPlease generate an appropriate cover letter.""" 
              responses = model.generate_content(plaintext_prompt, stream=True) 
              for response in responses: 
                self.conversation.insert('end', response.text) 
              self.conversation.insert('end', '\n') 
              self.conversation.configure(state='disabled')  

    if __name__ == "__main__": 
      window = ChatbotWindow() 
      window.mainloop()  
    
## Co-Pilot
![Python settings Tkinter window screenshot](https://www.bing.com/th?id=OSK.2c1420bb4985b9ecbc52f2fb4f554131&pid=cdx&w=320&h=189&c=7&rs=1)  

[1]: https://www.geeksforgeeks.org/python-tkinter-scrolledtext-widget/ ""
[2]: https://www.askpython.com/python-modules/tkinter/tkinter-text-widget-tkinter-scrollbar ""
[3]: https://stackoverflow.com/questions/49207769/how-to-get-text-box-to-horizontally-scroll-over-inserted-widgets ""
[4]: https://customtkinter.tomschimansky.com/documentation/widgets/scrollbar/ ""
[5]: https://docs.python.org/3/library/tkinter.scrolledtext.html ""
[6]: https://www.pythontutorial.net/tkinter/tkinter-scrolledtext/ ""
[7]: https://www.w3resource.com/python-exercises/tkinter/python-tkinter-widgets-exercise-10.php ""
[8]: https://getdocs.org/Python/docs/3.7/library/tkinter.scrolledtext ""

To integrate a scrollable textbox into your existing code, you can use the `ScrolledText` widget from the `tkinter.scrolledtext` module. This widget simplifies the process of adding both vertical and horizontal scrollbars to a `Text` widget. Here's how you can modify your `ChatbotWindow` class to include a scrollable textbox:

```python
# Importing the modules
import vertexai
from vertexai.generative_models import GenerativeModel
import google.auth
from tkinter import *
from tkinter.scrolledtext import ScrolledText

credentials, project_id = google.auth.default()

vertexai.init(project="generalpurposeai", location="us-central1")

model = GenerativeModel(model_name="gemini-1.0-pro")

class ChatbotWindow(Tk):
    def __init__(self):
        super().__init__()
        self.title('AI Cover Letter Writer')

        # Create scrolled text widget for conversation
        self.conversation = ScrolledText(self, wrap=NONE)
        self.conversation.pack(expand=True, fill='both')

        # Create entry widget for user input
        self.user_input = Entry(self)
        self.user_input.pack(side='left', expand=True, fill='x')

        # Create send button
        self.send_button = Button(self, text='Send', command=self.send_message)
        self.send_button.pack(side='right')

    def send_message(self):
        prompt = self.user_input.get()
        if prompt:
            # Add user message to conversation
            self.conversation.configure(state='normal')
            plaintext_prompt = f"""Given the contents of my CV (Resume) and the job description which are below:
            \nMy Resume/CV is as follows: {prompt}
            The job description is as follows: {prompt}
            \nPlease generate an appropriate cover letter."""
            responses = model.generate_content(plaintext_prompt, stream=True)
            for response in responses:
                self.conversation.insert('end', response.text)
            self.conversation.insert('end', '\n')
            self.conversation.configure(state='disabled')

if __name__ == "__main__":
    window = ChatbotWindow()
    window.mainloop()
```

This modification uses the `ScrolledText` widget, which automatically includes both vertical and horizontal scrollbars when the text overflows[^1^][1][^2^][2]. This should make your `ChatbotWindow` more user-friendly by allowing users to scroll through the conversation easily.

[^1^][1]: [GeeksforGeeks - Python Tkinter ScrolledText Widget](https://www.geeksforgeeks.org/python-tkinter-scrolledtext-widget/)
[^2^][2]: [Python Documentation - tkinter.scrolledtext](https://docs.python.org/3/library/tkinter.scrolledtext.html)

Feel free to ask if you need further assistance!

Learn more: [1. www.geeksforgeeks.org](https://www.geeksforgeeks.org/python-tkinter-scrolledtext-widget/) 
[2. www.askpython.com](https://www.askpython.com/python-modules/tkinter/tkinter-text-widget-tkinter-scrollbar)
[3. stackoverflow.com](https://stackoverflow.com/questions/49207769/how-to-get-text-box-to-horizontally-scroll-over-inserted-widgets)
[4. customtkinter.tomschimansky.com](https://customtkinter.tomschimansky.com/documentation/widgets/scrollbar/)
[5. docs.python.org](https://docs.python.org/3/library/tkinter.scrolledtext.html) 
[6. www.pythontutorial.net](https://www.pythontutorial.net/tkinter/tkinter-scrolledtext/) 
[7. www.w3resource.com](https://www.w3resource.com/python-exercises/tkinter/python-tkinter-widgets-exercise-10.php)
[8. getdocs.org](https://getdocs.org/Python/docs/3.7/library/tkinter.scrolledtext)
[9. en.wikipedia.org](https://en.wikipedia.org/wiki/Tkinter)  

*End of this Conversation*
