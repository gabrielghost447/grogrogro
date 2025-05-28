-- Mod Menu GUI para Blade Ball
-- Inclui Kill Aura e Auto Parry
-- Criado para execução em exploits como Arceus X

local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/UI-Libraries/Kavo-UI-Library/main/source.lua"))()
local Window = Library.CreateLib("Blade Ball Mod Menu", "DarkTheme")

local Main = Window:NewTab("Main")
local MainSection = Main:NewSection("Hacks")

-- Variáveis para controle
local killAura = false
local autoParry = false

-- Kill Aura
MainSection:NewToggle("Kill Aura", "Ataca inimigos automaticamente", function(state)
    killAura = state
    while killAura do
        for _, player in pairs(game:GetService("Players"):GetPlayers()) do
            if player ~= game.Players.LocalPlayer then
                local character = player.Character
                if character and character:FindFirstChild("HumanoidRootPart") then
                    game.Players.LocalPlayer.Character:FindFirstChild("HumanoidRootPart").CFrame = character.HumanoidRootPart.CFrame
                    wait(0.1)
                end
            end
        end
        wait(0.2)
    end
end)

-- Auto Parry
MainSection:NewToggle("Auto Parry", "Defende automaticamente", function(state)
    autoParry = state
    while autoParry do
        local args = {
            [1] = "Parry"
        }
        game:GetService("ReplicatedStorage"):FindFirstChild("RemoteEvent"):FireServer(unpack(args))
        wait(0.1)
    end
end)

-- Créditos
local Credits = Window:NewTab("Credits")
local CreditsSection = Credits:NewSection("Gabriel Andreatta") -- script desatualizado
