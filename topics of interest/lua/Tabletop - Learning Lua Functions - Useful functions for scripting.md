These functions are designed more for those with at least an introductory understanding of how Lua/scripting works.  
  
Each entry has the following breakdown to explain how to use the function:  
```

- Function: A description of what this function will do.  
    
- Takes: the type of input/inputs required.  
    
- Returns: the type of output/outputs generated.  
    
- Example Input: an example of the type of field you could give the function  
    
- Example Output: an example of what the function will return as a result
  
The function's code.

Some functions that I feel need further explanation or clarification will have additional notes added in this area.
```

Instructions

To use these functions, you would call on them in your script. For example, say you wanted to find a deck in a scripting zone when your script loads, and print its name. You could write:

```lua 
function onLoad() 
	local deckInZone = findDeckInZone(getObjectFromGUID("######"))
	print(deckInZone.getName()) 
end
```

Then copy/paste the code of the function found in this guide over into your code. Now, when it runs findDeckInZone, it will run that function and return the deck it found.  
  
Again, you WILL need scripting knowledge still to set up and utilize these functions, resolve errors, etc. If you are looking for fully feature-complete code, check the workshop. These are only helper functions.  
  
Alright! Time to begin.  

Find Object within Radius of Position

- **Function:** Locates objects within range of a given point, allows for filtering  
    
- **Takes:** position vector, radius number, filtering function, debug bool  
    
- **Returns:** table with entity references or empty table  
    
- **Example Input:** {0,5,0}, 1, function(o) return o.tag== "Deck" end, true  
    
- **Example Output:** {entity 1, entity2, entity3} (all decks within 1 unit of {0,5,0})

```lua
function findInRadiusBy(pos, radius, func, debug)  
	local radius = (radius or 1)  
	local objList = Physics.cast({  
		origin=pos, direction={0,1,0}, type=2, size={radius,radius,radius},  
		max_distance=0, debug=(debug or false)  
})  
  
	local refinedList = {}  
	for _, obj in ipairs(objList) do  
		if func == nil then  
			table.insert(refinedList, obj.hit_object)  
		else  
			if func(obj.hit_object) then  
				table.insert(refinedList, obj.hit_object)  
			end  
		end  
	end  
  
	return refinedList  
end
```

func is a function that is used to refine the results. If you don't give it a function, it will skip the refining and return all found objects in that radius. If you add a "true" bool for debug, it will visualize the raycast that takes place (what is finding the objects).  
  
In the example input, function(o) return o.tag== "Deck" end will only return decks found. function(o) return o.tag== "Card" or o.tag== "Deck" end would give you all cards and all decks.

Refine List using Function

- **Function:** Refines a table using a helper function  
    
- **Takes:** table, helper function  
    
- **Returns:** refined table or empty table  
    
- **Example Input:** {"cat", "dog", 5, "10"}, function(o) return type(o)== "string" end  
    
- **Example Output:** {"cat", "dog", "10"}

```lua
function refineTableBy(t, func)  
	if func==nil then error("No func supplied to refineTableBy") end  
	local refinedTable = {}  
	for _, v in ipairs(t) do  
		if func(v) then  
			table.insert(refinedTable, v)  
		end  
	end  
	return refinedTable  
end
```

Very flexible function, can be used to eliminate unwanted entries in a table. This version only works on numerically ordered tables currently.

Create Random Rotation

- **Function:** Creates a randomized rotation vector  
    
- **Takes:** n/a  
    
- **Returns:** vector table (no x/y/z index, only 1/2/3)  
    
- **Example Input:** n/a  
    
- **Example Output:** {random number, random number, random number}

