local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()
local Window = Library.CreateLib("Swordman Simulator", "GrapeTheme")

local Tab = Window:NewTab("AutoFarm")
local Section = Tab:NewSection("Farm-Strength")

Section:NewToggle("Auto Strength", "Toggle-Auto", function(Value)
_G.Strength = Value
while _G.Strength do wait()
    for i , v in pairs(game:GetService("Players").LocalPlayer.Backpack:GetChildren()) do
if v.ClassName == 'Tool' then
v.Parent = v.Parent.Parent.Character;
end;
end;
local LocalPlayer = game:GetService("Players").LocalPlayer
LocalPlayer.Character:FindFirstChildOfClass("Tool"):Activate()
    end
end)

Section:NewToggle("Auto Rebirth", "Toggle-Auto", function(Value)
_G.Rebirth = Value
while _G.Rebirth do wait()
    local Event = game:GetService("ReplicatedStorage").Rebirth
Event:FireServer()

    end
end)

local Tab = Window:NewTab("BuyEgg")
local Section = Tab:NewSection("Select Eggs!")
Eggs = {}
for i,v in pairs(game:GetService("ReplicatedStorage").Framework2.Modules.Shared.Internal["1 | Directory"].Eggs:GetChildren()) do
    table.insert(Eggs,v.Name) 
end
local drop = Section:NewDropdown("Select Eggs", "Click To Select", Eggs, function(t)
   PlayerTP = t
end)

Section:NewToggle("Auto Buy", "Toggle-Egg", function(t)
_G.Egg = t
while _G.Egg do wait()
    local A_1 = 
{
	[1] = PlayerTP
}
local Event = game:GetService("ReplicatedStorage").Framework2.Modules.Shared.Internal.Modules["2 | Network"].Remotes.openegg
Event:InvokeServer(A_1)

end
end)

local Tab = Window:NewTab("Portal")
local Section = Tab:NewSection("Select Portal! [But Forest] Bug!")

Eggs = {}
for i,v in pairs(workspace.__MAP.__WORLDS:GetChildren()) do
    table.insert(Eggs,v.Name) 
end

local drop = Section:NewDropdown("Select Teleport", "Click To Select", Eggs, function(t)
   PlayerTP = t
end)

Section:NewButton("Tp", "ButtonInfo", function(t)
    for i,v in pairs(workspace.__MAP.__WORLDS:GetDescendants()) do
if v.Name == PlayerTP then
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.CFrame
end
end
end)

Section:NewButton("Tp [Spawn]", "ButtonInfo", function()
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(576.59729, 552.520569, 41.753334, 0.71486485, 8.6472367e-09, -0.699262679, 3.83284657e-08, 1, 5.15498826e-08, 0.699262679, -6.36528625e-08, 0.71486485)
end)

local Tab = Window:NewTab("Ui")
local Section = Tab:NewSection("Ui-ON/OFF")

Section:NewKeybind("On/Off-Ui", "KeybindInfo-Ui", Enum.KeyCode.F, function()
	Library:ToggleUI()
end)

repeat wait() until game:IsLoaded()
game:GetService("Players").LocalPlayer.Idled:connect(function()
game:GetService("VirtualUser"):ClickButton2(Vector2.new())
end)
