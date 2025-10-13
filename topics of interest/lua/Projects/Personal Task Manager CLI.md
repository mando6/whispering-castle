**What you'll learn:**

- File I/O operations
- Table manipulation
- Object-oriented programming in Lua
- String parsing and pattern matching
- JSON encoding/decoding
- CLI interface design
- Error handling

## 📋 Setup Instructions

1. **Install Lua** (if not already installed):
    - macOS: `brew install lua`
    - Ubuntu/Debian: `sudo apt-get install lua5.3`
    - Windows: Download from lua.org
2. **Install JSON library** (using LuaRocks):

```bash
luarocks install dkjson
```

- **Save the code** as `task_manager.lua`
- **Run it**:

```bash
lua task_manager.lua
```

🚀 How to Use

```text
task> add "Learn Lua basics" high
task> add "Build a project" medium
task> list
task> complete 1
task> stats
task> help
```

## 📚 Learning Path

**Phase 1: Understand the basics**

- Study how tables work as objects
- Understand metatables (`__index`)
- Learn file I/O (`io.open`, `read`, `write`)

**Phase 2: Extend the project**

- Add due dates to tasks
- Implement search functionality
- Add task categories/tags
- Sort tasks by priority or date

**Phase 3: Advanced features**

- Add recurring tasks
- Export tasks to CSV
- Add color output (using ANSI codes)
- Create task reminders

## 💡 Challenge Ideas

1. **Add subtasks** - Let tasks have sub-items
2. **Time tracking** - Track how long tasks take
3. **Data visualization** - Show productivity charts
4. **Multi-user support** - Different task lists per user
5. **Web interface** - Connect it to a simple web UI

This project is perfect for learning because it's:

- ✅ Immediately useful in your daily life
- ✅ Covers most Lua fundamentals
- ✅ Easy to extend with new features
- ✅ Teaches practical programming patterns

# **PART 1: Setup & Configuration** 📦
```lua
local json = require("json")
local TASKS_FILE = "tasks.json"
```

**What's happening:**

- `require()` loads external code libraries (like `import` in Python)
- `local` means the variable is only visible in this file (good practice!)
- We're defining where to save tasks - a JSON file on your computer

---

## **PART 2: Creating the TaskManager "Class"** 🏗️
```lua
local TaskManager = {}
TaskManager.__index = TaskManager
```

**What's happening:**

- Lua doesn't have classes, but we can simulate them with **tables** and **metatables**
- `TaskManager = {}` creates an empty table to hold our "class" methods
- `__index = TaskManager` is metatable magic that enables object-oriented programming

**Think of it like:** Creating a blueprint for our task manager

---

## **PART 3: Constructor Function** 🎬
```lua
function TaskManager.new()
    local self = setmetatable({}, TaskManager)
    self.tasks = {}
    self:load()
    return self
end
```

**What's happening step-by-step:**

1. `local self = setmetatable({}, TaskManager)` - Creates a new object with TaskManager as its "parent"
2. `self.tasks = {}` - Gives the object an empty list to hold tasks
3. `self:load()` - Loads existing tasks from file (the `:` syntax is syntactic sugar)
4. `return self` - Returns the newly created object

**Equivalent to:** Python's `__init__` or JavaScript's constructor

# **PART 4: Load Function** 💾
```lua
function TaskManager:load()
    local file = io.open(TASKS_FILE, "r")
    if file then
        local content = file:read("*a")
        file:close()
        if content and content ~= "" then
            self.tasks = json.decode(content) or {}
        end
    end
end
```

**Breaking it down:**

