<img src="Assets/logodark.png#gh-dark-mode-only" alt="fluent">
<img src="Assets/logolight.png#gh-light-mode-only" alt="fluent">

## ⚡ Features

- Modern design
- Many customization options
- Almost any UI Element you would ever need 
<br/>

## Creating Library
```lua
local Fluent = loadstring(game:HttpGet(('https://raw.githubusercontent.com/Nevcit/UI-Library/Loadstring/FluentLib')))()
```

## Creating Window
```lua
local Window = Fluent:CreateWindow({
    Title = "Fluent " .. Fluent.Version,
    SubTitle = "by dawid",
    TabWidth = 160,
    Size = UDim2.fromOffset(580, 460),
    Acrylic = true, -- The blur may be detectable, setting this to false disables blur entirely
    Theme = "Dark",
    MinimizeKey = Enum.KeyCode.LeftControl -- Used when theres no MinimizeKeybind
})
```

## Creating Options
```lua
local Options = Fluent.Options
```

## Creating Notifications
```lua
Fluent:Notify({
        Title = "Notification",
        Content = "This is a notification",
        SubContent = "SubContent", -- Optional
        Duration = 5 -- Set to nil to make the notification not disappear
})
```

## Creating Dialogs
```lua
Window:Dialog({
    Title = "Title",
    Content = "This is a dialog",
    Buttons = {
        { 
            Title = "Confirm",
            Callback = function()
                print("Confirmed the dialog.")
            end 
        }, {
            Title = "Cancel",
            Callback = function()
                print("Cancelled the dialog.")
            end 
        }
    }
})
```

## Creating Tabs
```lua
-- Fluent provides Lucide Icons, they are optional
local Tabs = {
    Main = Window:AddTab({ Title = "Main", Icon = "" }),
    Settings = Window:AddTab({ Title = "Settings", Icon = "settings" })
}
})
```

## Interface and Configs
```lua
local SaveManager = loadstring(game:HttpGet("https://raw.githubusercontent.com/dawid-scripts/Fluent/master/Addons/SaveManager.lua"))()
local InterfaceManager = loadstring(game:HttpGet("https://raw.githubusercontent.com/dawid-scripts/Fluent/master/Addons/InterfaceManager.lua"))()

SaveManager:SetLibrary(Fluent)
InterfaceManager:SetLibrary(Fluent)

InterfaceManager:BuildInterfaceSection(Tabs.Settings)
SaveManager:BuildConfigSection(Tabs.Settings)
```

## Selecting Main Tab
```lua
Window:SelectTab(1)
```

## Creating Sections
```lua
local Section = Tabs.Main:AddSection("Section Name")
```

## Creating Section With Paragraph
```lua
local Section = Tabs.Main:AddSection("Section Name")
Section:AddParagraph({
    Title = "Paragraph"
})
```

## Creating Paragraphs
```lua
Tabs.Main:AddParagraph({
    Title = "Paragraph",
    Content = "This is a paragraph.\nSecond line!"
})
```

## Creating Buttons
```lua
Tabs.Main:AddButton({
    Title = "Button",
    Description = "Very important button",
    Callback = function()
        print("Hello, world!")
    end
})
```

## Creating Toogles
```lua
local Toggle = Tabs.Main:AddToggle("MyToggle", 
{
    Title = "Toggle", 
    Description = "Toggle description",
    Default = false,
    Callback = function(state)
	if state then
	    print("Toggle On")
	else
	    print("Toggle Off")
        end
    end 
})
```

## Event Handling Toogle
```lua
Toggle:OnChanged(function()
    print("Toggle changed:", Options.MyToggle.Value)
end)
```

## Changing Value Toogle
```lua
Toggle:SetValue(false)
```

## Creating a Sliders
```lua
local Slider = Tabs.Main:AddSlider("Slider", 
{
    Title = "Slider",
    Description = "This is a slider",
    Default = 2,
    Min = 0,
    Max = 5,
    Rounding = 1,
    Callback = function(Value)
        print("Slider was changed:", Value)
    end
})
```

## Event Handling Slider
```lua
Slider:OnChanged(function(Value)
    print("Slider changed:", Value)
end)
```

## Changing Value Slider
```lua
Slider:SetValue(3)
```

## Creating Dropdowns
```lua
local Dropdown = Tabs.Main:AddDropdown("Dropdown", {
    Title = "Dropdown",
    Description = "Dropdown description",
    Values = {"one", "two", "three", "four", "five", "six", "seven", "eight", "nine", "ten", "eleven", "twelve", "thirteen", "fourteen"},
    Multi = false,
    Default = 1,
})
```
## Event Handling Dropdown
```lua
Dropdown:OnChanged(function(Value)
    print("Dropdown changed:", Value)
end)
```

