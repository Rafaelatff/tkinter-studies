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

I can, optionaly create the main window using only ```window = Tk()``` instead of ```window = tkinter.Tk()```. But for that I need to use ```from tkinter import *```.

```py
from tkinter import *
window = Tk()
```

Note: If I do the second way, later I need to call others import such as ```import tkinter.filedialog```.

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

## Now let's focus on our project!

First I will add a feature, that when the user tries to close the window, a new window opens asking if he is sure about his decision. For that, we need to use the [wm_protocol](https://web.archive.org/web/20200731093951id_/http://effbot.org/tkinterbook/wm.htm#Tkinter.Wm.protocol-method) method of the toplevel window. Specifically, we are interested in the WM_DELETE_WINDOW protocol. Using that method, it allows us to register a callback which is called when the window is being destroyed.

For that I need to add a few lines to our code:

```py
##### AT THE BEGIN OF THE CODE #####

import tkinter.messagebox as tkMessageBox

### defs at the begin of the code ###
def callback():
    if tkMessageBox.askokcancel("Sair", "Tem certeza que deseja sair?"):
        window.destroy()

##### AT THE BOTTON OF THE CODE #####

# Mainloop method
window.protocol("WM_DELETE_WINDOW", callback)
window.mainloop() # method to display the window until you manually close it

```

Bonus: I finally learn how to comment more than one line :D I am sooo happy.

```py
''' this coments
more than just
one line '''
```
As results:

![image](https://github.com/Rafaelatff/tkinter-studies/assets/58916022/b885c5cf-fd25-4718-a964-c2d457ce9277)

## Entry value

Let's create a box, so user can entry a value to a variable. In our case it will be our variable for the window size of the [running statistics](https://github.com/Rafaelatff/Running-statistics).

First we are going to create a small text to assist the user:

```py
# Create text to assist user 
text = tk.Label(bottom_frame, text = "Tamanho da janela:")
text.place(x=110,y=263)
```
Then we are going to create a Entry space, where user can add a value. We will set the position and value. In our case we add 5 and "5".

```py
# Create box to receive value
window_size = tk.Entry(bottom_frame, width=10)
window_size.place(x=230,y=264)
window_size.insert(5, "5")
```
Just by typing a value in the Entry box, the variable won't be modified. We need a button to make the action of sendind the value to the variable. First we are going to create the button, as showed in next code lines:

```py
# Create button to save value to the variable
b_save_value = tk.Button(bottom_frame,text="GRAVAR", width=10, command = save_value)
b_save_value.place(x=300, y=260)
b_save_value.config(state="normal")
```
An error is pressented at this point, because we call the ```command = save_value``` but we didn't create the function. Let's to that! At the begin of the code we add the following function:

```py
def save_value():
    entry = window_size.get() # Takes string fist
    window_size_N = int(entry) # Then convert str to int
    print(window_size_N)
    if window_size_N <= 1:
        print('Window size cannont be lesser than 2')
    elif window_size_N > 101: #elif = else if
        print('Window size cannont be greater than 101')
    else:
        print('Running statistcs considering window size of: ', window_size_N)
```

To take the value from the Entry box, we use the .get() methode. It recovers a string value. Then we use the int() to get the int value from the string.

Note: We changed the window size to 1000x300 and set ```window.resizable(0,0)```, so user can't resize window.

As results:

![image](https://github.com/Rafaelatff/tkinter-studies/assets/58916022/dc1ad82e-d2bd-46cb-963e-26b5d498bb72)

## Graphic

## Save graphic button







