

```lua
-- Corvo Hub Script para Blox Fruits

local Player = game.Players.LocalPlayer
local Character = Player.Character or Player.CharacterAdded:Wait()

function teleportToLocation(position)
    Character.HumanoidRootPart.CFrame = CFrame.new(position)
end

function giveFruit(fruitName)
    -- Exemplo de como dar uma fruta ao jogador
    local args = {
        [1] = fruitName
    }

    game:GetService("ReplicatedStorage").remote:FireServer(unpack(args))
end

function autoFarm()
    while true do
        wait(2)
        -- Exemplo de Auto Farm: atacar inimigos na área
        for _, enemy in pairs(workspace.Enemies:GetChildren()) do
            if enemy:FindFirstChild("Humanoid") then
                enemy.Humanoid:TakeDamage(9999) -- Causa dano imediato
            end
        end
    end
end

-- Tela de interface do Corvo Hub
local ScreenGui = Instance.new("ScreenGui")
local Button = Instance.new("TextButton")

Button.Parent = ScreenGui
Button.Text = "Teletransportar para a Ilha"
Button.Size = UDim2.new(0, 200, 0, 50)
Button.Position = UDim2.new(0.5, -100, 0.5, -25)
Button.BackgroundColor3 = Color3.new(0.1, 0.1, 0.1)
Button.TextColor3 = Color3.new(1, 1, 1)

Button.MouseButton1Click:Connect(function()
    teleportToLocation(Vector3.new(0, 0, 0)) -- Substitua pela posição desejada
end)

ScreenGui.Parent = game.CoreGui

-- Começar o Auto Farm
autoFarm()
```

