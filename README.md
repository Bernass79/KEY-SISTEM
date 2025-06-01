-- Lista de nicks permitidos (whitelist)
local Whitelist = {
    "malucodemeiatigela7",
    "Davmbr21",
     "x",
     "x",
     "x",
     ".",
}
-- Função para verificar se o jogador está na whitelist
local function CheckWhitelist(player)
    for _, name in pairs(Whitelist) do
        if player.Name == name then
            return true
        end
    end
    return false
end

-- Evento para novos jogadores que entram
game.Players.PlayerAdded:Connect(function(player)
    if not CheckWhitelist(player) then
        player:Kick("Player não está na whitelist")
    end
end)

-- Verifica jogadores já no servidor quando o script inicia
for _, player in pairs(game.Players:GetPlayers()) do
    if not CheckWhitelist(player) then
        player:Kick("Player não está na whitelist")
    end
end
