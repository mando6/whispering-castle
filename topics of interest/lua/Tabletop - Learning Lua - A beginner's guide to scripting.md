  
Setting Up

When you save your scripts in Tabletop, it will use your most recent save and then load the script into it. So for any script you intend to write, you will need to do the following:

- Set up the table the way you want it.  
    
- Save the table.  
    
- Load the table.

For this exercise, take a blank table and spawn two objects (I used a square block and rectangle block) as well as a red checker.  
  
Remember to save/load then open up the scripting in Atom or go to Host > Scripting in Tabletop Simulator to begin.

![[Pasted image 20251001151837.png]]

Global.lua

Global.lua is the scripting which is a part of the save file. It is where we will be working for most of this tutorial. On a new save, it always starts with some text saved into the editor. Just delete it, we will not be using it.  
  
It is also possible to write scripts and attach them to objects instead of Global. That way if you save and object it will save its LUA right along with it. You can perform most functions using either Global or Item scripts but we will be working in Global.

Functions

Functions are what trigger groups of code. Some of them are built into the scripting system (_ex. onload()_) while others can be created by the user. Every function will start with the word **function** and end with the word **end**.

A common function built into Tabletop Simulator is onload(). This function triggers every time the script is loaded (like if Undo/Redo is pressed). So let us get started by using it to activate a function we will create. Functions should start with a lowercase letter, and cannot contain spaces. We'll use exampleFunction.

```lua
function onload()
	exampleFunction()
end
```

Now our script, when it loads, will try to run a function named exampleFunction. But we haven't written one yet! So now we will create our own function, right after the onload function has ended.

```lua
function exampleFunction()
	print('Hello, World.')
end
```

The command of **print()** is also a function. But instead of triggering a section of code in LUA, it activates programming inside of Tabletop Simulator to produce a desired effect. In this case, printing a message to the host of the game, in chat.  
  
The message is called a **string**, and is always surrounded by quotes to indicate that. A string is a series of characters. (Ex: _"This is a string."_ or _'So is this!'_)When you save and upload your script, it should now print "Hello, World." to chat.  
  
**Extra Credit:** When you create your own function, you can also pass variables along with it for the function to use. Another way to write our starting exercise would be:

```lua
function onload()
	exampleFunction('Hello, World!')
end
function exampleFunction(passedString)
	print(passedString)
end
```

We created a variable to represent the string (_passedString_) and then printed what was contained in that variable.

Objects

Objects are the physical entities that exist within tabletop. In our example, our objects currently are two blocks and a checker (what a terrible game we are making). Using scripting, we can manipulate objects, move them, add buttons to them or perform other various actions. **We're starting our Global.lua over fresh. Erase all text in it.**

![[Pasted image 20251001152242.png]]

GUIDs
To affect and object, first we must identify it in LUA. There are several ways to do this, such as identifying items being picked up or put down by players, finding objects inside of a scripting zone and more. We will be identifying these objects by their GUID.  
  
A **GUID** is a unique identifier which each spawned item in TS will have. Even 2 of the same item will have different GUIDs. To locate an object's GUID, right click on it and go to Scripting. If you click on its GUID there, it will copy it to your clipboard. A GUID is always a string, so remember strings are always in quotes. Lets create some variables with the GUIDs of our objects. **REMEMBER:** Your GUIDs will be different than mine.

```lua
object1_GUID = '195868'
object2_GUID = '333365'
checker_GUID = '7dc60d'
```

Defining Objects
Then, using onload so this happens when the script is loaded, we will make variables to represent our objects. All of these variable names we've been making must start with a lower case letter and not contain spaces, but other than that you are fairly free to make up variable names yourself. You want to make it clear what it represents. I will be using object1, object2 and checker to represent my objects. The function we will use to identify will be getObjectFromGUID(string). We place the GUID in the spot for the string.

```lua
function onload()
	object1 = getObjectFromGUID(object1_GUID)
	object2 = getObjectFromGUID(object2_GUID)
	checker = getObjectFromGUID(checker_GUID)
end
```

Manipulating Objects
Now we need to manipulate these objects somehow. We will give them a name. In onload(), after we defined our objects, we will use the function of setName(string). Notice that setName, like other object functions, must be tied to an object. Otherwise the script will not understand what object's name we want to change. The string in setName will be what we set the name to.

```lua
object1.setName('Object1') 
object2.setName('Object2') 
checker.setName('That Stupid Checker')
```

**Extra Credit:** You may be curious as to why we didn't put the object GUIDs directly into getObject (EX: object1 = _getObjectFromGUID('195868')_ ). We could have, it would work. This example was to show you that, sometimes, it is more convenient to set a variable early on so you can reference it later. That way, if that variable needs to change (new GUID) you don't have to try to track it down to fix it throughout your code.  
  
If you wanted to, for the checker, there is no reason you couldn't write it like:

```lua
function onload() getObjectFromGUID('7dc60d').setName('That Stupid Checker') end
```

