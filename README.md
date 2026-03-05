local Players = game:GetService("Players")

local function addESP(character)
    local highlight = Instance.new("Highlight")
    highlight.FillColor = Color3.fromRGB(255, 0, 0) -- Red fill
    highlight.OutlineColor = Color3.fromRGB(255, 255, 255) -- White outline
    highlight.FillTransparency = 0.5
    highlight.OutlineTransparency = 0
    highlight.Parent = character
end

local function onCharacterAdded(character)
    addESP(character)
end

local function onPlayerAdded(player)
    player.CharacterAdded:Connect(onCharacterAdded)
end

Players.PlayerAdded:Connect(onPlayerAdded)

-- Add ESP to players already in the game
for _, player in pairs(Players:GetPlayers()) do
    if player.Character then
        addESP(player.Character)
    end
    player.CharacterAdded:Connect(onCharacterAdded)
end
