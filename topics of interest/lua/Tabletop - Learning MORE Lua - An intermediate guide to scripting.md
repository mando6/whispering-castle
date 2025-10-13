
Creating/Calling New Functions

A common practice in coding is to "call" another function. Some of these functions are part of the API. For example, using **print("Word")** is calling the function to put that string into the host's chat log. However we are not only limited to developer created functios, we can create out own. This can either be to continue a process elsewhere or to create your own function to create/modify/find information.  
  
Calling another function you create is as easy as making up a name for the function.

```lua
function onLoad() 
	anotherFunction() 
end 

function anotherFunction() 
	print("This will print on load") 
end
```

You can send parameters to your new function too.

```lua
function onLoad() 
	printThisString("This will be printed by a custom function.") 
end 

function printThisString(stringToPrint) 
	print(stringToPrint) 
end
```

You can also use functions to separate out work. There are multiple reasons you may choose to do this. You can use it on code that repeats or you can use it to make your code easier to read, avoiding large, bloated functions that try to do everything on their own. Plus, these functions can "return" information.

```lua
function onLoad() 
	local result = addTheseNumbers(2,3) 
	print(result) --prints "5" 
end 

function addTheseNumbers (num1, num2) 
	return num1 + num2 
end
```

Return will automatically end your function as soon as it runs, so it should always be the last step in a line of logic.  
  
Then you have larger functions, it can be hard to track what is being done at each step, leading to confusion. If this is a problem you are having, breaking one large function down into smaller functions can help you find problems.

Local/Global Variables

So far we have only worked with global variables, ones that persist and are available to the entire code. So for example, this would create a global variable.

```lua
function onLoad() 
	globalString = "I will always exist." 
	doATestPrint() 
end 

function doATestPrint() 
	print(globalString) --prints the string successfully 
end
```

But for most applications, using a local variable is preferred. They are created by placing the word "local" before your variable name when the variable is being created. Local variables only exist within the function they are created. When the function ends, a local variable is forgotten. If you only use Global variables, in longer scripts you will find yourself thinking of more and more complicated variable names, accidentally overwriting variables, accidentally using old variables, etc. So below is an example of how this local variable would be different.

```lua
function onLoad() 
	local localString = "I don't exist outside of this function." 
	doATestPrint() 
end 

function doATestPrint() 
	print(localString) 
	--Will not print the string 
	--Because that string doesn't exist in this function, only in onLoad 
end
```

But as you move your code into different functions, they will need a way to communicate and share these local variables sometimes. If that is the case, you can share a local variable with another function by sending it as a parameter.

```lua
function onLoad() 
	local localString = "I will be passed to another function."
	doATestPrint(localString) 
end

function doATestPrint(passedString) 
	print(passedString) --Will print successfully 
end
```

I personally avoid general variables as much as possible. I only ever use them if I need data to persist. For example, if you reference the example table, the "Save/Load" memory example has a Global variable which tracks the value of a counter.  

Coroutines

These are more advanced, but coroutines are perfect for managing short waits, pauses, delays etc. Normally, when a script is run, it all activates in one "frame" of the game. A coroutine can pause its running until the next frame, allowing you to chain those pauses together to make your script wait. This can also be used to wait for something you know will happen after a short delay (like waiting for an object to come to rest). DO NOT FEEL LIKE YOU NEED TO MASTER THESE. They are only used in specific circumstances, so as long as you understand WHY they are used, you will be alright.  
  
When we go to use a coroutine, rather than just calling a function's name, we use startLuaCorotuine to trigger it instead. All coroutines should end with return 1 in Tabletop Simulator, to properly terminate them when they are over. When using startLuaCoroutine, the first parameter is a reference to where the coroutine script can be found (in this example, Global script). The second parameter is the function name.

```lua
function onLoad() 
	startLuaCoroutine(Global, "exampleCoroutine") 
end 

function exampleCoroutine() 
	print("This will run right away, on load.") 
	return 1 
end
```

That example of a coroutine did not pause at all. If we want to add a pause, we run the code coroutine.yield(0). This will "yield", making the coroutine wait until the next frame before it continues. So in this next example, we will yield for 200 frames.

```lua
function onLoad() 
	startLuaCoroutine(Global, "exampleCoroutine") 
end

function exampleCoroutine() 
	print("This will run right away, on load.") 
	for i=1, 200 do 
		coroutine.yield(0) 
	end 
	print("This will run 200 frames after on load.") 
	return 1 
end
```

---BEGINNING OF EXAMPLES---