```lua
function randomRotation()  
	--Credit for this function goes to Revinor (forums)  
	--Get 3 random numbers  
	local u1 = math.random()  
	local u2 = math.random()  
	local u3 = math.random()  
	--Convert them into quats to avoid gimbal lock  
	local u1sqrt = math.sqrt(u1)  
	local u1m1sqrt = math.sqrt(1-u1)  
	local qx = u1m1sqrt *math.sin(2*math.pi*u2)  
	local qy = u1m1sqrt *math.cos(2*math.pi*u2)  
	local qz = u1sqrt *math.sin(2*math.pi*u3)  
	local qw = u1sqrt *math.cos(2*math.pi*u3)  
	--Apply rotation  
	local ysqr = qy * qy  
	local t0 = -2.0 * (ysqr + qz * qz) + 1.0  
	local t1 = 2.0 * (qx * qy - qw * qz)  
	local t2 = -2.0 * (qx * qz + qw * qy)  
	local t3 = 2.0 * (qy * qz - qw * qx)  
	local t4 = -2.0 * (qx * qx + ysqr) + 1.0  
	--Correct  
	if t2 > 1.0 then t2 = 1.0 end  
	if t2 < -1.0 then ts = -1.0 end  
	--Convert back to X/Y/Z  
	local xr = math.asin(t2)  
	local yr = math.atan2(t3, t4)  
	local zr = math.atan2(t1, t0)  
	--Return result  
	return {math.deg(xr),math.deg(yr),math.deg(zr)}  
end
```

If you just do random(1,360) three times for X/Y/Z, your rotation is strongly biased towards the y axis poles. This function avoids that issue.

Simple Rounding

- **Function:** Basic rounding function  
    
- **Takes:** number, intiger  
    
- **Returns:** number  
    
- **Example Input:** 5.55555, 3  
    
- **Example Output:** 5.556

```lua
function round(num, dec)  
	local mult = 10^(dec or 0)  
	return math.floor(num * mult + 0.5) / mult  
end
```

If you do not supply an intiger for dec it will default to 0. That means the rounding result will have no decimal places. A dec of 0.1 would round to the tens place.

Shuffle Table

- **Function:** Shuffles a table's contents (randomizing their order)  
    
- **Takes:** table  
    
- **Returns:** table  
    
- **Example Input:** {1,2,3,4,5}  
    
- **Example Output:** {4,2,1,3,5}

```lua
function shuffleTable(tbl)  
	local size = #tbl  
	for i = size, 1, -1 do  
		local rand = math.random(i)  
		tbl[i], tbl[rand] = tbl[rand], tbl[i]  
	end  
	return tbl  
end
```

Will only work with numerically, sequentially numbered indexes.

Compact broadcast utility

- **Function:** Way to shorten broadcasts where you call them  
    
- **Takes:** string message, table color, string player color  
    
- **Returns:** n/a  
    
- **Example Input:** "Hello, World!", {0,1,0}  
    
- **Example Output:** n/a

```lua
function bcast(msg, textColor, playerColor)  
	if playerColor ~= nil then  
		Player[playerColor].broadcast(msg, (textColor or {1,1,1}))  
	else  
		broadcastToAll(msg, (textColor or {1,1,1}))  
	end  
end
```

I use this typically to help organize things at the time I am making broadcasts. If textColor is nil then it broadcasts in white. If playerColor is supplied then it broadcasts just to that color, otherwise it broadcasts to all.

Find a Single Deck/Figurine/Token/Etc in a Zone

- **Function:** Locates a specific type of item in a scripting zone.  
    
- **Takes:** zone entity  
    
- **Returns:** item entity or nil  
    
- **Example Input:** getObjectFromGUID("######")  
    
- **Example Output:** (the reference to the object)

```lua
function findDeckInZone(zone)  
	local objectsInZone = zone.getObjects()  
	for i, object in ipairs(objectsInZone) do  
		if object.tag == "Deck" then  
			return object  
		end  
	end  
	return nil  
end
```

In this example we were looking for an object with the tag of "Deck". You can change that to "Figurine" or whatever else you need. This will only return the first of this type of item found, or nil if none are found.

Find All Decks/Figurines/Tokens/Etc in a Zone

- **Function:** Locates all of a specific type of item in a zone.  
    
- **Takes:** zone entity  
    
- **Returns:** table or nil  
    
- **Example Input:** getObjectFromGUID("######")  
    