1. `io.open(TASKS_FILE, "r")` - Opens file for **r**eading (returns `nil` if doesn't exist)
2. `if file then` - Only proceed if file exists
3. `file:read("*a")` - Read **a**ll content as a string
4. `file:close()` - Always close files! (prevents memory leaks)
5. `json.decode(content)` - Convert JSON text to Lua table
6. `or {}` - If decoding fails, use empty table as fallback

**Why the checks?** First run won't have a file yet - we handle that gracefully!

---

## **PART 5: Save Function** 💾
```lua
function TaskManager:save()
    local file = io.open(TASKS_FILE, "w")
    if file then
        file:write(json.encode(self.tasks))
        file:close()
        return true
    end
    return false
end
```

**Breaking it down:**

1. `io.open(TASKS_FILE, "w")` - Opens file for **w**riting (creates if doesn't exist)
2. `json.encode(self.tasks)` - Converts Lua table to JSON string
3. `file:write()` - Writes the JSON to file
4. `return true/false` - Tells caller if save succeeded

---

## **PART 6: Add Function** ➕
```lua
function TaskManager:add(description, priority)
    priority = priority or "medium"  -- Default value trick
    local task = {
        id = #self.tasks + 1,        -- # gets table length
        description = description,
        priority = priority,
        completed = false,
        created = os.time(),          -- Current timestamp
        completed_at = nil
    }
    table.insert(self.tasks, task)   -- Add to end of array
    self:save()
    return task.id
end
```

**Breaking it down:**

1. `priority = priority or "medium"` - **Lua idiom**: if priority is nil, use "medium"
2. Creates a **task table** with all properties
3. `#self.tasks` - The `#` operator gets array length (number of tasks)
4. `os.time()` - Gets current Unix timestamp
5. `table.insert()` - Lua's built-in function to add to arrays
6. Saves immediately so data persists

## **Task structure:**
```lua
{
  id = 1,
  description = "Learn Lua",
  priority = "high",
  completed = false,
  created = 1696608000,
  completed_at = nil
}
```

# **PART 7: List Function** 📋
```lua
function TaskManager:list(filter)
    filter = filter or "all"
    
    print("\n" .. string.rep("=", 70))  -- Print 70 equal signs
    print(string.format("%-5s %-10s %-40s %-10s", "ID", "Status", "Description", "Priority"))
    print(string.rep("=", 70))
    
    for _, task in ipairs(self.tasks) do
        local show = false
        if filter == "all" then
            show = true
        elseif filter == "pending" and not task.completed then
            show = true
        elseif filter == "completed" and task.completed then
            show = true
        end
        
        if show then
            local status = task.completed and "[✓]" or "[ ]"
            local desc = task.description
            if #desc > 40 then
                desc = string.sub(desc, 1, 37) .. "..."
            end
            print(string.format("%-5d %-10s %-40s %-10s", 
                task.id, status, desc, task.priority))
        end
    end
    print(string.rep("=", 70) .. "\n")
end
```

**Breaking it down:**

**String operations:**

- `string.rep("=", 70)` - Repeat "=" 70 times (makes a line)
- `string.format("%-5s", value)` - Format string, left-aligned in 5 character width
- `..` - String concatenation operator
- `string.sub(desc, 1, 37)` - Get substring from position 1 to 37

**Loop:**

- `for _, task in ipairs(self.tasks)` - Loop through array
- `_` means "I don't need this variable" (it would be the index)
- `ipairs` is for arrays (vs `pairs` for general tables)

**Conditional operator:**

- `task.completed and "[✓]" or "[ ]"` - Like a ternary operator (condition and value1 or value2)

---

## **PART 8: Complete Function** ✅

```lua
function TaskManager:complete(id)
    for _, task in ipairs(self.tasks) do
        if task.id == id then
            task.completed = true
            task.completed_at = os.time()
            self:save()
            return true
        end
    end
    return false  -- Task not found
end
```

**What's happening:**

1. Loop through all tasks
2. Find the one matching the ID
3. Update its properties
4. Save to file
5. Return success/failure

**Pattern:** Find → Modify → Save → Report

---

## **PART 9: Delete Function** 🗑️

```lua
function TaskManager:delete(id)
    for i, task in ipairs(self.tasks) do
        if task.id == id then
            table.remove(self.tasks, i)  -- Remove by index
            self:save()
            return true
        end
    end
    return false
end
```

**Key difference from complete:**

- We need the **index** (`i`) not just the task
- `table.remove(array, index)` removes item at that position

---

## **PART 10: Stats Function** 📊
```lua
function TaskManager:stats()
    local total = #self.tasks
    local completed = 0
    local by_priority = {high = 0, medium = 0, low = 0}
    
    for _, task in ipairs(self.tasks) do
        if task.completed then
            completed = completed + 1
        else
            by_priority[task.priority] = (by_priority[task.priority] or 0) + 1
        end
    end
    
    -- Then prints all the statistics...
end
```

**What's happening:**

1. Initialize counters
2. Loop through all tasks
3. Count completed vs pending
4. Group by priority
5. Calculate percentages
6. Display nicely formatted output

**Lua pattern:** `by_priority[task.priority]` - Tables can be accessed like dictionaries!

---

## **PART 11: Main CLI Interface** 🖥️

```lua
local function main()
    local manager = TaskManager.new()  -- Create our task manager
    print("🎯 Welcome to Task Manager!")
    
    while true do  -- Infinite loop
        io.write("task> ")  -- Prompt (doesn't add newline)
        local input = io.read()  -- Read user input
        
        if not input then break end  -- Handle Ctrl+D
        
        -- Parse command and arguments
        local command, args = input:match("^(%S+)%s*(.*)$")
        command = command or input
        
        -- Handle each command...
    end
end
```

**Breaking it down:**

**Pattern matching:**

```lua
local command, args = input:match("^(%S+)%s*(.*)$")
```

- `^` - Start of string
- `(%S+)` - Capture one or more non-whitespace characters (the command)
- `%s*` - Match zero or more whitespace
- `(.*)` - Capture everything else (the arguments)
- `$` - End of string

**Example:** "add Buy milk high" becomes:

- command = "add"
- args = "Buy milk high"

---

## **PART 12: Command Handling - Add** ➕

```lua
elseif command == "add" then
    local desc, priority = args:match("^\"(.-)\"?%s*(%S*)$")
    if not desc then
        desc, priority = args:match("^(%S+)%s*(%S*)$")
    end
    if desc and desc ~= "" then
        priority = priority ~= "" and priority or "medium"
        local id = manager:add(desc, priority)
        print(string.format("✓ Task #%d added successfully!", id))
    else
        print("❌ Usage: add <description> [priority]")
    end
```

**What's happening:**

1. First pattern tries to match quoted descriptions: `"Buy milk"`
2. If that fails, tries to match single word descriptions: `groceries`
3. Validates we got a description
4. Sets default priority if not provided
5. Calls `manager:add()` to actually add the task
6. Prints confirmation with the new ID

**Handles both:**

- `add "Buy groceries" high`
- `add groceries high`

---

## **PART 13: Command Handling - List** 📋

```lua
elseif command == "list" then
    local filter = args ~= "" and args or "all"
    manager:list(filter)
```

**Simple!**

- Get filter from args (or default to "all")
- Call the list function
---

## **PART 14: Command Handling - Complete & Delete** ✅🗑️

```lua
elseif command == "complete" then
    local id = tonumber(args)  -- Convert string to number
    if id and manager:complete(id) then
        print(string.format("✓ Task #%d marked as completed!", id))
    else
        print("❌ Task not found")
    end
```

**Pattern:**

1. Convert argument to number
2. Try to complete/delete
3. Show success or error message

**Key function:** `tonumber()` converts strings like "5" to actual number 5

---

## **Key Lua Concepts Used** 🔑

1. **Tables are everything** - Arrays, objects, dictionaries all use tables
2. **Metatables** - Enable OOP behavior
3. **Colon syntax** `object:method()` - Automatically passes `self`
4. **Pattern matching** - Lua's version of regex
5. **Multiple returns** - Functions can return multiple values
6. **Truthy/falsy** - Only `nil` and `false` are falsy
7. **String operations** - Built-in string library
8. **File I/O** - io.open, read, write, close
9. **Arrays are 1-indexed** - Unlike most languages!

---

## **Flow of the Program** 🔄

```text
1. Start program
2. Create TaskManager object
3. Load existing tasks from file
4. Enter infinite loop:
   a. Show prompt
   b. Read user input
   c. Parse command
   d. Execute command
   e. Repeat
5. Exit when user types "exit"

```

