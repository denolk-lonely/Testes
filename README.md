
game.StarterGui:SetCore("SendNotification", {
    Title = "Welcome to Catholic Hub!",
    Text = "Look at the credits in the first tab!",
    Duration = 5,
})

--------------------------------------------------------------------------------------------------------------------------------
loadstring(game:HttpGet("https://pastebin.com/raw/N4xSxRQU"))()

local redzlib = loadstring(game:HttpGet("https://pastefy.app/N6Kn9u0M/raw"))()

local Window = redzlib:MakeWindow({
    Title = "Catholic Hub | Brookhaven RP",
    SubTitle = "by Denolk・Version 1.1 Remade",
    SaveFolder = "catholichubfolder"
  })

  Window:AddMinimizeButton({
    Button = { Image = "rbxassetid://88281998871219", BackgroundTransparency = 0 },
    Corner = { CornerRadius = UDim.new(35, 1) },
})

--------------------------------------------------------------------------------------------------------------------------------
                                                   -- === Tab: credits === --
--------------------------------------------------------------------------------------------------------------------------------
local Tab = Window:MakeTab({"Credits", "info"})
Tab:AddSection({"Hub Credits"})

Tab:AddDiscordInvite({
    Name = "Catholic Hub",
    Description = "Join the hub discord server.",
    Logo = "rbxassetid://98296601157312",
    Invite = "https://discord.gg/hW8vab2wDw",
})

Tab:AddSection({ "User Information" })

local player = game.Players.LocalPlayer

Tab:AddParagraph({ "Username:", player.Name })
Tab:AddParagraph({ "User ID:", tostring(player.UserId) })
Tab:AddParagraph({ "Account Age:", tostring(player.AccountAge) .. " days" })

Tab:AddSection({ "System Information" })

local function detectExecutor()
    if identifyexecutor then
        local exec = identifyexecutor()
        return exec and exec or "Unknown"
    elseif syn then
        return "Synapse X"
    elseif KRNL_LOADED then
        return "KRNL"
    elseif fluxus then
        return "Fluxus"
    else
        return "Unknown Executor"
    end
end

Tab:AddParagraph({ "Executor:", detectExecutor() })
Tab:AddParagraph({ "Game:", "Brookhaven RP" })
Tab:AddParagraph({ "Place ID:", tostring(game.PlaceId) })

Tab:AddSection({ "Server Information" })