- **Example Output:** { (the reference to the object), (the reference to the object) }

```lua
function findDecksInZone(zone)  
	local objectsInZone = zone.getObjects()  
	local decksFound = {}  
	for i, object in ipairs(objectsInZone) do  
		if object.tag == "Deck" then  
			table.insert(decksFound, object)  
		end  
	end  
	if #decksFound > 0 then  
		return decksFound  
	else  
		return nil  
	end  
end
```

In this example we were looking for an object with the tag of "Deck". You can change that to "Figurine" or whatever else you need. This will return all of that object type in a table, or nil if none are found.

Find List of Objects in Radius of a Position (optional tag whitelist)

- **Function:** Finds all items within a radius of a given position. Can be given tags to use to filter results.  
    
- **Takes:** position table, tag string  
    
- **Returns:** table  
    
- **Example Input:** {0,5,0}  
    
- **Example Output:** {object1, object2, object3, etc}

```lua
function getObjectsAtPosition(pos, ...)  
	local tagList = {...}  
	local objList = Physics.cast({  
		origin=pos, direction={0,1,0}, type=2, size={1,1,1},  
		max_distance=0, debug=true  
})  
  
	local foundItems = {}  
	for _, obj in ipairs(objList) do  
		if #tagList == 0 then  
			table.insert(foundItems, obj.hit_object)  
		else  
			for _, tag in ipairs(tagList) do  
				if obj.hit_object.tag == tag then  
					table.insert(foundItems, obj.hit_object)  
					break  
				end  
			end  
		end  
	end  
  
	return foundItems  
end
```

If you use tags as arguments, the ... allows you to include as few or as many as you desire. For example, if you wanted to find all cards and decks at point {0,0,0} you would call getObjectsAtPosition({0,0,0}, "Card", "Deck"). If you called it without "Card" and "Deck" then you would just get every object there instead.

Safely take an object from a container

- **Function:** Returns the object retrieved from the container, or nil if nothing was retrieved  
    
- **Takes:** Object reference, table (takeObject parameters)  
    
- **Returns:** Object reference  
    
- **Example Input:** {container object}, {guid = 'ffffff', position = {0,0,0}}  
    
- **Example Output:** nil

```lua
--perform takeObject only if the object exists in the container  
function takeObjectSafe(container, params)  
	if params.guid ~= nil then  
		for _, item in pairs(container.getObjects()) do  
			if item.guid == params.guid then  
				return container.takeObject(params)  
			end  
		end  
	else  
		return container.takeObject(params)  
	end  
--printToAll("Warning: Object " .. params.guid .. " not found in container. It may have already been removed.", {1,0,0})  
end
```

Using takeObject on a guid that doesn't exist in the bag will cause the script to crash. Use this function to safely try to take the object. Optionally uncomment the error message to inform the players. Remember to check if the result is nil, in which case the callback function will never be called.

Print message to all, but only broadcast to the target player

- **Function:** Print a message to all players, but only broadcast to the target.  
    
- **Takes:** string, table, string  
    
- **Returns:** void  
    
- **Example Input:** "Hello world!", {1,1,1}, "White"  
    
- **Example Output:** void

```lua
function allGameMessage(msg, rgb, target_color)  
	for _, player in ipairs(Player.getPlayers()) do  
		if player.color == target_color then  
			player.broadcast(msg, rgb)  
		else  
			player.print(msg, rgb)  
		end  
	end  
end
```

Get bracketed hex color for rgb

- **Function:** Returns the bracketed hex color code for a color, which can be used to add colors to strings. Can wrap with stringColorToRGB to use with player colors, or any other custom color, so long as it fits the RGB format.  
    
- **Takes:** table (rgb format)  
    
- **Returns:** string  
    
- **Example Input:** stringColorToRGB('White')  
    
- **Example Output:** "[ffffff]"

```lua
function RGBToBracketedHex(rgb)  
	if rgb ~= nil then  
		return "[" .. string.format("%02x%02x%02x", rgb.r*255,rgb.g*255,rgb.b*255) .. "]"  
	else  
		return ""  
	end  
end
```

