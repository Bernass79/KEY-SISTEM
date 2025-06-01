-- ID do grupo
local GROUP_ID = 35079880

-- Função para verificar se o jogador está no grupo
local function CheckGroupMembership(player)
    local success, result = pcall(function()
        return player:IsInGroup(GROUP_ID)
    end)
    
    if success then
        return result
    else
        warn("Erro ao verificar associação ao grupo: " .. tostring(result))
        return false -- Retorna false em caso de erro para evitar falsos positivos
    end
end

-- Evento para novos jogadores que entram
game:GetService("Players").PlayerAdded:Connect(function(player)
    if not CheckGroupMembership(player) then
        player:Kick("Você não está no grupo requerido!")
    end
end)

-- Verifica jogadores já no servidor quando o script inicia
for _, player in pairs(game:GetService("Players"):GetPlayers()) do
    if not CheckGroupMembership(player) then
        player:Kick("Você não está no grupo requerido!")
    end
end
