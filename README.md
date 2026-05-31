local player = game.Players:GetPlayers()[1] -- Exemplo

if player.Character and player.Character:FindFirstChild("Humanoid") then
    player.Character.Humanoid.Health = 0
end