Order a Table's Elements

- **Function:** Orders table entries based on value.  
    
- **Takes:** table  
    
- **Returns:** table  
    
- **Example Input:** { {color="Red", points=5}, {color="Blue", points=10} }  
    
- **Example Output:** { {color="Blue", points=10}, {color="Red", points=5} }

```lua
function orderTable(t)  
	local sort_func = function( a,b ) return a.points > b.points end  
	table.sort( t, sort_func )  
	return t  
end
```

This is good for ordering players based on score. In this example you feed the function a table filled with other tables. Each sub-table has the player color the score is for and the score. This example orders highest to lowest. Change the > to a < and it will order lowest to highest.

Shuffle a Table's Elements

- **Function:** Randomizes the order of elements in a table, shuffling them.  
    
- **Takes:** table  
    
- **Returns:** table  
    
- **Example Input:** {"first", "second", "third"}  
    
- **Example Output:** {"second", "first", "third"}

```lua
function shuffleTable(t)  
	for i = #t, 2, -1 do  
		local n = math.random(i)  
		t[i], t[n] = t[n], t[i]  
	end  
	return t  
end
```

Checks if a table contains an element

- **Function:** Returns true if the table contains an element, false otherwise  
    
- **Takes:** table, variable  
    
- **Returns:** bool  
    
- **Example Input:** {1, 2, 3, 4, 5}, 3  
    
- **Example Output:** true

```lua
function table.contains(table, element)  
	if type(element) ~= 'table' then  
		for _, value in ipairs(table) do  
			if value == element then  
				return true  
			end  
		end  
	end  
	return false  
end
```

Activate an Asset Bundle Trigger Effect by Name

- **Function:** Activates a trigger effect on an asset bundle.  
    
- **Takes:** object, string  
    
- **Returns:** nothing  
    
- **Example Input:** (object entity of assetbundle), "Some Name  
    
- **Example Output:** -

```lua
function activateTrigger(obj, triggerName)  
	local effectList = local obj.AssetBundle.getTriggerEffects()  
	if #effectList == 0 then  
		print("Error: No trigger effects on this object.")  
	else  
		for i, effect in pairs(effectList) do  
			if effect.name == triggerName then  
				obj.AssetBundle.playTriggerEffect(effect.index)  
				return  
			end  
		end  
		print("Error: No trigger found with that exact name.")  
		return  
	end  
end
```

Pause a coroutine for x seconds

- **Function:** yields a coroutine for any number of seconds  
    
- **Takes:** float  
    
- **Returns:** void  
    
- **Example Input:** 0.25  
    
- **Example Output:** void

```lua
function wait(time)  
local start = os.time()  
repeat coroutine.yield(0) until os.time() > start + time  
end
```

Find Distance Between an Object and a Position

- **Function:** Finds the distance between and object and a position.  
    
- **Takes:** position table, object entity  
    
- **Returns:** distance number  
    
- **Example Input:** {x=5, y=2, z=12}, (object entity)  
    
- **Example Output:** 3.526

```lua
function findProximity(targetPos, object)  
	local objectPos = object.getPosition()  
	local xDistance = math.abs(targetPos.x - objectPos.x)  
	local zDistance = math.abs(targetPos.z - objectPos.z)  
	local distance = xDistance^2 + zDistance^2  
	return math.sqrt(distance)  
end
```

This function handles positions directly from getPosition() without any reformatting. It does not take Y into account (height off table). The number it returns matches those readings you would get from the line tool, except more exact. Special thanks to my good friend Math for help on this one. I find this function particularly useful to locate an object without a scripting zone. For example, if I were trying to find a deck near a certain position, I would use getAllObjects(), check if object.tag == "Deck", then check how far that deck was from the certain position to see if it was the correct deck.  
  
Note: If you are only trying to find the closest object to a position/object and you don't need the exact number, you can skip the math.sqrt operation, since this is very math intensive and will slow down your program for no reason.