local players = game:GetService("Players")
Tab:AddParagraph({ "Online Players:", tostring(#players:GetPlayers()) .. "/" .. tostring(players.MaxPlayers) })
Tab:AddParagraph({ "Server ID:", game.JobId })

local function getTime()
    return os.date("%H:%M:%S")
end

local function getDate()
    return os.date("%d/%m/%Y")
end

Tab:AddSection({ "Time Information" })

Tab:AddParagraph({ "Current Time:", getTime() })
Tab:AddParagraph({ "Current Date:", getDate() })

Tab:AddSection({ "Developer Links" })

Tab:AddButton({
    Name = "Copy TikTok Denolk",
    Callback = function()
        setclipboard("@mrdenolk")
        game.StarterGui:SetCore("SendNotification", {
            Title = "Copied",
            Text = "Username copied!",
            Duration = 3
        })
    end
})

Tab:AddButton({
    Name = "Copy TikTok Link",
    Callback = function()
        setclipboard("https://www.tiktok.com/@mrdenolk")
        game.StarterGui:SetCore("SendNotification", {
            Title = "Copied",
            Text = "Link copied!",
            Duration = 3
        })
    end
})

Tab:AddButton({
    Name = "Copy TikTok Catholic Hub",
    Callback = function()
        setclipboard("@catholic_hub0")
        game.StarterGui:SetCore("SendNotification", {
            Title = "Copied",
            Text = "Username copied!",
            Duration = 3
        })
    end
})

Tab:AddButton({
    Name = "Copy TikTok Link",
    Callback = function()
        setclipboard("https://www.tiktok.com/@catholic_hub0")
        game.StarterGui:SetCore("SendNotification", {
            Title = "Copied",
            Text = "Link copied!",
            Duration = 3
        })
    end
})

Tab:AddSection({ "Development Team" })

Tab:AddParagraph({ "Owner & Sub-Owner:", "Denolk & Assure" })
Tab:AddParagraph({ "Manager & Developer:", "..." })
Tab:AddParagraph({ "Admins:", "DK-GHOST, Cardoso and Shelby" })
Tab:AddParagraph({ "Moderators:", "Nplayboy, PHZIN and Ixi362" })
Tab:AddParagraph({ "Testers:", "..." })

Tab:AddSection({ "Information Script" })

Tab:AddParagraph({ "Name:", "Catholic Hub" })
Tab:AddParagraph({ "Version:", "1.1 Remade" })
Tab:AddParagraph({ "Game:", "Brookhaven RP" })

 ---------------------------------------------------------------------------------------------------------------------------------
                                                   -- === Tab: Local Player === --
-----------------------------------------------------------------------------------------------------------------------------------
local Tab = Window:MakeTab({"Local Player", "User"})
local Section = Tab:AddSection({"Local Player Effects"})

Tab:AddSlider({
    Name = "Player Speed (local)",
    Increase = 1,
    MinValue = 16,
    MaxValue = 1000,
    Default = 16,
    Callback = function(Value)
        local player = game.Players.LocalPlayer
        local character = player.Character or player.CharacterAdded:Wait()
        local humanoid = character:FindFirstChildOfClass("Humanoid")
        
        if humanoid then
            humanoid.WalkSpeed = Value
        end
    end
})
 
Tab:AddSlider({
    Name = "Player Jump (local)",
    Increase = 1,
    MinValue = 50,
    MaxValue = 1000,
    Default = 50,
    Callback = function(Value)
        local player = game.Players.LocalPlayer
        local character = player.Character or player.CharacterAdded:Wait()
        local humanoid = character:FindFirstChildOfClass("Humanoid")
        
        if humanoid then
            humanoid.JumpPower = Value
        end
    end
})
 
Tab:AddSlider({
    Name = "Player Gravity (local)",
    Increase = 1,
    MinValue = 0,
    MaxValue = 1000,
    Default = 196.2,
    Callback = function(Value)
        game.Workspace.Gravity = Value
    end
})
 
---------------------------------------------------------------------------------------------------------------------------------
                                          -- === Tab: Utilities Player === --
---------------------------------------------------------------------------------------------------------------------------------
local Tab = Window:MakeTab({"Utilities Player", "Paint"})
Tab:AddSection({"Esp System"})

local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer

local ESPEnabled = {
    Body = false,
    Name = false,
    Lines = false
}

local SelectedColor = Color3.fromRGB(255, 0, 0)
local RGBMode = false
local ESPObjects = {}
local FontSize = 30

local function clearESP()
    for _, v in pairs(ESPObjects) do
        for _, obj in pairs(v) do
            if obj.Destroy then
                obj:Destroy()
            elseif obj.Remove then
                obj:Remove()
            end
        end
    end
    ESPObjects = {}
end

local function createESP(player)
    if player == LocalPlayer then return end
    local character = player.Character
    if not character then return end

    ESPObjects[player] = {}
    
    if ESPEnabled.Body then
        local highlight = Instance.new("Highlight")
        highlight.FillColor = SelectedColor
        highlight.OutlineColor = SelectedColor
        highlight.FillTransparency = 0.7
        highlight.OutlineTransparency = 0
        highlight.Adornee = character
        highlight.Parent = character
        table.insert(ESPObjects[player], highlight)
    end
    
    if ESPEnabled.Name then
        local billboard = Instance.new("BillboardGui")
        billboard.Size = UDim2.new(0, 200, 0, 50)
        billboard.AlwaysOnTop = true
        billboard.Adornee = character:FindFirstChild("Head")
        billboard.Parent = character

        local label = Instance.new("TextLabel")
        label.Size = UDim2.new(1, 0, 1, 0)
        label.BackgroundTransparency = 1
        label.TextColor3 = SelectedColor
        label.TextStrokeTransparency = 0
        label.Font = Enum.Font.SourceSansBold
        label.TextScaled = false
        label.TextSize = FontSize
        label.Text = player.Name
        label.Parent = billboard

        RunService.RenderStepped:Connect(function()
            if character and character:FindFirstChild("HumanoidRootPart") and LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("HumanoidRootPart") then
                local dist = math.floor((character.HumanoidRootPart.Position - LocalPlayer.Character.HumanoidRootPart.Position).Magnitude)
                label.Text = player.Name .. " (" .. dist .. "m)"
                label.TextSize = FontSize
            end
        end)
        table.insert(ESPObjects[player], billboard)
    end
    
    if ESPEnabled.Lines then
        local line = Drawing.new("Line")
        line.Thickness = 2
        line.Transparency = 1
        line.Color = SelectedColor

        RunService.RenderStepped:Connect(function()
            if not character:FindFirstChild("HumanoidRootPart") or not LocalPlayer.Character:FindFirstChild("HumanoidRootPart") then
                line.Visible = false
                return
            end

            local root = character.HumanoidRootPart
            local localRoot = LocalPlayer.Character.HumanoidRootPart
            local rootPos, onScreen1 = workspace.CurrentCamera:WorldToViewportPoint(root.Position)
            local localPos, onScreen2 = workspace.CurrentCamera:WorldToViewportPoint(localRoot.Position)

            if onScreen1 and onScreen2 then
                line.From = Vector2.new(localPos.X, localPos.Y)
                line.To = Vector2.new(rootPos.X, rootPos.Y)
                line.Color = SelectedColor
                line.Visible = true
            else
                line.Visible = false
            end
        end)
        table.insert(ESPObjects[player], line)
    end
end

local function updateAllESP()
    clearESP()
    for _, player in pairs(Players:GetPlayers()) do
        createESP(player)
    end
end

Players.PlayerAdded:Connect(function(player)
    player.CharacterAdded:Connect(function()
        task.wait(1)
        updateAllESP()
    end)
end)

Players.PlayerRemoving:Connect(function(player)
    if ESPObjects[player] then
        for _, obj in pairs(ESPObjects[player]) do
            if obj.Destroy then
                obj:Destroy()
            elseif obj.Remove then
                obj:Remove()
            end
        end
        ESPObjects[player] = nil
    end
end)

task.spawn(function()
    while task.wait() do
        if RGBMode then
            local t = tick()
            local r = math.abs(math.sin(t * 2)) * 255
            local g = math.abs(math.sin(t * 2 + 2)) * 255
            local b = math.abs(math.sin(t * 2 + 4)) * 255
            SelectedColor = Color3.fromRGB(r, g, b)
            updateAllESP()
        end
    end
end)

local colorList = {
    ["Red"] = Color3.fromRGB(255, 0, 0),
    ["Green"] = Color3.fromRGB(0, 255, 0),
    ["Blue"] = Color3.fromRGB(0, 0, 255),
    ["Yellow"] = Color3.fromRGB(255, 255, 0),
    ["Purple"] = Color3.fromRGB(128, 0, 128),
    ["Cyan"] = Color3.fromRGB(0, 255, 255),
    ["White"] = Color3.fromRGB(255, 255, 255),
    ["Black"] = Color3.fromRGB(0, 0, 0),
    ["Orange"] = Color3.fromRGB(255, 140, 0),
    ["Pink"] = Color3.fromRGB(255, 0, 255),
    ["RGB"] = "RGB"
}

local colorNames = {}
for name in pairs(colorList) do
    table.insert(colorNames, name)
end

Tab:AddDropdown({
    Name = "ESP Color",
    Description = " ",
    Options = colorNames,
    Default = "Red",
    Callback = function(value)
        if colorList[value] == "RGB" then
            RGBMode = true
        else
            RGBMode = false
            SelectedColor = colorList[value]
            updateAllESP()
        end
    end
})

Tab:AddToggle({
    Name = "ESP Body",
    Description = " ",
    Default = false,
    Callback = function(Value)
        ESPEnabled.Body = Value
        updateAllESP()
    end
})

Tab:AddToggle({
    Name = "ESP Name and Distance",
    Description = " ",
    Default = false,
    Callback = function(Value)
        ESPEnabled.Name = Value
        updateAllESP()
    end
})

Tab:AddToggle({
    Name = "ESP Lines",
    Description = " ",
    Default = false,
    Callback = function(Value)
        ESPEnabled.Lines = Value
        updateAllESP()
    end
})

Tab:AddSlider({
    Name = "ESP Text Size",
    Description = " ",
    Min = 1,
    Max = 100,
    Default = 30,
    Callback = function(value)
        FontSize = math.clamp(value, 1, 100)
        updateAllESP()
    end
})

---------------------------------------------------------------------------------------------------------------------------------
local Section = Tab:AddSection({"Name and Bio (VIP FREE)"})

local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer

local rgbSpeed = 1

Tab:AddSlider({
    Name = "Speed RGB/Gradient",
    Description = "",
    Min = 1,
    Max = 5,
    Increment = 1,
    Default = 3,
    Callback = function(Value)
        rgbSpeed = Value
    end
})

local function getRainbowColor(speedMultiplier)
    local h = (tick() * speedMultiplier % 5) / 5
    return Color3.fromHSV(h, 1, 1)
end

local function fireServer(eventName, args)
    local event = game:GetService("ReplicatedStorage"):FindFirstChild("RE")
    if event and event:FindFirstChild(eventName) then
        pcall(function()
            event[eventName]:FireServer(unpack(args))
        end)
    end
end

local colorOptions = {
    "Red",
    "Green",
    "Blue",
    "Yellow",
    "Purple",
    "Orange",
    "Pink",
    "Cyan",
    "White",
    "Black"
}

local colorMap = {
    Red = Color3.fromRGB(255, 0, 0),
    Green = Color3.fromRGB(0, 255, 0),
    Blue = Color3.fromRGB(0, 0, 255),
    Yellow = Color3.fromRGB(255, 255, 0),
    Purple = Color3.fromRGB(128, 0, 128),
    Orange = Color3.fromRGB(255, 165, 0),
    Pink = Color3.fromRGB(255, 192, 203),
    Cyan = Color3.fromRGB(0, 255, 255),
    White = Color3.fromRGB(255, 255, 255),
    Black = Color3.fromRGB(0, 0, 0)
}

local selectedColor1 = "Red"
local selectedColor2 = "Blue"
local gradientActive = false
local gradientThread = nil

Tab:AddDropdown({
    Name = "First Color",
    Description = "",
    Default = "Red",
    Options = colorOptions,
    Callback = function(Value)
        selectedColor1 = Value
    end
})

Tab:AddDropdown({
    Name = "Second Color",
    Description = "",
    Default = "Blue",
    Options = colorOptions,
    Callback = function(Value)
        selectedColor2 = Value
    end
})


local function lerpColor(color1, color2, t)
    t = math.clamp(t, 0, 1)
    return Color3.new(
        color1.R + (color2.R - color1.R) * t,
        color1.G + (color2.G - color1.G) * t,
        color1.B + (color2.B - color1.B) * t
    )
end

Tab:AddToggle({
    Name = "Gradient Name/Bio",
    Default = false,
    Callback = function(state)
        gradientActive = state
        if gradientThread then
            task.cancel(gradientThread)
            gradientThread = nil
        end
        
        if state then
            gradientThread = task.spawn(function()
                while gradientActive and LocalPlayer and LocalPlayer.Character do

                    local color1 = colorMap[selectedColor1]
                    local color2 = colorMap[selectedColor2]
                    
                    local time = tick() * rgbSpeed
                    local t = (math.sin(time) + 1) / 2  -- Varia de 0 a 1 e volta
                    
                    local currentColor = lerpColor(color1, color2, t)
                    
                    fireServer("1RPNam1eColo1r", { "PickingRPNameColor", currentColor })
                    fireServer("1RPNam1eColo1r", { "PickingRPBioColor", currentColor })
                    
                    task.wait(0.03)
                end
            end)
        end
    end
})

local nameBioRGBActive = false
local rainbowThread = nil

Tab:AddToggle({
    Name = "Name + Bio RGB",
    Default = false,
    Callback = function(state)
        nameBioRGBActive = state
        if rainbowThread then
            task.cancel(rainbowThread)
            rainbowThread = nil
        end
        
        if gradientThread then
            task.cancel(gradientThread)
            gradientThread = nil
        end
        
        if state then
            rainbowThread = task.spawn(function()
                while nameBioRGBActive and LocalPlayer.Character do
                    local color = getRainbowColor(rgbSpeed)
                    fireServer("1RPNam1eColo1r", { "PickingRPNameColor", color })
                    fireServer("1RPNam1eColo1r", { "PickingRPBioColor", color })
                    task.wait(0.03)
                end
            end)
        end
    end
})

---------------------------------------------------------------------------------------------------------------------------------
                                          -- === Tab: Car === --
---------------------------------------------------------------------------------------------------------------------------------
local Tab = Window:MakeTab({"Car", "Car"})
local Section = Tab:AddSection({"Motor Controls (Car / Boat / Smaller Vehicles)"})

local speedValue = 200
local turboValue = 11.3
local defaultWalkSpeed = 16

local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer

local function getCharacter()
    return LocalPlayer.Character or LocalPlayer.CharacterAdded:Wait()
end

local function isHorse(model)
    if not model or not model:IsA("Model") then return false end

    local name = model.Name:lower()
    if name:find("horse") or name:find("cavalo") then
        return true
    end

    if model:FindFirstChildWhichIsA("Seat", true)
        or model:FindFirstChildWhichIsA("VehicleSeat", true) then
        return true
    end

    return false
end

local function applyCarSpeed(vehicle)
    local seat = vehicle:FindFirstChild("Seats")
        and vehicle.Seats:FindFirstChildWhichIsA("VehicleSeat")
    if not seat then return end

    pcall(function()
        seat.MaxSpeed = speedValue
    end)

    for _, v in pairs(seat:GetChildren()) do
        if v:IsA("NumberValue") then
            v.Value = speedValue
        end
    end
end

local function applyHorseSpeed(horse)
    local seat = horse:FindFirstChildWhichIsA("Seat", true)
        or horse:FindFirstChildWhichIsA("VehicleSeat", true)
    if not seat then return end

    pcall(function()
        seat.MaxSpeed = speedValue
    end)

    for _, v in pairs(seat:GetChildren()) do
        if v:IsA("NumberValue") then
            v.Value = speedValue
        end
    end

    if horse.PrimaryPart then
        horse.PrimaryPart.AssemblyLinearVelocity =
            horse.PrimaryPart.CFrame.LookVector * speedValue
    end
end

local function applyCarTurbo(vehicle)
    local seat = vehicle:FindFirstChild("Seats")
        and vehicle.Seats:FindFirstChildWhichIsA("VehicleSeat")
    if not seat then return end

    for _, v in pairs(seat:GetChildren()) do
        if v:IsA("NumberValue") and v.Name:lower():find("turbo") then
            v.Value = turboValue
        end
    end
end

local function applyBoatSpeed(vehicle)
    local body = vehicle:FindFirstChild("Body")
    if not body then return end

    for _, obj in pairs(body:GetDescendants()) do
        if obj:IsA("NumberValue") then
            obj.Value = speedValue
        end
    end

    if vehicle.PrimaryPart then
        vehicle.PrimaryPart.AssemblyLinearVelocity =
            vehicle.PrimaryPart.CFrame.LookVector * speedValue
    end
end

local function applySpeedAllVehicles()
    local folder = workspace:FindFirstChild("Vehicles")
    if not folder then return end

    for _, v in pairs(folder:GetChildren()) do
        if v:FindFirstChild("Seats") then
            applyCarSpeed(v)

        elseif v:FindFirstChild("Body") then
            applyBoatSpeed(v)

        elseif isHorse(v) then
            applyHorseSpeed(v)
        end
    end
end

local function applyTurboAllCars()
    local folder = workspace:FindFirstChild("Vehicles")
    if not folder then return end

    for _, v in pairs(folder:GetChildren()) do
        if v:FindFirstChild("Seats") then
            applyCarTurbo(v)
        end
    end
end

local function applyPlayerSpeed()
    local char = getCharacter()
    local humanoid = char:FindFirstChildWhichIsA("Humanoid")
    if humanoid then
        humanoid.WalkSpeed = speedValue
    end
end

local function resetPlayerSpeed()
    local char = getCharacter()
    local humanoid = char:FindFirstChildWhichIsA("Humanoid")
    if humanoid then
        humanoid.WalkSpeed = defaultWalkSpeed
    end
end

local function boostAttachedObjects()
    local char = getCharacter()
    local root = char:FindFirstChild("HumanoidRootPart")
    if not root then return end

    for _, v in pairs(char:GetChildren()) do
        if v:IsA("Model") and v.PrimaryPart then
            v.PrimaryPart.AssemblyLinearVelocity =
                root.CFrame.LookVector * speedValue
        end
    end
end

Tab:AddTextBox({
    Name = "Speed",
    PlaceholderText = "200",
    Callback = function(v)
        local n = tonumber(v)
        if n then speedValue = n end
    end
})

Tab:AddTextBox({
    Name = "Turbo",
    PlaceholderText = "11.3",
    Callback = function(v)
        local n = tonumber(v)
        if n then turboValue = n end
    end
})

Tab:AddButton({
    Name = "Apply Speed (Car & Boat)",
    Callback = function()
        applySpeedAllVehicles()
    end
})

Tab:AddButton({
    Name = "Apply Turbo (Car / No Boat)",
    Callback = function()
        applyTurboAllCars()
    end
})

Tab:AddButton({
    Name = "Apply Speed (Smaller Vehicles)",
    Callback = function()
        applyPlayerSpeed()
    end
})

local RunService = game:GetService("RunService")

local usingSpeedItem = false

local function isUsingVehicleOrItem()
    local char = getCharacter()
    local humanoid = char:FindFirstChildWhichIsA("Humanoid")
    if not humanoid then return false end

    if humanoid.SeatPart then
        return true
    end

    for _, v in pairs(char:GetChildren()) do
        if v:IsA("Model") and v.PrimaryPart then
            return true
        end
    end

    return false
end

RunService.Heartbeat:Connect(function()
    local char = LocalPlayer.Character
    if not char then return end

    local humanoid = char:FindFirstChildWhichIsA("Humanoid")
    if not humanoid then return end

    local usingNow = isUsingVehicleOrItem()

    if usingNow then
        usingSpeedItem = true

    elseif usingSpeedItem then
        humanoid.WalkSpeed = defaultWalkSpeed
        usingSpeedItem = false
    end
end)

local RunService = game:GetService("RunService")
local wasUsing = false

RunService.Heartbeat:Connect(function()
    local char = LocalPlayer.Character
    if not char then return end

    local humanoid = char:FindFirstChildWhichIsA("Humanoid")
    local root = char:FindFirstChild("HumanoidRootPart")
    if not humanoid or not root then return end

    local usingNow = humanoid.SeatPart ~= nil

    if wasUsing and not usingNow then
        humanoid.WalkSpeed = defaultWalkSpeed
        root.AssemblyLinearVelocity = Vector3.zero
        root.AssemblyAngularVelocity = Vector3.zero
    end

    wasUsing = usingNow
end)

---------------------------------------------------------------------------------------------------------------------------------
                                                   -- === Tab: Protections === --
---------------------------------------------------------------------------------------------------------------------------------
local Tab = Window:MakeTab({"Protections", "Shield"})
local Section = Tab:AddSection({"Advanced Protections"})

local CatholicPlayer = game:GetService("Players").LocalPlayer
local CatholicWorkspace = game:GetService("Workspace")
local CatholicRunService = game:GetService("RunService")

local catholicBackupStorage = {
    vehicles = {},
    canoes = {},
    jets = {},
    helis = {},
    balls = {},
    sounds = {}
}

local catholicActiveConnections = {}

local function catholicStoreObject(obj, storageKey)
    if not obj or not obj.Parent then return end
    catholicBackupStorage[storageKey][obj] = obj.Parent
    obj.Parent = nil
end

local function catholicRestoreObjects(storageKey)
    for obj, parent in pairs(catholicBackupStorage[storageKey]) do
        if obj and parent then
            obj.Parent = parent
        end
    end
    catholicBackupStorage[storageKey] = {}
end

local function catholicDisconnectService(serviceName)
    if catholicActiveConnections[serviceName] then
        catholicActiveConnections[serviceName]:Disconnect()
        catholicActiveConnections[serviceName] = nil
    end
end

local function catholicIsPlayerOwnedVehicle(vehicle)
    for _, part in ipairs(vehicle:GetDescendants()) do
        if (part:IsA("VehicleSeat") or part:IsA("Seat")) and part.Occupant then
            if part.Occupant.Parent == CatholicPlayer.Character then
                return true
            end
        end
    end
    return false
end

Tab:AddToggle({
    Name = "Ant Fling Cars",
    Default = false,
    Callback = function(state)
        if state then
            catholicActiveConnections.vehicles = CatholicRunService.Heartbeat:Connect(function()
                local vehiclesFolder = CatholicWorkspace:FindFirstChild("Vehicles")
                if not vehiclesFolder then return end
                
                for _, vehicle in ipairs(vehiclesFolder:GetChildren()) do
                    if not catholicIsPlayerOwnedVehicle(vehicle) then
                        catholicStoreObject(vehicle, "vehicles")
                    end
                end
            end)
        else
            catholicDisconnectService("vehicles")
            catholicRestoreObjects("vehicles")
        end
    end
})

Tab:AddToggle({
    Name = "Ant Fling Canoe",
    Default = false,
    Callback = function(state)
        if state then
            catholicActiveConnections.canoes = CatholicRunService.Heartbeat:Connect(function()
                local storage = CatholicWorkspace:FindFirstChild("WorkspaceCom")
                if storage then
                    storage = storage:FindFirstChild("001_CanoeStorage")
                end
                if not storage then return end
                
                for _, canoe in ipairs(storage:GetChildren()) do
                    local owner = canoe:FindFirstChild("Owner")
                    if not owner or owner.Value ~= CatholicPlayer then
                        catholicStoreObject(canoe, "canoes")
                    end
                end
            end)
        else
            catholicDisconnectService("canoes")
            catholicRestoreObjects("canoes")
        end
    end
})

Tab:AddToggle({
    Name = "Ant Fling Jets",
    Default = false,
    Callback = function(state)
        if state then
            catholicActiveConnections.jets = CatholicRunService.Heartbeat:Connect(function()
                local path = CatholicWorkspace:FindFirstChild("WorkspaceCom")
                if path then path = path:FindFirstChild("001_Airport") end
                if path then path = path:FindFirstChild("AirportHanger") end
                if path then path = path:FindFirstChild("001_JetStorage") end
                if path then path = path:FindFirstChild("JetAirport") end
                if not path then return end
                
                for _, jet in ipairs(path:GetChildren()) do
                    if jet.Name ~= CatholicPlayer.Name then
                        catholicStoreObject(jet, "jets")
                    end
                end
            end)
        else
            catholicDisconnectService("jets")
            catholicRestoreObjects("jets")
        end
    end
})

Tab:AddToggle({
    Name = "Ant Fling Helicopter",
    Default = false,
    Callback = function(state)
        if state then
            catholicActiveConnections.helis = CatholicRunService.Heartbeat:Connect(function()
                local heliFolder = CatholicWorkspace:FindFirstChild("WorkspaceCom")
                if heliFolder then
                    heliFolder = heliFolder:FindFirstChild("001_HeliStorage")
                end
                if heliFolder then
                    heliFolder = heliFolder:FindFirstChild("PoliceStationHeli")
                end
                if not heliFolder then return end
                
                for _, heli in ipairs(heliFolder:GetChildren()) do
                    if heli.Name ~= CatholicPlayer.Name then
                        catholicStoreObject(heli, "helis")
                    end
                end
            end)
        else
            catholicDisconnectService("helis")
            catholicRestoreObjects("helis")
        end
    end
})

Tab:AddToggle({
    Name = "Ant Fling Ball",
    Default = false,
    Callback = function(state)
        if state then
            catholicActiveConnections.balls = CatholicRunService.Heartbeat:Connect(function()
                local ballFolder = CatholicWorkspace:FindFirstChild("WorkspaceCom")
                if ballFolder then
                    ballFolder = ballFolder:FindFirstChild("001_SoccerBalls")
                end
                if not ballFolder then return end
                
                for _, ball in ipairs(ballFolder:GetChildren()) do
                    catholicStoreObject(ball, "balls")
                end
            end)
        else
            catholicDisconnectService("balls")
            catholicRestoreObjects("balls")
        end
    end
})

Tab:AddToggle({
    Name = "Ant Fling Doors",
    Description = "",
    Default = false,
    Callback = function(state)
        if not _G.hiddenDoors then _G.hiddenDoors = {} end
        if state then
            _G.hiddenDoors = {}
            for _, obj in ipairs(workspace:GetDescendants()) do
                if obj:IsA("BasePart") and obj.Name:lower():find("door") then
                    local doorData = {
                        door = obj,
                        originalTransparency = obj.Transparency,
                        originalCanCollide = obj.CanCollide,
                        originalCastShadow = obj.CastShadow
                    }
                    obj.Transparency = 1
                    obj.CanCollide = false
                    obj.CastShadow = false
                    for _, child in ipairs(obj:GetChildren()) do
                        if child:IsA("BasePart") then
                            child.Transparency = 1
                            child.CanCollide = false
                        elseif child:IsA("SurfaceGui") or child:IsA("BillboardGui") then
                            child.Enabled = false
                        end
                    end
                    table.insert(_G.hiddenDoors, doorData)
                end
            end
            print("ðŸ”§ " .. #_G.hiddenDoors .. " portas escondidas!")
        else
            for _, doorData in ipairs(_G.hiddenDoors or {}) do
                if doorData.door and doorData.door.Parent then
                    doorData.door.Transparency = doorData.originalTransparency
                    doorData.door.CanCollide = doorData.originalCanCollide
                    doorData.door.CastShadow = doorData.originalCastShadow
                    for _, child in ipairs(doorData.door:GetChildren()) do
                        if child:IsA("BasePart") then
                            child.Transparency = 0
                            child.CanCollide = true
                        elseif child:IsA("SurfaceGui") or child:IsA("BillboardGui") then
                            child.Enabled = true
                        end
                    end
                end
            end
            print("âœ… " .. #(_G.hiddenDoors or {}) .. " portas restauradas com funcionalidade!")
            _G.hiddenDoors = {}
        end
    end
})

Tab:AddToggle({
    Name = "Ant Lag",
    Description = "",
    Default = false,
    Callback = function(state)
        local Players = game:GetService("Players")
        local dedupLock = {}
        local IGNORED_PLAYER

        if not state then return end

        local function marcarIgnorado(player)
            IGNORED_PLAYER = player
        end

        local function isTargetTool(inst)
            return inst:IsA("Tool")
        end

        local function gatherTools(player)
            local found = {}
            local containers = {}
            if player.Character then table.insert(containers, player.Character) end
            local backpack = player:FindFirstChildOfClass("Backpack")
            if backpack then table.insert(containers, backpack) end
            local sg = player:FindFirstChild("StarterGear")
            if sg then table.insert(containers, sg) end
            for _, container in ipairs(containers) do
                for _, child in ipairs(container:GetChildren()) do
                    if isTargetTool(child) then table.insert(found, child) end
                end
            end
            return found
        end

        local function dedupePlayer(player)
            if player == IGNORED_PLAYER then return end
            if dedupLock[player] then return end
            dedupLock[player] = true
            local tools = gatherTools(player)
            if #tools > 1 then
                for i = 2, #tools do pcall(function() tools[i]:Destroy() end) end
            end
            dedupLock[player] = false
        end

        local function hookPlayer(player)
            if not IGNORED_PLAYER then marcarIgnorado(player) end
            task.defer(dedupePlayer, player)
            local function setupChar(char)
                task.delay(0.5, function() dedupePlayer(player) end)
                char.ChildAdded:Connect(function(child)
                    if isTargetTool(child) then task.delay(0.1, function() dedupePlayer(player) end) end
                end)
            end
            if player.Character then setupChar(player.Character) end
            player.CharacterAdded:Connect(setupChar)
            local backpack = player:WaitForChild("Backpack", 10)
            if backpack then
                backpack.ChildAdded:Connect(function(child)
                    if isTargetTool(child) then task.delay(0.1, function() dedupePlayer(player) end) end
                end)
            end
            local sg = player:FindFirstChild("StarterGear") or player:WaitForChild("StarterGear", 10)
            if sg then
                sg.ChildAdded:Connect(function(child)
                    if isTargetTool(child) then task.delay(0.1, function() dedupePlayer(player) end) end
                end)
            end
        end

        Players.PlayerAdded:Connect(hookPlayer)
        for _, plr in ipairs(Players:GetPlayers()) do hookPlayer(plr) end

        task.spawn(function()
            while state do
                for _, plr in ipairs(Players:GetPlayers()) do dedupePlayer(plr) end
                task.wait(2)
            end
        end)
    end
})

Tab:AddToggle({
    Name = "Ant Bug",
    Default = false,
    Callback = function(Value)
        if Value then

            local Players = game:GetService("Players")
            local LocalPlayer = Players.LocalPlayer
            
            local antBugConnections = {}
            
            local blacklist = {
                {Name = "water", Class = "Part"},
            }
            
            local function neutralize(part)
                if part and part:IsA("BasePart") then
                    pcall(function()
                        part.Anchored = true
                        part.CanCollide = false
                        part.Massless = true
                        part.Transparency = 1
                        part:ClearAllChildren()
                    end)
                    pcall(function()
                        part:Destroy()
                    end)
                end
            end
            
            table.insert(antBugConnections, workspace.DescendantAdded:Connect(function(obj)
                for _, rule in ipairs(blacklist) do
                    if obj.Name == rule.Name and obj.ClassName == rule.Class then
                        neutralize(obj)
                    end
                end
            end))
            
            for _, obj in ipairs(workspace:GetDescendants()) do
                for _, rule in ipairs(blacklist) do
                    if obj.Name == rule.Name and obj.ClassName == rule.Class then
                        neutralize(obj)
                    end
                end
            end
            
            local loopRunning = true
            task.spawn(function()
                while loopRunning do
                    task.wait(0.25)
                    for _, rule in ipairs(blacklist) do
                        for _, v in next, getnilinstances() do
                            if v.Name == rule.Name and v.ClassName == rule.Class then
                                neutralize(v)
                            end
                        end
                    end
                end
            end)
            
            local function onCharacterAdded(char)
                local hum = char:WaitForChild("Humanoid")
                table.insert(antBugConnections, hum.Touched:Connect(function(hit)
                    for _, rule in ipairs(blacklist) do
                        if hit.Name == rule.Name and hit.ClassName == rule.Class then
                            neutralize(hit)
                        end
                    end
                end))
            end
            
            table.insert(antBugConnections, LocalPlayer.CharacterAdded:Connect(onCharacterAdded))
            
            if LocalPlayer.Character then
                onCharacterAdded(LocalPlayer.Character)
            end
            
            _G.antBugData = {
                connections = antBugConnections,
                loopRunning = loopRunning
            }
            
        else

            if _G.antBugData then

                for _, conn in ipairs(_G.antBugData.connections) do
                    pcall(function()
                        conn:Disconnect()
                    end)
                end
                
                _G.antBugData.loopRunning = false
                
                _G.antBugData = nil
            end

        end
    end
})

Tab:AddToggle({
    Name = "Ant Sit (local)",
    Default = false,
    Callback = function(state)
        if state then
            catholicActiveConnections.sit = CatholicRunService.Heartbeat:Connect(function()
                local humanoid = CatholicPlayer.Character and CatholicPlayer.Character:FindFirstChildOfClass("Humanoid")
                if not humanoid then return end
                
                humanoid:SetStateEnabled(Enum.HumanoidStateType.Seated, false)
                
                if humanoid:GetState() == Enum.HumanoidStateType.Seated then
                    humanoid:ChangeState(Enum.HumanoidStateType.Running)
                end
                
                if humanoid.SeatPart then
                    humanoid.Sit = false
                    humanoid.SeatPart = nil
                end
            end)
        else
            catholicDisconnectService("sit")
            local humanoid = CatholicPlayer.Character and CatholicPlayer.Character:FindFirstChildOfClass("Humanoid")
            if humanoid then
                humanoid:SetStateEnabled(Enum.HumanoidStateType.Seated, true)
            end
        end
    end
})

Tab:AddToggle({
    Name = "Ant Sound",
    Default = false,
    Callback = function(state)
        if state then
            catholicActiveConnections.sounds = CatholicRunService.Heartbeat:Connect(function()
                for _, obj in ipairs(CatholicWorkspace:GetDescendants()) do
                    if obj:IsA("Sound") then
                        catholicStoreObject(obj, "sounds")
                    end
                end
            end)
        else
            catholicDisconnectService("sounds")
            catholicRestoreObjects("sounds")
        end
    end
})

---------------------------------------------------------------------------------------------------------------------------------
                                                   -- === Tab: Troll Player === --
---------------------------------------------------------------------------------------------------------------------------------
local Tab = Window:MakeTab({"Troll Player", "skull"}) 
