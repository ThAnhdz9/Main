local Players = game:GetService("Players")

-- Khi có người chơi tham gia, kiểm tra và gửi yêu cầu kết bạn
Players.PlayerAdded:Connect(function(player)
    for _, otherPlayer in pairs(Players:GetPlayers()) do
        if otherPlayer ~= player then
            -- Gửi yêu cầu kết bạn
            player:RequestFriendship(otherPlayer)
        end
    end
end)

-- Khi có người rời đi, cập nhật lại danh sách
Players.PlayerRemoving:Connect(function(leavingPlayer)
    for _, player in pairs(Players:GetPlayers()) do
        if player ~= leavingPlayer then
            player:RequestFriendship(leavingPlayer)
        end
    end
end)
