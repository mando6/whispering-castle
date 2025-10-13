```lua
-- TTRPG Battle Simulator

-- Define the different factions and their units
local factions = {
  ["Humans"] = {
    "Knight", "Archer", "Mage"
  },
  ["Orcs"] = {
    "Orc Warrior", "Orc Shaman", "Orc Warg"
  },
  ["Elves"] = {
    "Elf Ranger", "Elf Mage", "Elf Druid"
  }
}

-- Define the rules for each unit
local unit_rules = {
  ["Knight"] = {
    health = 100, attack = 20, defense = 15
  },
  ["Archer"] = {
    health = 80, attack = 15, defense = 10
  },
  ["Mage"] = {
    health = 70, attack = 25, defense = 5
  },
  ["Orc Warrior"] = {
    health = 120, attack = 18, defense = 12
  },
  ["Orc Shaman"] = {
    health = 90, attack = 22, defense = 8
  },
  ["Orc Warg"] = {
    health = 150, attack = 22, defense = 15
  },
  ["Elf Ranger"] = {
    health = 90, attack = 18, defense = 12
  },
  ["Elf Mage"] = {
    health = 80, attack = 25, defense = 5
  },
  ["Elf Druid"] = {
    health = 100, attack = 15, defense = 15
  }
}

-- Function to simulate a battle between two units
local function simulate_battle(unit1, unit2)
  local unit1_health = unit_rules[unit1].health
  local unit2_health = unit_rules[unit2].health

  while unit1_health > 0 and unit2_health > 0 do
    -- Unit 1 attacks Unit 2
    local damage = math.max(unit_rules[unit1].attack - unit_rules[unit2].defense, 1)
    unit2_health = unit2_health - damage
    print(string.format("%s attacks %s, dealing %d damage.", unit1, unit2, damage))

    -- Unit 2 attacks Unit 1
    damage = math.max(unit_rules[unit2].attack - unit_rules[unit1].defense, 1)
    unit1_health = unit1_health - damage
    print(string.format("%s attacks %s, dealing %d damage.", unit2, unit1, damage))
  end

  if unit1_health <= 0 then
    return unit2
  else
    return unit1
  end
end

-- Function to simulate a battle between two factions
local function simulate_faction_battle(faction1, faction2)
  local faction1_units = factions[faction1]
  local faction2_units = factions[faction2]

  local faction1_wins = 0
  local faction2_wins = 0

  for i = 1, math.max(#faction1_units, #faction2_units) do
    local unit1 = faction1_units[i] or faction1_units[1]
    local unit2 = faction2_units[i] or faction2_units[1]

    local winner = simulate_battle(unit1, unit2)
    if winner == unit1 then
      faction1_wins = faction1_wins + 1
    else
      faction2_wins = faction2_wins + 1
    end
  end

  if faction1_wins > faction2_wins then
    return faction1
  else
    return faction2
  end
end

-- Example usage
local winning_faction = simulate_faction_battle("Humans", "Orcs")
print("The winning faction is: " .. winning_faction)
```

Explanation:

1. The code defines the different factions and their units in the `factions` table.
2. The `unit_rules` table defines the health, attack, and defense values for each unit.
3. The `simulate_battle` function takes two units and simulates a battle between them, returning the winner.
4. The `simulate_faction_battle` function takes two factions and simulates a battle between them, returning the winning faction.
5. The example usage at the end demonstrates how to use the `simulate_faction_battle` function to determine the winning faction between "Humans" and "Orcs".

This is a basic implementation, and you can further expand on it by adding more features, such as special abilities, item/equipment management, and more complex battle mechanics.