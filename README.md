-- Xmodded Premium RGB Lento
-- Coloque este LocalScript em StarterPlayerScripts
local Players = game:GetService("Players")
local TweenService = game:GetService("TweenService")
local RunService = game:GetService("RunService")
local player = Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")
-- Função helper
local function new(class, props)
local obj = Instance.new(class)
for k,v in pairs(props) do
obj[k] = v
end
return obj
end
-- // TELA DE CARREGAMENTO
local loadingScreen = new("ScreenGui", {Parent = playerGui, Name = "LoadingUI"})
local frame = new("Frame", {
Parent = loadingScreen,
Size = UDim2.new(1,0,1,0),
BackgroundColor3 = Color3.new(0,0,0)
})
local numberLabel = new("TextLabel", {
Parent = frame,
Size = UDim2.new(0,200,0,100),
Position = UDim2.new(0.5,-100,0.5,-50),
BackgroundTransparency = 1,
Text = "0%",
TextColor3 = Color3.fromRGB(255,0,0),
TextStrokeTransparency = 0,
TextStrokeColor3 = Color3.new(1,1,1),
Font = Enum.Font.FredokaOne,
TextScaled = true
})
local skipButton = new("TextButton", {
Parent = frame,
Size = UDim2.new(0,100,0,40),
Position = UDim2.new(0.5,-50,0.7,0),
Text = "SKIP",
BackgroundColor3 = Color3.fromRGB(255,0,0),
TextColor3 = Color3.new(1,1,1),
TextStrokeTransparency = 0,
TextStrokeColor3 = Color3.new(1,1,1),
Font = Enum.Font.FredokaOne,
TextScaled = true
})
local skipped = false
skipButton.MouseButton1Click:Connect(function()
skipped = true
loadingScreen:Destroy()
end)
task.spawn(function()
for i=0,100 do
if skipped then break end
numberLabel.Text = i.."%"
task.wait(0.05)
end
if not skipped then
loadingScreen:Destroy()
end
end)
-- // INTERFACE PRINCIPAL
local gui = new("ScreenGui", {Parent = playerGui, Name = "XmoddedUI"})
local mainFrame = new("Frame", {
Parent = gui,
Size = UDim2.new(0,250,0,150),
Position = UDim2.new(0,20,0,100),
BackgroundColor3 = Color3.fromRGB(25,25,25),
BorderSizePixel = 0
})
-- Título com RGB lento
local title = new("TextLabel", {
Parent = mainFrame,
Size = UDim2.new(1,0,0,40),
