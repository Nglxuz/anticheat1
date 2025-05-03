-- Server-Side (Script no servidor)
game.Players.PlayerAdded:Connect(function(player)
	player.CharacterAdded:Connect(function(character)
		-- Exemplo de verificação se a velocidade do personagem não está além do limite
		local humanoid = character:WaitForChild("Humanoid")
		humanoid:GetPropertyChangedSignal("WalkSpeed"):Connect(function()
			if humanoid.WalkSpeed > 16 then
				humanoid.WalkSpeed = 16  -- Limita a velocidade máxima do jogador
				player:Kick("Você foi expulso por trapaça.")
			end
		end)
	end)
end)
