# Lovense.lua
Lovense API wrapper written in Roblox Lua

Unlike other wrappers, this works via control links. Which means you must have internet connection in order to control the toy.
I reversed their web page's communication module and figured out how their private API works. And wrote a wrapper for it cuz why not?

Example usage:
```lua
local Lovense = LovenseSession:new("6-char control code")

if Lovense:Connect() then
  print("Connected")
  for i=0,20 do
    Lovense:Vibrate(i) -- from 0 to 20 (max)
    wait(3)
  end
  Lovense:Vibrate(0) -- stop vibration
  Lovense:Disconnect() -- disconnect
end
```

Possible implementations:

```lua
local Lovense = LovenseSession:new("sfn3m1")

if Lovense:Connect() then
  game.Players.LocalPlayer.Character.Humanoid.Died:Connect(function()
    Lovense:Vibrate(20)
    wait(5)
    Lovense:Vibrate(0)
  end)
end
```
