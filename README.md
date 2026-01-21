local Players = game:GetService("Players")
local UIS = game:GetService("UserInputService")
local player = Players.LocalPlayer

local gui = Instance.new("ScreenGui")
gui.Name = "PhantomHub"
gui.ResetOnSpawn = false
gui.Parent = player:WaitForChild("PlayerGui")

local openBtn = Instance.new("Frame", gui)
openBtn.Size = UDim2.new(0, 56, 0, 56)
openBtn.Position = UDim2.new(0.04, 0, 0.45, 0)
openBtn.BackgroundColor3 = Color3.fromRGB(15,15,15)
openBtn.BackgroundTransparency = 0.15
openBtn.BorderSizePixel = 0
openBtn.Active = true

Instance.new("UICorner", openBtn).CornerRadius = UDim.new(1,0)

local openTxt = Instance.new("TextButton", openBtn)
openTxt.Size = UDim2.new(1,0,1,0)
openTxt.Text = "P"
openTxt.Font = Enum.Font.GothamBold
openTxt.TextScaled = true
openTxt.TextColor3 = Color3.fromRGB(170,0,255)
openTxt.BackgroundTransparency = 1

local main = Instance.new("Frame", gui)
main.Size = UDim2.new(0, 460, 0, 320)
main.Position = UDim2.new(0.5,-230,0.5,-160)
main.BackgroundColor3 = Color3.fromRGB(12,12,12)
main.BackgroundTransparency = 0.12
main.BorderSizePixel = 0
main.Visible = false
main.Active = true

Instance.new("UICorner", main).CornerRadius = UDim.new(0,18)

local topBar = Instance.new("Frame", main)
topBar.Size = UDim2.new(1,0,0,42)
topBar.BackgroundTransparency = 1
topBar.Active = true

local title = Instance.new("TextLabel", topBar)
title.Size = UDim2.new(1,0,1,0)
title.Text = "Phantom Hub"
title.Font = Enum.Font.GothamBold
title.TextScaled = true
title.TextColor3 = Color3.fromRGB(190,0,255)
title.BackgroundTransparency = 1

local tabs = Instance.new("Frame", main)
tabs.Position = UDim2.new(1,-140,0,42)
tabs.Size = UDim2.new(0,140,1,-42)
tabs.BackgroundTransparency = 1

local farmTab = Instance.new("TextButton", tabs)
farmTab.Size = UDim2.new(1,-10,0,36)
farmTab.Position = UDim2.new(0,5,0,10)
farmTab.Text = "Tab Farming"
farmTab.Font = Enum.Font.Gotham
farmTab.TextScaled = true
farmTab.TextColor3 = Color3.fromRGB(220,220,220)
farmTab.BackgroundColor3 = Color3.fromRGB(25,25,25)
farmTab.BorderSizePixel = 0

Instance.new("UICorner", farmTab).CornerRadius = UDim.new(0,12)

local content = Instance.new("ScrollingFrame", main)
content.Position = UDim2.new(0,15,0,52)
content.Size = UDim2.new(1,-170,1,-70)
content.CanvasSize = UDim2.new(0,0,0,220)
content.ScrollBarImageTransparency = 0.5
content.BackgroundTransparency = 1

local weaponBox = Instance.new("Frame", content)
weaponBox.Size = UDim2.new(1,0,0,40)
weaponBox.BackgroundColor3 = Color3.fromRGB(25,25,25)
weaponBox.BorderSizePixel = 0

Instance.new("UICorner", weaponBox).CornerRadius = UDim.new(0,12)

local weaponTxt = Instance.new("TextLabel", weaponBox)
weaponTxt.Size = UDim2.new(0.7,0,1,0)
weaponTxt.Text = "Select Weapon"
weaponTxt.Font = Enum.Font.Gotham
weaponTxt.TextScaled = true
weaponTxt.TextColor3 = Color3.fromRGB(220,220,220)
weaponTxt.BackgroundTransparency = 1

local weaponBtn = Instance.new("TextButton", weaponBox)
weaponBtn.Size = UDim2.new(0.3,-8,0.7,0)
weaponBtn.Position = UDim2.new(0.7,4,0.15,0)
weaponBtn.Text = "Melee ^"
weaponBtn.Font = Enum.Font.Gotham
weaponBtn.TextScaled = true
weaponBtn.TextColor3 = Color3.fromRGB(170,0,255)
weaponBtn.BackgroundColor3 = Color3.fromRGB(15,15,15)
weaponBtn.BorderSizePixel = 0

Instance.new("UICorner", weaponBtn).CornerRadius = UDim.new(0,10)

local farmBox = Instance.new("Frame", content)
farmBox.Position = UDim2.new(0,0,0,60)
farmBox.Size = UDim2.new(1,0,0,40)
farmBox.BackgroundColor3 = Color3.fromRGB(25,25,25)
farmBox.BorderSizePixel = 0

Instance.new("UICorner", farmBox).CornerRadius = UDim.new(0,12)

local farmTxt = Instance.new("TextLabel", farmBox)
farmTxt.Size = UDim2.new(0.7,0,1,0)
farmTxt.Text = "Auto Farm Level"
farmTxt.Font = Enum.Font.Gotham
farmTxt.TextScaled = true
farmTxt.TextColor3 = Color3.fromRGB(220,220,220)
farmTxt.BackgroundTransparency = 1

local farmToggle = Instance.new("TextButton", farmBox)
farmToggle.Size = UDim2.new(0.3,-8,0.7,0)
farmToggle.Position = UDim2.new(0.7,4,0.15,0)
farmToggle.Text = "OFF"
farmToggle.Font = Enum.Font.GothamBold
farmToggle.TextScaled = true
farmToggle.TextColor3 = Color3.fromRGB(255,80,80)
farmToggle.BackgroundColor3 = Color3.fromRGB(15,15,15)
farmToggle.BorderSizePixel = 0

Instance.new("UICorner", farmToggle).CornerRadius = UDim.new(0,10)

local AutoFarm = false
local SelectedWeapon = "Melee"

farmToggle.MouseButton1Click:Connect(function()
	AutoFarm = not AutoFarm
	farmToggle.Text = AutoFarm and "ON" or "OFF"
	farmToggle.TextColor3 = AutoFarm and Color3.fromRGB(80,255,120) or Color3.fromRGB(255,80,80)

	if AutoFarm then
		-- Aqui entra o sistema de Quest / NPC / Hitbox
		warn("Auto Farm iniciado (lógica será plugada)")
	end
end)

weaponBtn.MouseButton1Click:Connect(function()
	-- Dropdown preparado
	SelectedWeapon = "Melee"
end)

openTxt.MouseButton1Click:Connect(function()
	main.Visible = not main.Visible
end)

do
	local dragging, startPos, startInput
	topBar.InputBegan:Connect(function(i)
		if i.UserInputType == Enum.UserInputType.MouseButton1 or i.UserInputType == Enum.UserInputType.Touch then
			dragging = true
			startInput = i.Position
			startPos = main.Position
		end
	end)

	UIS.InputChanged:Connect(function(i)
		if dragging and (i.UserInputType == Enum.UserInputType.MouseMovement or i.UserInputType == Enum.UserInputType.Touch) then
			local delta = i.Position - startInput
			main.Position = UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X, startPos.Y.Scale, startPos.Y.Offset + delta.Y)
		end
	end)

	UIS.InputEnded:Connect(function(i)
		if i.UserInputType == Enum.UserInputType.MouseButton1 or i.UserInputType == Enum.UserInputType.Touch then
			dragging = false
		end
	end)
end
