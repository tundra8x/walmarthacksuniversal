local rs = game:GetService("RunService")
local player = game.Players.LocalPlayer
local lastTime = tick()
local frameCount = 0
local fps = 0

rs.Heartbeat:Connect(function()
	frameCount = frameCount + 1
	if tick() - lastTime >= 1 then
		fps = frameCount
		frameCount = 0
		lastTime = tick()
	end
end)

local debuggui = Instance.new("ScreenGui")
debuggui.Name = "Debug"
debuggui.IgnoreGuiInset = true

local mainFrame = Instance.new("Frame")
mainFrame.Name = "Main"
mainFrame.AnchorPoint = Vector2.new(0.5,0.5)
mainFrame.Position = UDim2.new(0.068, 0,0.922, 0)
mainFrame.Size = UDim2.new(0.126, 0,0.133, 0)
mainFrame.BackgroundColor3 = Color3.fromRGB(28, 28, 28)
mainFrame.BackgroundTransparency = 0
mainFrame.BorderSizePixel = 0

local uistroke_mainframe = Instance.new("UIStroke")
uistroke_mainframe.Name = "UIStroke_MainFrame"
uistroke_mainframe.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
uistroke_mainframe.Color = Color3.fromRGB(44, 104, 183)
uistroke_mainframe.Thickness = 2
uistroke_mainframe.Transparency = 0

local insetFrame = Instance.new("Frame")
insetFrame.Name = "Inset"
insetFrame.AnchorPoint = Vector2.new(0.5,0.5)
insetFrame.Position = UDim2.new(0.5, 0,0.565, 0)
insetFrame.Size = UDim2.new(0.9, 0,0.686, 0)
insetFrame.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
insetFrame.BackgroundTransparency = 0
insetFrame.BorderSizePixel = 0

local uiListLayout = Instance.new("UIListLayout")
uiListLayout.Name = "UIListLayout"
uiListLayout.Padding = UDim.new(0, 5)
uiListLayout.FillDirection = Enum.FillDirection.Vertical
uiListLayout.SortOrder = Enum.SortOrder.LayoutOrder
uiListLayout.Wraps = false
uiListLayout.HorizontalAlignment = Enum.HorizontalAlignment.Center
uiListLayout.HorizontalFlex = Enum.UIFlexAlignment.None
uiListLayout.ItemLineAlignment = Enum.ItemLineAlignment.Automatic
uiListLayout.VerticalAlignment = Enum.VerticalAlignment.Center
uiListLayout.VerticalFlex = Enum.UIFlexAlignment.None

local uistroke_insetframe = Instance.new("UIStroke")
uistroke_insetframe.Name = "UIStroke_InsetFrame"
uistroke_insetframe.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
uistroke_insetframe.Color = Color3.fromRGB(6, 6, 6)
uistroke_insetframe.Thickness = 1
uistroke_insetframe.Transparency = 0

local textLabel_Main = Instance.new("TextLabel")
textLabel_Main.Name = "FPS"
textLabel_Main.AnchorPoint = Vector2.new(0,0)
textLabel_Main.Size = UDim2.new(0.962, 0,0.138, 0)
textLabel_Main.Position = UDim2.new(0.014, 0,0.025, 0)
textLabel_Main.Font = Enum.Font.Code
textLabel_Main.BackgroundTransparency = 1
textLabel_Main.Text = "Debug Menu"
textLabel_Main.TextColor3 = Color3.fromRGB(222, 222, 222)
textLabel_Main.TextScaled = true
textLabel_Main.TextTransparency = 0

local uistroke_textlabel_main = Instance.new("UIStroke")
uistroke_textlabel_main.Name = "UIStroke_TextLabel_Main"
uistroke_textlabel_main.ApplyStrokeMode = Enum.ApplyStrokeMode.Contextual
uistroke_textlabel_main.Color = Color3.fromRGB(4, 4, 4)
uistroke_textlabel_main.Thickness = 1
uistroke_textlabel_main.Transparency = 0

local fpsLabel = Instance.new("TextLabel")
fpsLabel.Name = "FPS"
fpsLabel.AnchorPoint = Vector2.new(0.5,0.5)
fpsLabel.Size = UDim2.new(0.957, 0,0.197, 0)
fpsLabel.Font = Enum.Font.Code
fpsLabel.BackgroundTransparency = 1
fpsLabel.Text = "FPS: "..fps
fpsLabel.TextColor3 = Color3.fromRGB(222, 222, 222)
fpsLabel.TextScaled = true
fpsLabel.TextTransparency = 0

local uistroke_fps = Instance.new("UIStroke")
uistroke_fps.Name = "UIStroke_FPS"
uistroke_fps.ApplyStrokeMode = Enum.ApplyStrokeMode.Contextual
uistroke_fps.Color = Color3.fromRGB(4, 4, 4)
uistroke_fps.Thickness = 1
uistroke_fps.Transparency = 0

local pingLabel = Instance.new("TextLabel")
pingLabel.Name = "PING"
pingLabel.AnchorPoint = Vector2.new(0.5,0.5)
pingLabel.Size = UDim2.new(0.957, 0,0.197, 0)
pingLabel.Font = Enum.Font.Code
pingLabel.BackgroundTransparency = 1
pingLabel.Text = "PING: "..player:GetNetworkPing()
pingLabel.TextColor3 = Color3.fromRGB(222, 222, 222)
pingLabel.TextScaled = true
pingLabel.TextTransparency = 0

local uistroke_ping = Instance.new("UIStroke")
uistroke_ping.Name = "UIStroke_PING"
uistroke_ping.ApplyStrokeMode = Enum.ApplyStrokeMode.Contextual
uistroke_ping.Color = Color3.fromRGB(4, 4, 4)
uistroke_ping.Thickness = 1
uistroke_ping.Transparency = 0

local objectsLabel = Instance.new("TextLabel")
objectsLabel.Name = "OIV"
objectsLabel.AnchorPoint = Vector2.new(0.5,0.5)
objectsLabel.Size = UDim2.new(0.957, 0,0.197, 0)
objectsLabel.Font = Enum.Font.Code
objectsLabel.BackgroundTransparency = 1
objectsLabel.Text = "OBJECTS: "..#workspace:GetDescendants()
objectsLabel.TextColor3 = Color3.fromRGB(222, 222, 222)
objectsLabel.TextScaled = true
objectsLabel.TextTransparency = 0

local uistroke_objects = Instance.new("UIStroke")
uistroke_objects.Name = "UIStroke_OBJECTS"
uistroke_objects.ApplyStrokeMode = Enum.ApplyStrokeMode.Contextual
uistroke_objects.Color = Color3.fromRGB(4, 4, 4)
uistroke_objects.Thickness = 1
uistroke_objects.Transparency = 0

uistroke_objects.Parent = objectsLabel
objectsLabel.Parent = insetFrame
uistroke_ping.Parent = pingLabel
pingLabel.Parent = insetFrame
uistroke_fps.Parent = fpsLabel
fpsLabel.Parent = insetFrame
uiListLayout.Parent = insetFrame
uistroke_insetframe.Parent = insetFrame
insetFrame.Parent = mainFrame
uistroke_textlabel_main.Parent = textLabel_Main
textLabel_Main.Parent = mainFrame
uistroke_mainframe.Parent = mainFrame
mainFrame.Parent = debuggui
debuggui.Parent = player.PlayerGui
