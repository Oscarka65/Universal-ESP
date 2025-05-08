-- simple ESP for any games that has teams shit. wont work in games where teams are not in GetService:("Players")
-- its quite simple to understand so u can use it for education or smth idk 


local Players = game:GetService("Players")
local player = Players.LocalPlayer
local Teams = game:GetService("Teams")

local SETTINGS = {
    TEXT_SIZE = 18,                               
    TEXT_FONT = Enum.Font.GothamBold,             
    TEXT_OUTLINE = true,                          
    TEXT_OUTLINE_COLOR = Color3.new(0, 0, 0),     
    HIGHLIGHT_ENABLED = true                      
}

local function createNametag(character, playerName, otherPlayer)
    local head = character:WaitForChild("Head")
    
    local billboard = Instance.new("BillboardGui")
    billboard.Adornee = head
    billboard.Size = UDim2.new(0, 200, 0, 50) 
    billboard.StudsOffset = Vector3.new(0, 4, 0)
    billboard.AlwaysOnTop = true
    billboard.Parent = character

    local textLabel = Instance.new("TextLabel")
    textLabel.Size = UDim2.new(1, 0, 1, 0)
    textLabel.BackgroundTransparency = 1
    textLabel.Text = playerName

    if otherPlayer.Team then
        textLabel.TextColor3 = otherPlayer.Team.TeamColor.Color
    else
        textLabel.TextColor3 = Color3.new(0.5,0.5,0.5)
    end

    textLabel.TextSize = SETTINGS.TEXT_SIZE
    textLabel.Font = SETTINGS.TEXT_FONT
    
    if SETTINGS.TEXT_OUTLINE then
        local outline = Instance.new("UIStroke")
        outline.Color = SETTINGS.TEXT_OUTLINE_COLOR
        outline.Thickness = 1.5
        outline.Parent = textLabel
    end
    
    textLabel.Parent = billboard
end

local function highlightPlayer(character, otherPlayer) -- player highlight function no way
    if not SETTINGS.HIGHLIGHT_ENABLED then return end
    
    local highlight = Instance.new("Highlight")
    if otherPlayer.Team then
        highlight.FillColor = otherPlayer.Team.TeamColor.Color
    else
        highlight.FillColor = Color3.new(0.5, 0.5, 0.5)
    end
    highlight.OutlineColor = Color3.new(0, 0, 0)
    highlight.Parent = character
end

local function processPlayer(otherPlayer)
    if otherPlayer == player then return end 
    
    local character = otherPlayer.Character or otherPlayer.CharacterAdded:Wait()


    highlightPlayer(character, otherPlayer)
    createNametag(character, otherPlayer.Name, otherPlayer)
    
    otherPlayer.CharacterAdded:Connect(function(newChar)
        highlightPlayer(newChar, otherPlayer)
        createNametag(newChar, otherPlayer.Name, otherPlayer)
    end)
end

for _, otherPlayer in ipairs(Players:GetPlayers()) do -- check if player respawned
    task.spawn(processPlayer, otherPlayer)
end


local function onTeamChanged(otherPlayer) -- function if player changes team
    if otherPlayer == player then return end
    
    local character = otherPlayer.Character
    if character then

        local head = character:FindFirstChild("Head")
        if head then
            for _, child in ipairs(head:GetChildren()) do
                if child:IsA("BillboardGui") or child:IsA("Highlight") then
                    child:Destroy()
                end
            end
        end
        
        highlightPlayer(character, otherPlayer)
        createNametag(character, otherPlayer.Name, otherPlayer)
    end
end

for _, otherPlayer in ipairs(Players:GetPlayers()) do -- catching signal if someone changes team
    otherPlayer:GetPropertyChangedSignal("Team"):Connect(function()
        onTeamChanged(otherPlayer)
    end)
end


Players.PlayerAdded:Connect(function(newPlayer)
    newPlayer:GetPropertyChangedSignal("Team"):Connect(function()
        onTeamChanged(newPlayer)
    end)
end)

Players.PlayerAdded:Connect(processPlayer) -- if player joins it will work ez
