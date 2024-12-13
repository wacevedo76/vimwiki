# Lua for Neovim - General language notes

## Syntax
### Comments
| Purpose             | Notes                                         |
| -------             | -----                                         |
| Single line comment | `-- text`                                     |
| Multi line comment  | `--[[ this comment can span mutiple lines ]]` |

## Variables
### Literals
| Purpose              | Notes                                                     |
| -------              | -----                                                     |
| local number         | `local number = 5`                                        |
| local string         | `local string = "Hello World"`                            |
| multi line construct | `local multi_line = [[ this is a a multi line literal ]]` |
| local boolean        | `local truth, lies = true, false`                         |
| local nil            | `local nothing = nil`                                     |

## Functions
* **Defind local function:**  
    `local function hello(name)`<br>
      `print("Hello!", name)`<br>
    `end`

* **Define function expression:**  
  `local func_expression = function(name)`<br>
  `  print("Hello " .. name .. "!")`<br>
  `end`
<br>

* **Define Higher order function:**  
  `local higher_order = function(value)`<br>
  `   return function(another)`<br>
  `    return value + another`<br>
  `  end`<br>
  `end`

## Data Structures
* Lua effectively has only one data structure.  
  The same structure is used for maps & lists

| Structure type | Format                                                                                                              |
| :------------: | ------                                                                                                              |
| List           | `{ "A list", "contains", 2, 'or more comma separated values', function() print('can also contain functions') end }` |
| Map            | `local t = { literal_key = "a string", ["an expression"] = "also works", [function() end] = true }`                 |

## Control Flow
* Maps and lists are **1 based indexed**, as opposed to other languages which are *0 based indexed*