From this point forward, you should have a pretty good grasp of the basic concepts of making a good script. Now you just need to learn to put those concepts into practice. In my opinion, the best way to manage that is learning by example. If you have not already, subscribe to the [**WORKSHOP COMPANION TABLE**](http://steamcommunity.com/sharedfiles/filedetails/?id=879494019) for this guide.  
  
What follows will be short, simple descriptions of the concepts behind each example and what they do. On the example table, each token has scripting saved onto it, with detailed comments, explaining the inner workings of these tools. They also have information in their names/descriptions on what they are supposed to do.  
  
At this point in your learning, all the basics are covered, so all that is left is to learn from specific examples and, occasionally, googling for specific Lua functions (ex. a rounding function). Happy tinkering.

Example: takeObject()

[![](https://images.steamusercontent.com/ugc/172665724245568542/6A5CDA3E5A2FCC43941DE8CF92F822F2BBC34728/)](https://images.steamusercontent.com/ugc/172665724245568542/6A5CDA3E5A2FCC43941DE8CF92F822F2BBC34728/)takeObject() is how you get an object out of a container (deck or bag). This is used VERY commonly, and also has many core concepts associated with it you will come to rely on. There are two I specifically want you to learn about.  
  
The first is the concept of giving a function parameters to tell it what you want it to do. You create a table which contains certain named elements (ex: position, rotation, etc) and give it to takeObject. (ex. takeObject(parameters) ). The Knowledge Base outlines what parameters functions can accept.  
  
The second is the "callback" portion of the function. Some functions allow for a "callback", which means after the object from the function loads, it can call on another function to act. This is important, because when you use takeObject, you can't immediately take certain actions because the object doesn't physically exist on the table yet. So you can't lock it, set its tint, etc. So a callback will allow you to perform those actions after it has loaded into the world. Understanding callbacks is vital to manipulating objects after using takeObject.

Example: spawnObject()

[![](https://images.steamusercontent.com/ugc/172665724245568908/1AD67C7693124FEBD373DD2524439828262B6B7F/)](https://images.steamusercontent.com/ugc/172665724245568908/1AD67C7693124FEBD373DD2524439828262B6B7F/)This is used less commonly, but it allows you to spawn objects from nothing. It requires you to look up some information from the Knowledge Base, but other than that it is no more complicated than takeObject. Just think of it as takeObject but you are taking a blank slate out of thin air, and it is up to you to tell it what you want it to become.

Example: Timer

[![](https://images.steamusercontent.com/ugc/172665724245569147/F8F44CAB249B21314567B45E40350E12951FED82/)](https://images.steamusercontent.com/ugc/172665724245569147/F8F44CAB249B21314567B45E40350E12951FED82/)**THIS FUNCTION IS NOW DEPRECIATED**. It has been replaed with Wait.time(yourFunction, seconds). Please check out [http://api.tabletopsimulator.com](https://steamcommunity.com/linkfilter/?u=http%3A%2F%2Fapi.tabletopsimulator.com), under the Wait class, for multiple examples. I will leave this example here now, for the time being, and hopefully replace it later.  
  
The timer function allows you to trigger a function after X amount of time. The timers require a UNIQUE identifier. The name you use cannot be shared by any variable in ANY code on the table. Because of this restriction, it is a common practice to use an object's GUID when creating a timer, because that GUID should be unique.  
  
Currently in Tabletop Simulator timers will continue to run if the code is stopped/deleted. So if you have a recurring timer running, it will CONTINUE to run, and throw errors, if you end that instance of the code. Hitting undo or loading away from the table will cause these timer errors too, if the timer was running when the action was taken. This is a bug in TTS. In the Knowledge Base, you may see the option to repeat a timer automatically. I recommend not using it until this bug is rectified in the future.  

Example: Locating Objects

[![](https://images.steamusercontent.com/ugc/172665724245569424/1FEC59694390B15996006DDE1E48C69EAB37897D/)](https://images.steamusercontent.com/ugc/172665724245569424/1FEC59694390B15996006DDE1E48C69EAB37897D/)Locating objects is one of the things you do most in Tabletop Simulator, and often times you will find GUIDs an inconvenient or impossible way to manage it. There are many different ways to locate items, and they can be combined in various ways to get different results. But they all boil down to this: getting a pool of possible items that the item you want is a part of, and then going through and looking for some unique identifying information.  
  
You can use these same methods with many of the "Member Variables" listed in the Knowledge Base. What you will use is 100% dependent on the situation you are using it in, so be flexibile.  

Example: onSave()

[![](https://images.steamusercontent.com/ugc/172665724245569670/9AF9ED78829D6FAD1B8A49C9EEB880B597DAFB24/)](https://images.steamusercontent.com/ugc/172665724245569670/9AF9ED78829D6FAD1B8A49C9EEB880B597DAFB24/)Any time that you hit Undo or Redo or load a table, all of your scripts are starting anew. So if you were tracking a number using a Global variable, when you hit Undo that Global variable is going to be reset back to its default value you started it with.  
  
This is where onSave comes into play. It allows you to put anything you would like the script to remember between loads into a table. Then, when you load the table next, it will pull that information back out during onLoad() and let you access it. This is a fairly simple function that is vital to some scripts.  
  
A piece of personal advice, I recommend always leaving onSave() for last when scripting. The reason is that sometimes some information can be saved due to a bug in your script and saving over it is required to fix it, which can be tedious to keep track of. I typically set my script up to use onSave but then don't actually activate it until I feel like I have everything else working how I intend it to.  

Example: math.random()

[![](https://images.steamusercontent.com/ugc/172665724245601215/3649C56222A9A2A2B5A0C43C1B8CD9E57DA6DD0A/)](https://images.steamusercontent.com/ugc/172665724245601215/3649C56222A9A2A2B5A0C43C1B8CD9E57DA6DD0A/)These are important for selecting random players, items, etc. They can be used to pick an element out of a table or select random colors for RGB and more. If you give math.random() no parameters it will pick a number between 0 and 1 (ex. 0.24531). If you give if 2 parameters, it will use those as the floor/ceiling values to pick from. Example: math.random(1,3) would result in a whole number (1, 2 or 3) being returned.  
  
But getting truly random numbers in scripting can be a bit tricky. The way they are generated is with a math formula which uses a "seed" number as its basis. You can set this seed value with math.randomseed(numberhere). If you used the number 1 for numberhere and then did math.random(), it would give you a result. If you set the randomseed to number here again and did another math.random, you'll end up with the same exact result. Because it is just based on that formula.