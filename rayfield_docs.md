Booting the Library
Loading the Rayfield Library
local Rayfield = loadstring(game:HttpGet('https://sirius.menu/rayfield'))()

Enabling Configuration Saving
tip
Enable ConfigurationSaving in the CreateWindow function
Choose an appropiate FileName in the CreateWindow function
Choose an unique flag identifier for each supported element you create
Place Rayfield:LoadConfiguration() at the bottom of all your code
Rayfield will now automatically save and load your configuration

Windows in Rayfield
Creating a Window
local Window = Rayfield:CreateWindow({
   Name = "Rayfield Example Window",
   Icon = 0, -- Icon in Topbar. Can use Lucide Icons (string) or Roblox Image (number). 0 to use no icon (default).
   LoadingTitle = "Rayfield Interface Suite",
   LoadingSubtitle = "by Sirius",
   ShowText = "Rayfield", -- for mobile users to unhide rayfield, change if you'd like
   Theme = "Default", -- Check https://docs.sirius.menu/rayfield/configuration/themes

   ToggleUIKeybind = "K", -- The keybind to toggle the UI visibility (string like "K" or Enum.KeyCode)

   DisableRayfieldPrompts = false,
   DisableBuildWarnings = false, -- Prevents Rayfield from warning when the script has a version mismatch with the interface

   ConfigurationSaving = {
      Enabled = true,
      FolderName = nil, -- Create a custom folder for your hub/game
      FileName = "Big Hub"
   },

   Discord = {
      Enabled = false, -- Prompt the user to join your Discord server if their executor supports it
      Invite = "noinvitelink", -- The Discord invite code, do not include discord.gg/. E.g. discord.gg/ ABCD would be ABCD
      RememberJoins = true -- Set this to false to make them join the discord every time they load it up
   },

   KeySystem = false, -- Set this to true to use our key system
   KeySettings = {
      Title = "Untitled",
      Subtitle = "Key System",
      Note = "No method of obtaining the key is provided", -- Use this to tell the user how to get a key
      FileName = "Key", -- It is recommended to use something unique as other scripts using Rayfield may overwrite your key file
      SaveKey = true, -- The user's key will be saved, but if you change the key, they will be unable to use your script
      GrabKeyFromSite = false, -- If this is true, set Key below to the RAW site you would like Rayfield to get the key from
      Key = {"Hello"} -- List of keys that will be accepted by the system, can be RAW file links (pastebin, github etc) or simple strings ("hello","key22")
   }
})


Creating a Tab
local Tab = Window:CreateTab("Tab Example", 4483362458) -- Title, Image

Lucide Icon Support
You can now also use Lucide Icons with Rayfield. To do so, replace the Image Id above 4483362458 with a string value of an icon name in Lucide Icons.

local Tab = Window:CreateTab("Tab Example", "rewind")

This will set the Tab icon to a rewind symbol from Lucide Icons.

All Lucide Icons Supported Lucide Icons

Credit to Lucide and Latte Softworks

Creating a Section
local Section = Tab:CreateSection("Section Example")

Updating a Section
Section:Set("Section Example")

Creating a Divider
local Divider = Tab:CreateDivider()

Updating a Divider
Divider:Set(false) -- Whether the divider's visibility is to be set to true or false.


Changing the Interface's Visibility
Setting the Visibility
Rayfield:SetVisibility(false)

Getting the Visibility
Rayfield:IsVisible()

Destroying the Interface
Rayfield:Destroy()

Adding interactive elements
Notifying the user
Rayfield:Notify({
   Title = "Notification Title",
   Content = "Notification Content",
   Duration = 6.5,
   Image = 4483362458,
})

Lucide Icon Support
You can now also use Lucide Icons with Rayfield. To do so, replace the Image Id above 4483362458 with a string value of an icon name in Lucide Icons.

Rayfield:Notify({
   Title = "Notification Title",
   Content = "Notification Content",
   Duration = 6.5,
   Image = "rewind",
})

This will set the icon to a rewind symbol from Lucide Icons.

All Lucide Icons Supported Lucide Icons

Credit to Lucide and Latte Softworks

Creating a Button
local Button = Tab:CreateButton({
   Name = "Button Example",
   Callback = function()
   -- The function that takes place when the button is pressed
   end,
})

Updating a Button
Button:Set("Button Example")

