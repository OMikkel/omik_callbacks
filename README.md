# OMikkels Callback functions

## Indhold

### [Installation](#installation-1)
### [Hvordan bruges det??](#hvordan-bruges-det-1)

---

## Installation

**cCallback.lua**
Skal ligge i toppen af client_scripts i `fxmanifest.lua/__resource.lua`
<details>
<summary>Eksempel</summary>
    
    ```lua
    client_scripts {
        "cCallback.lua",
        "client.lua"
    }
    ```

</details>


**sCallback.lua**
Skal ligge i toppen af server_scripts i `fxmanifest.lua/__resource.lua`
<details>
<summary>Eksempel</summary>
    
    ```lua
    server_scripts {
        "sCallback.lua",
        "server.lua"
    }
    ```
    
</details>

## Hvordan bruges det??

### Client side

**Modtag info fra server: - `A`**
<details>
<summary>Eksempel</summary>
    
    ```lua
        local args, du, skal, bruge = "Dette ", "Callback ", "Er ", "Måske "
        cCallback:TriggerServerCallback("NavnPåMitCallback", {args, du, skal, bruge}, function(values)
            print(values) -- Values er resultatet fra serverside // Dette Callback Er Måske Lavet af OMikkel
        end)
    ```
    
</details>

**Send info til server: - `B`**
<details>
<summary>Eksempel</summary>
    
    ```lua
        cCallback:RegisterClientCallback("GetCoords", function()
            local ped = GetPlayerPed(-1)
            local coords = GetEntityCoords(ped, true)
            return coords
        end)
    ```
    
</details>

### Server side

**Send info til client: - `A`**
<details>
<summary>Eksempel</summary>
    
    ```lua
        sCallback:RegisterServerCallback("NavnPåMitCallback", function(args, du, skal, bruge)
            local callbackText = args..du..skal..bruge.."Lavet af OMikkel"
            return callbackText
        end)
    ```
    
</details>

**Modtag info fra client: - `B`**
<details>
<summary>Eksempel</summary>
    
    ```lua
        sCallback:TriggerClientCallback(source, "GetCoords", {}, function(coords)
            print(coords) -- vector3(x, y, z)
        end)
    ```
    
</details>

## I samarbejde med Mohr

## Yder jeg support - Nej
