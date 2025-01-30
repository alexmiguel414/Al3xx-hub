-- ESP Script para Roblox
local players = game:GetService("Players")
local runService = game:GetService("RunService")
local localPlayer = players.LocalPlayer
local camera = workspace.CurrentCamera

function createESP(player)
    local highlight = Instance.new("Highlight")
    highlight.Adornee = player.Character
    highlight.Parent = player.Character
    highlight.FillColor = Color3.fromRGB(255, 0, 0)
    highlight.FillTransparency = 0.5
    highlight.OutlineColor = Color3.fromRGB(0, 0, 0)
    highlight.OutlineTransparency = 0.1
end

runService.RenderStepped:Connect(function()
    for _, player in pairs(players:GetPlayers()) do
        if player ~= localPlayer and player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
            if not player.Character:FindFirstChild("Highlight") then
                createESP(player)
            end
        end
    end
end)