Creating a Toggle
local Toggle = Tab:CreateToggle({
   Name = "Toggle Example",
   CurrentValue = false,
   Flag = "Toggle1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(Value)
   -- The function that takes place when the toggle is pressed
   -- The variable (Value) is a boolean on whether the toggle is true or false
   end,
})


Updating a Toggle
Toggle:Set(false)

Creating a Color Picker
local ColorPicker = Tab:CreateColorPicker({
    Name = "Color Picker",
    Color = Color3.fromRGB(255,255,255),
    Flag = "ColorPicker1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
    Callback = function(Value)
        -- The function that takes place every time the color picker is moved/changed
        -- The variable (Value) is a Color3fromRGB value based on which color is selected
    end
})


Updating a Color Picker
ColorPicker:Set(Color3.fromRGB(255,255,255)

Creating a Slider
local Slider = Tab:CreateSlider({
   Name = "Slider Example",
   Range = {0, 100},
   Increment = 10,
   Suffix = "Bananas",
   CurrentValue = 10,
   Flag = "Slider1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(Value)
   -- The function that takes place when the slider changes
   -- The variable (Value) is a number which correlates to the value the slider is currently at
   end,
})


Updating a Slider
Slider:Set(10) -- The new slider integer value

Creating an Adaptive Input (TextBox)
local Input = Tab:CreateInput({
   Name = "Input Example",
   CurrentValue = "",
   PlaceholderText = "Input Placeholder",
   RemoveTextAfterFocusLost = false,
   Flag = "Input1",
   Callback = function(Text)
   -- The function that takes place when the input is changed
   -- The variable (Text) is a string for the value in the text box
   end,
})

Updating a an Adaptive Input (TextBox)
Input:Set("New Text") -- The new input text value

Creating a Dropdown menu
local Dropdown = Tab:CreateDropdown({
   Name = "Dropdown Example",
   Options = {"Option 1","Option 2"},
   CurrentOption = {"Option 1"},
   MultipleOptions = false,
   Flag = "Dropdown1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(Options)
   -- The function that takes place when the selected option is changed
   -- The variable (Options) is a table of strings for the current selected options
   end,
})


Updating a Dropdown
You can update the dropdown's option list using Dropdown:Refresh().

Dropdown:Refresh({"New Option 1","New Option 2"}) -- The new list of options

Set the dropdown's currently selecton option(s) using Dropdown:Set(). The option table can include multiple strings if you set MultipleOptions to true when creating the dropdown.

Dropdown:Set({"Option 2"}) -- "Option 2" will now be selected

note
The dropdown's callback function is called when you use the Dropdown:Set() method.

Check the value of an existing element
To check the value of an existing element, use ElementName.CurrentValue. If the element is a keybind or a dropdown, you need to use KeybindName.CurrentKeybind or DropdownName.CurrentOption respectively. You can also check it via the flags from Rayfield.Flags.

Binding keys in Rayfield
Creating a Keybind
local Keybind = Tab:CreateKeybind({
   Name = "Keybind Example",
   CurrentKeybind = "Q",
   HoldToInteract = false,
   Flag = "Keybind1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(Keybind)
   -- The function that takes place when the keybind is pressed
   -- The variable (Keybind) is a boolean for whether the keybind is being held or not (HoldToInteract needs to be true)
   end,
})


Updating a Keybind
Keybind:Set("RightCtrl") -- Keybind (string)

Textual elements in Rayfield
Creating a Label
local Label = Tab:CreateLabel("Label Example", 4483362458, Color3.fromRGB(255, 255, 255), false) -- Title, Icon, Color, IgnoreTheme


Lucide Icon Support
You can now also use Lucide Icons with Rayfield. To do so, replace the Image Id above 4483362458 with a string value of an icon name in Lucide Icons.

local Label = Tab:CreateLabel("Label Example", "rewind")

This will set the icon to a rewind symbol from Lucide Icons.

All Lucide Icons Supported Lucide Icons

Credit to Lucide and Latte Softworks

Updating a Label
Label:Set("Label Example", 4483362458, Color3.fromRGB(255, 255, 255), false) -- Title, Icon, Color, IgnoreTheme


Creating a Paragraph
local Paragraph = Tab:CreateParagraph({Title = "Paragraph Example", Content = "Paragraph Example"})


Updating a Paragraph
Paragraph:Set({Title = "Paragraph Example", Content = "Paragraph Example"})