# Mohrs Callback functions

## Hvordan bruges det??

### Client side

**Brug et callback:**
```lua
    local args, du, skal, bruge = "Dette ", "Callback ", "Er ", "Måske "
    cCallback:TriggerServerCallback("NavnPåMitCallback", {args, du, skal, bruge}, function(values)
        print(values) -- Values er resultatet fra serverside
    end)
```

### Server side

**Lav et nyt callback:**
```lua
    sCallback:RegisterServerCallback("NavnPåMitCallback", function(args, du, skal, bruge)
        local callbackText = args..du..skal..bruge.."Lavet af Mohr"
        return callbackText
    end)
```

## Med hjælp fra OMikkel

## Yder jeg support - Måske