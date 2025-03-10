local Players = game:GetService("Players")
setclipboard("https://dsc.gg/get-8-bit")

local function setUnixTime()
    local unixTime = tick()
    getgenv().startTime = unixTime
end

setUnixTime()

if not getgenv().yetexecuted then
    getgenv().yetexecuted = true

    local bindable = Instance.new("BindableFunction")
    function bindable.OnInvoke(buttonPressed)
        if buttonPressed == "Yes" then
            loadstring(game:HttpGet("https://gist.githubusercontent.com/8bits4ya/104b2a4fc2b5d8e3e458904f825471ed/raw/21a563f1f16d4942e5fd5e7f52d75b5ba7fa6d3d/gistfile1.txt"))()
        elseif buttonPressed == "No" then
            print("Ok")
        end
    end

    local success, errorMsg = pcall(function()
        game.StarterGui:SetCore("SendNotification", {
            Title = "Load script ?",
            Text = "Press yes to load",
            Icon = "rbxassetid://135755849962682",
            Duration = 20,
            Callback = bindable,
            Button1 = "Yes",
            Button2 = "No"
        })
    end)

    if not success then
        game.StarterGui:SetCore("SendNotification", {
            Title = "Error",
            Text = "Script is paused..",
            Icon = "rbxassetid://135755849962682",
            Duration = 56
        })

        game.StarterGui:SetCore("SendNotification", {
            Title = "Info",
            Text = "Script is online but cannot connect to server.",
            Icon = "rbxassetid://135755849962682",
            Duration = 56
        })

        wait(30)
        Players.LocalPlayer:Kick("Restart Roblox and try again.")
    end
else
    game.StarterGui:SetCore("SendNotification", {
        Title = "Notification",
        Text = "Already executed...",
        Icon = "rbxassetid://116912659948477",
        Duration = 2
    })

    game.StarterGui:SetCore("SendNotification", {
        Title = "Notification",
        Text = "Wait for it to load or exit game and execute.",
        Icon = "rbxassetid://116912659948477",
        Duration = 15
    })
end
