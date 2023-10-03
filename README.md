# tkinter-studies
Learning how to work with GUI and tkinter

Tkinter comes pre-installed with Python3, and you need not bother about installing it.

```py
# Import tkinter module
import tkinter

# Initialize the window manager
window = tkinter.Tk() # blank window with close, maximize, and minimize buttons on the top

# (Optional) Rename the GUI window
window.title("tkinter-studies")

# Geometry management 
# first test with no geometry management

# Define the label widget
label = tkinter.Label(window, text ="Hello World!").pack() # a widget that is used to insert some text into the window

# Mainloop method
window.mainloop() # method to display the window until you manually close it
```

* pack(): It organizes the widgets in a block manner, and the complete available width is occupied by it. Useful to define frames.
* grid(): It organizes the widgets in a table-like structure. 
* place(): Its purpose is to place the widgets at a specific position as instructed by the user in the parent widget.


Results:

![image](https://github.com/Rafaelatff/tkinter-studies/assets/58916022/f4206a53-c22b-4ceb-887f-3994472c64ca)

Manually, I can easily change its size.

![image](https://github.com/Rafaelatff/tkinter-studies/assets/58916022/16b65bcf-6eca-4287-a1ec-b0cdf9eb02d1)

Now let's add some geometry to the window and also a button:

```py
# Geometry management 
window.geometry("500x300")

# Let's create two frames
top_frame = tkinter.Frame(window).pack()
bottom_frame = tkinter.Frame(window).pack(side = "bottom")

# Let's keep a text
label = tkinter.Label(top_frame, text ="Press the button:").pack()
# And add the button
btn_widget = tkinter.Button(bottom_frame, text = "Button!", fg = "purple").pack() # I could use .pack(side = "left")
```
To set window size: window.geometry("**width**x**height**")

As results:

![image](https://github.com/Rafaelatff/tkinter-studies/assets/58916022/b5cbebe7-e6d4-4358-b755-4932fdb13661)