The reason I do not encourage that for learners is partially an aesthetic choice, and partially for code clarity. You want it to be easy for someone else to understand your code, and once you start doing things more complex than changing the name of an object it can get VERY difficult to see what is going on. It can also make future revisions to your code a chore.

Buttons
While there are many ways to activate functions, buttons are a convenient way to activate sections of code at the player's choosing. All buttons must be attached to an object, and are created using parameters. The object we want to attach our button to is our checker, and those parameters are found on the Objects page in the Knowledge Base. Many are optional, here they are for reference.  

- **click_function = _String_** --The name of the function which will activate when this button is pressed.  
    
- **function_owner = _Object_** --Determines where the function that the button activates lives (global or an object's script).  
    
- **labels = _String_** --The name on the button.  
    
- **position = _Table_** --X, Y and Z coordinates for where the button appears, from the center of the object it is attached to.  
    
- **rotation = _Table_** --Pitch, Roll and Yaw in degrees, relative to the object it is attached to.  
    
- **width = _Number_** --How wide the button is, relative to the scale of its object.  
    
- **height = _Number_** --How tall the button is, relative to the scale of its object.  
    
- **font_size = _Number_** --Size of the text on the button, relative to the scale of its object.

![[Pasted image 20251001152632.png]]

Tables
Tables in LUA are collections of entries. You can store most anything inside of a table and reference it later. All tables are indicated by curly brackets {}. You can reference entries in a table by a name or by an index number (what number entry it is, indexes start at 1 in LUA.). We will be creating a table right beneath where we established our GUIDs and then filling it with entries to use with the createButton(table) function. The name we are choosing for our table is button_paramiters

```lua
button_parameters = {} 
button_parameters.click_function = 'buttonClicked' button_parameters.function_owner = nil 
button_parameters.label = 'Press Me' 
button_parameters.position = {0,0.8,0} 
button_parameters.rotation = {0,0,0} 
button_parameters.width = 500 b
utton_parameters.height = 500 
button_parameters.font_size = 100
```

Now we have a table with the paramiters listed within it. So lets use the object function to create a button on the checker. Enter this inside of function onload() before its end.

```lua
checker.createButton(button_parameters)
```

Check Your Work
Save and apply your code. You should now have a button which floats a few inches above your checker. If you don't see it and didn't get an error, try flipping your checker over. It might be upside down so the button is hiding inside the table! If you did flip the checker over, remember to save over your old save with the checker correctly positioned.  
  

Add Button Function

Now we need to add the button's function into our code. To test the function out, we'll print ourselves a message. We'll add this user-defined function to the end of our script.

```lua
function buttonClicked() 
	print('Learning is fun. Sort of.') 
end
```

After uploading our script, pressing the button should print our message once for each click.  
[![](https://images.steamusercontent.com/ugc/490146591486191640/23858C6BE6922BD3054E2995154760D813E6287A/)](https://images.steamusercontent.com/ugc/490146591486191640/23858C6BE6922BD3054E2995154760D813E6287A/)  
  
Click it repeatedly because of course you will.  
[![](https://images.steamusercontent.com/ugc/490146591486192037/4D2EE8EDB05A407737B6D79DEF44A26125B40DFD/)](https://images.steamusercontent.com/ugc/490146591486192037/4D2EE8EDB05A407737B6D79DEF44A26125B40DFD/)

**EXTRA CREDIT:** When you create tables, there are [several ways to accomplish it](https://steamcommunity.com/linkfilter/?u=https%3A%2F%2Fwww.lua.org%2Fpil%2F3.6.html)[www.lua.org]. The way used here was to provide visual clarity. However, creating button parameters like this, if you are going to have many buttons, takes up A LOT of space. I prefer to create my tables in such a way that it saves space but doesn't create a run-on line that goes well off the right side of the screen. Using our example, I would have created my parameter table like this:

```lua
button_parameters = { 
	click_function='buttonClicked', function_owner=nil, label='Press Me', 
	position={0,0.8,0}, rotation={0,0,0}, width=500, height=500, font_size=100 
}
```

**EXTRA CREDIT:** This is the perfect point to start playing with different things you can do with objects. Go to the Object page in the Knowledge Database and try stuff. Move the objects, make them switch positions, change their colors, whatever you can think of.  
  
**EXTRA CREDIT:** Also, any time you press a button, its click_function triggers with 2 parameters. The first is an object reference, specifically the reference to the object the button is attached to. The second is a color (ex. "Blue") in string format of the color player who pressed the button.

Logic Statements

Logic Statements are generally called "if statements". They are used to tell your code what you want it to do in a given situation. When the statement is activated (say, by pressing a button) the logic contained in its statement will only be activated if the condition given is true. They are always formatted as:

```lua
if CONDITION then 
	--Activates if condition was true 
end
```

You can also add "else" to that, so that if the statement is false, something ELSE happens instead. Notice here I added commenting using two minus signs in a row. The engine will ignore anything on a line after --.

```lua
if CONDITION then 
	--Activates if condition was true 
else 
	--Activates if condition was false 
end
```

What you place in the area I labeled CONDITION in these examples are called [relational and conditional operators.](https://steamcommunity.com/linkfilter/?u=http%3A%2F%2Fwww.tutorialspoint.com%2Flua%2Flua_operators.htm)[www.tutorialspoint.com] Using them, you can compare many things to eachother. They produce what is called a boolian value (a variable value that is either "true" or "false").

![[Pasted image 20251001152907.png]]

Our First Logic Statements

We will try a few of these out. **Erase the current contents in your buttonClicked() function.** Now enter into that function these statements:

```lua
if 5 > 6 then 
	print("5 is greater than 6") 
end 

if 6 > 4 then 
	print('6 is greater than 5') 
end 

if 5 == 0 then 
	print("Five is equal to ZERO?!") 
else 
	print("No, five isn't equal to zero.") 
end
```

When those lines are used and the button pressed, you will see that only the print functions located in the TRUE statement were printed. Also, because 5==0 is a false statement it activated the print function located in the "else" part of the logic.  
[![](https://images.steamusercontent.com/ugc/490146591486300574/DFA4AC472759E4E8C4B91FB71D7FEA8CA176CB72/)](https://images.steamusercontent.com/ugc/490146591486300574/DFA4AC472759E4E8C4B91FB71D7FEA8CA176CB72/)  
  

Comparing Variables

Once again, **erase all of the scripting inside of the buttonClicked() function.** We are going to be creating a new variable, then altering it. The new variable will be a bool. Bool values can only be true, false or nil (nil means neither). Bool values are always written in all lower case. First, we will create our variable just beneath our object and checker GUIDs being established.

```lua
trueOrFalse = true
```

Then, in buttonClicked, we will establish some logic to check if trueOrFalse is, well, true or false. If it is true, we'll print that it was true and switch it over to false. If the button is clicked again, it will print that it was false and switch it to true.

```lua
if trueOrFalse then 
	print('trueOrFalse was true.') 
	trueOrFalse = false 
else 
	print('trueOrFalse was false.') 
	trueOrFalse = true
end
```

We could have also written that as "if trueOrFalse == true then" but that is unnecesary. Remember, the IF statement just needs to be fed True or False. And since trueOrFalse is already one of those, we can skip the operators.

 Loops
 Loops are sections of code that can run multiple times/continuously when activated only once. These are some of the more complex elements you will use in LUA. They often go hand-in-hand with tables, allowing you to run code on each entry in the table.

![[Pasted image 20251001153012.png]]

Numeric For Loops
A Numeric For Loop  is one which runs a set number of times. You give it 2 or 3 numbers and a unique variable name (I will use "i", which stands for index) and it starts at the first number, then goes until it hits the second number. If a third number is used, it will count by that. So normally it counts up from 1 by 1, but if you put, as a third number, a 2 it would count by 2s. Each number is separated by a comma. Replace the code in your buttonClicked function with this and give it a try. "i", the index, will be equal to 1 on the first run, then it will go up by 1, and be equal to 2 and run again, and keep doing that until it hits 10.

```lua
for i=1, 10 do 
	print(i) 
end 
print('Loop Finished')
```

What the output is upon pressing the button:  
[![](https://images.steamusercontent.com/ugc/490146591486498099/0C9ABDF150AEE8F2C24FDF4102CEDEE5AFD0D41C/)](https://images.steamusercontent.com/ugc/490146591486498099/0C9ABDF150AEE8F2C24FDF4102CEDEE5AFD0D41C/)  
  

Generic For Loops

A [generic for loop](https://steamcommunity.com/linkfilter/?u=https%3A%2F%2Fwww.lua.org%2Fpil%2F4.3.5.html)[www.lua.org] is one which runs through entries in a table. For example, the button_parameter table we created. We would set two variables, one for index and one for value, in the loop and then it would run through each entry in the provided table. For each entry in the table, it would make index equal the name of the variable (Ex: position, width, etc) and value equal that values we gave each entry. Add this after your current for loop in buttonClicked.

```lua
for i, v in pairs(button_parameters) do 
	print(i) 
end
```

What the output is upon pressing the button:  
[![](https://images.steamusercontent.com/ugc/490146591486496851/29BF89F6A6F23C35EE50142184E9A53724EE0666/)](https://images.steamusercontent.com/ugc/490146591486496851/29BF89F6A6F23C35EE50142184E9A53724EE0666/)  
There is another type is ipairs. Pairs is for tables with non-numeric keys, while ipairs is for sequential numeric keys (arrays). ipairs goes in order, while pairs can go in any order.  
  

Break
Break will end a for loop as soon as it is activated. For instance, if you added to your numeric for loop, just after its print function, the line **if i== 3 then break end**, it would end the loop after it had printed 1, 2, 3.

Scripting Outside of Global
In order to write a script directly into an object, right click that object in game, go to Scripting, and select Lua Editor (if you use Atom, this will open a window in Atom for it).  
  
When you write LUA here, it is just like global. Except if you need to reference the object the script is a part of, you simply write "self" without the quotes, all lower case. So to create a button on itself, you would use self.createButton(table_of_paramiters).
