# OMikkels Callback functions

## Installation

**cCallback.lua**
Skal ligge i toppen af client_scripts i `fxmanifest.lua/__resource.lua`
```lua
client_scripts {
    "cCallback.lua",
    "client.lua"
}
```

**sCallback.lua**
Skal ligge i toppen af server_scripts i `fxmanifest.lua/__resource.lua`
```lua
server_scripts {
    "sCallback.lua",
    "server.lua"
}
```

## Hvordan bruges det??

### Client side

**Modtag info fra server: - A**
```lua
    local args, du, skal, bruge = "Dette ", "Callback ", "Er ", "Måske "
    cCallback:TriggerServerCallback("NavnPåMitCallback", {args, du, skal, bruge}, function(values)
        print(values) -- Values er resultatet fra serverside // Dette Callback Er Måske Lavet af OMikkel
    end)
```

**Send info til server: - B**
```lua
    cCallback:RegisterClientCallback("GetCoords", function()
        local ped = GetPlayerPed(-1)
        local coords = GetEntityCoords(ped, true)
        return coords
    end)
```

### Server side

**Send info til client: - A**
```lua
    sCallback:RegisterServerCallback("NavnPåMitCallback", function(args, du, skal, bruge)
        local callbackText = args..du..skal..bruge.."Lavet af OMikkel"
        return callbackText
    end)
```

**Modtag info fra client: - B**
```lua
    sCallback:TriggerClientCallback(source, "GetCoords", {}, function(coords)
        print(coords) -- vector3(x, y, z)
    end)
```

## I samarbejde med Mohr

## Yder jeg support - Nej
