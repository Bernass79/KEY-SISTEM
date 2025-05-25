-- Lista de nicks permitidos (whitelist)
local Whitelist = {
    "Puls3Rid3rNinja2015",
    "Epic_Storm57",
     "XxLuckyBlazeBlastxX",
     "os_drakes00",
     "d",
     "XxJam3sJ3llySt3althx",
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
