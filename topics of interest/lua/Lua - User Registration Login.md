
```lua

-- User class to represent a user with registration and login functionality.
User = {}
User.__index = User

-- This function creates a new User object with the given username and password.
-- @param username: The username of the user.
-- @param password: The password of the user.
-- @return: Returns a new User object.
function User.new(username, password)
    local self = setmetatable({}, User)
    self.username = username
    self.password = password
    return self
end

-- This function registers a new user on the server.
-- @param username: The username of the user.
-- @param password: The password of the user.
-- @return: Returns a new User object representing the registered user.
function register(username, password)
    return User.new(username, password)
end

-- This function logs in a user on the server.
-- @param user: The User object representing the user.
-- @param username: The username of the user.
-- @param password: The password of the user.
-- @return: Returns true if the login is successful, false otherwise.
function login(user, username, password)
    if user.username == username and user.password == password then
        return true
    else
        return false
    end
end

-- Example usage of the User class and functions

-- Usage Example 1: Register a new user
local user1 = register("john", "password123")

-- Usage Example 2: Login with the registered user
local loggedIn = login(user1, "john", "password123")
if loggedIn then
    print("Login successful!")
else
    print("Login failed!")
end

```