## Changing Value Dropdown
```lua
Dropdown:SetValue("four")
```

## Creating Multiple Dropdowns
```lua
local MultiDropdown = Tabs.Main:AddDropdown("MultiDropdown", {
   Title = "Dropdown",
   Description = "You can select multiple values.",
   Values = {"one", "two", "three", "four", "five", "six", "seven", "eight", "nine", "ten", "eleven", "twelve", "thirteen", "fourteen"},
   Multi = true,
   Default = {"seven", "twelve"},
})
```

## Event Handling Multiple Dropdown
```lua
MultiDropdown:OnChanged(function(Value)
    local Values = {}
    for Value, State in next, Value do
        table.insert(Values, Value)
    end
    print("Mutlidropdown changed:", table.concat(Values, ", "))
end)
```

## Changing Value Multiple Dropdown
```lua
MultiDropdown:SetValue({
   three = true,
   five = true,
   seven = false
})
```

## Creating a Color Picker
```lua
local Colorpicker = Tabs.Main:AddColorpicker("Colorpicker", {
    Title = "Colorpicker",
    Description = "Description for colorpicker",
    Default = Color3.fromRGB(96, 205, 255)
})

Colorpicker:OnChanged(function()
    print("Colorpicker changed:", Colorpicker.Value)
end)
    
Colorpicker:SetValueRGB(Color3.fromRGB(0, 255, 140))
```

## Event Handling Colorpicker
```lua
Colorpicker:OnChanged(function()
    print("Colorpicker changed:", Colorpicker.Value)
end)
```

## Changing Value Colorpicker
```lua
Colorpicker:SetValueRGB(Color3.fromRGB(0, 255, 140))
```

## Transparency Colorpicker
```
local TColorpicker = Tabs.Main:AddColorpicker("TransparencyColorpicker", {
    Title = "Colorpicker",
    Description = "but you can change the transparency.",
    Transparency = 0,
    Default = Color3.fromRGB(96, 205, 255)
})
```

## Event Handling Transparency Colorpicker
```lua
TColorpicker:OnChanged(function()
    print(
        "TColorpicker changed:", TColorpicker.Value,
        "Transparency:", TColorpicker.Transparency
    )
end)
```

## Changing Value Transparency Colorpicker
```lua
TColorpicker:SetValue({0, 100, 100}, 0.5) -- hsv, transparency
```

## Creating Keybinds
```lua
local Keybind = Tabs.Main:AddKeybind("Keybind", {
    Title = "Keybind",
    Description = "Keybind Description",
    Mode = "Toggle", -- Always, Toggle, Hold
    Default = "LeftControl", -- String as the name of the keybind (MB1, MB2 for mouse buttons)

    -- Occurs when the keybind is clicked, Value is `true`/`false`
    Callback = function(Value)
        print("Keybind clicked!", Value)
    end,

    -- Occurs when the keybind itself is changed, `New` is a KeyCode Enum OR a UserInputType Enum
    ChangedCallback = function(New)
        print("Keybind changed!", New)
    end
})
```

## Event Handling Keybind
```lua
-- OnClick is only fired when you press the keybind and the mode is Toggle
-- Otherwise, you will have to use Keybind:GetState()
Keybind:OnClick(function()
    print("Keybind clicked:", Keybind:GetState())
end)

Keybind:OnChanged(function()
    print("Keybind changed:", Keybind.Value)
end)

task.spawn(function()
    while true do
        wait(1)
        -- example for checking if a keybind is being pressed
        local state = Keybind:GetState()
        if state then
            print("Keybind is being held down")
        end

        if Fluent.Unloaded then break end
    end
end)
```

## Changing Value Keybind
```lua
Keybind:SetValue("MB2", "Toggle") -- Sets keybind to MB2, mode to Hold
```

## Creating Inputs
```lua
local Input = Tabs.Main:AddInput("Input", {
    Title = "Input",
    Description = "Input Description",
    Default = "Default",
    Placeholder = "Placeholder",
    Numeric = false, -- Only allows numbers
    Finished = false, -- Only calls callback when you press enter
    Callback = function(Value)
        print("Input changed:", Value)
    end
})
```

## Event Handling Input
```lua
Input:OnChanged(function()
    print("Input updated:", Input.Value)
end)
```

## Changing Value Input
```lua
Input:SetValue("Text")
```

## Toogle Gui Transparency
```lua
Fluent:ToggleTransparency(false) and Fluent:ToggleTransparency(true)
```

## Toogle Arcylic (Blur)
```lua
Fluent:ToggleAcrylic(false) or Fluent:ToggleAcrylic(true)
```

## Destroy Gui
```lua
Fluent:Destroy()
```
