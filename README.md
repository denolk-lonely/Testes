
game.StarterGui:SetCore("SendNotification", {
    Title = "Welcome to Catholic Hub!",
    Text = "Look at the credits in the first tab!",
    Duration = 5,
})

--------------------------------------------------------------------------------------------------------------------------------
loadstring(game:HttpGet("https://pastebin.com/raw/N4xSxRQU"))()

local redzlib = loadstring(game:HttpGet("https://pastefy.app/WTFg1Qpp/raw"))()

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
    Description = "Join our Discord server",
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

Tab:AddButton({
    Name = "Copy All Info",
    Callback = function()
        local info = "=== Catholic Hub Info ===\n"
        info = info .. "User: " .. player.Name .. "\n"
        info = info .. "ID: " .. player.UserId .. "\n"
        info = info .. "Executor: " .. detectExecutor() .. "\n"
        info = info .. "Server: " .. #players:GetPlayers() .. "/" .. players.MaxPlayers .. "\n"
        info = info .. "Time: " .. getTime() .. " | " .. getDate() .. "\n"
        info = info .. "========================"
        
        setclipboard(info)
        game.StarterGui:SetCore("SendNotification", {
            Title = "Success",
            Text = "Info copied to clipboard!",
            Duration = 3
        })
    end
})

Tab:AddSection({ "Development Team" })

Tab:AddParagraph({ "Owner & Sub-Owner:", "Denolk & Mayke" })
Tab:AddParagraph({ "Manager & Developer:", "Streex..." })
Tab:AddParagraph({ "Admins:", "Ghost and DemoxianYT" })
Tab:AddParagraph({ "Moderators:", "Nplayboy, PH, Ixi362" })
Tab:AddParagraph({ "Testers:", "Fhata & Bryan... (In-complete)" })

Tab:AddSection({ "Hub Information" })

Tab:AddParagraph({ "Name:", "Catholic Hub" })
Tab:AddParagraph({ "Version:", "1.1 Remade" })
Tab:AddParagraph({ "Game:", "Brookhaven RP" })

task.spawn(function()
    while task.wait(1) do

    end
end)

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
 
local InfiniteJumpEnabled = false
 
 game:GetService("UserInputService").JumpRequest:Connect(function()
    if InfiniteJumpEnabled then
       local character = game.Players.LocalPlayer.Character
       if character and character:FindFirstChild("Humanoid") then
          character.Humanoid:ChangeState(Enum.HumanoidStateType.Jumping)
       end
    end
end)

Tab:AddButton({
    Name = "Reset Speed, Gravity, Jump Power",
    Callback = function()
        -- Resetar Speed
        local player = game.Players.LocalPlayer
        local character = player.Character or player.CharacterAdded:Wait()
        local humanoid = character:FindFirstChildOfClass("Humanoid")
        if humanoid then
            humanoid.WalkSpeed = 16 
            humanoid.JumpPower = 50 
        end
        
        game.Workspace.Gravity = 196.2 
        

        InfiniteJumpEnabled = false
    end
})
 
Tab:AddToggle({
    Name = "Infinite Jump",
    Default = false,
    Callback = function(Value)
       InfiniteJumpEnabled = Value
    end
})

local UltimateNoclip = {
    Enabled = false,
    Connections = {},
    SoccerBalls = {}
}

local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
local Workspace = game:GetService("Workspace")
local LocalPlayer = Players.LocalPlayer

local function managePlayerCollisions(character)
    if not character then return end
    
    for _, part in ipairs(character:GetDescendants()) do
        if part:IsA("BasePart") then
            part.CanCollide = not UltimateNoclip.Enabled
            part.Anchored = false
        end
    end
end

local function voidProtection(rootPart)
    if rootPart.Position.Y < -500 then
        local safeCFrame = CFrame.new(0, 100, 0)
        local rayParams = RaycastParams.new()
        rayParams.FilterDescendantsInstances = {LocalPlayer.Character}
        
        local result = Workspace:Raycast(rootPart.Position, Vector3.new(0, 500, 0), rayParams)
        rootPart.CFrame = result and CFrame.new(result.Position + Vector3.new(0, 5, 0)) or safeCFrame
    end
end

local function manageSoccerBalls()
    local soccerFolder = Workspace:FindFirstChild("Com", true)
                      and Workspace.Com:FindFirstChild("001_SoccerBalls")
    
    if soccerFolder then
        for _, ball in ipairs(soccerFolder:GetChildren()) do
            if ball.Name:match("^Soccer") then
                pcall(function()
                    ball.CanCollide = not UltimateNoclip.Enabled
                    ball.Anchored = UltimateNoclip.Enabled
                end)
                UltimateNoclip.SoccerBalls[ball] = true
            end
        end
        
        if not UltimateNoclip.Connections.BallAdded then
            UltimateNoclip.Connections.BallAdded = soccerFolder.ChildAdded:Connect(function(ball)
                if ball.Name:match("^Soccer") then
                    task.wait(0.3)
                    pcall(function()
                        ball.CanCollide = not UltimateNoclip.Enabled
                        ball.Anchored = UltimateNoclip.Enabled
                    end)
                end
            end)
        end
    end
end

local section = Tab:AddSection({"Manage Player Boards"})

local textoPlaca = ""
local selectedPlaca = nil

local function getPlayersListPlaca()
    local list = {}
    for _, plr in ipairs(Players:GetPlayers()) do
        if plr ~= LocalPlayer then
            table.insert(list, plr.Name)
        end
    end
    return list
end

local function trocaPlaca(all, txt)
    if all then
        for _, v in next, Players:GetPlayers() do
            if v.Character and v.Character:FindFirstChild("Sign") then
                v.Character:FindFirstChild("Sign").ToolSound:FireServer("Sign", "SignWords", txt)
            end
        end
    else
        if selectedPlaca then
            local target = Players:FindFirstChild(selectedPlaca)
            if target and target.Character and target.Character:FindFirstChild("Sign") then
                target.Character:FindFirstChild("Sign").ToolSound:FireServer("Sign", "SignWords", txt)
            end
        end
    end
end

Tab:AddTextBox({
    Name = "Text on the Plate",
    PlaceholderText = "Texto da placa",
    Callback = function(value)
        textoPlaca = value
    end
})

Tab:AddButton({
    Name = "Rewrite ALL Plate",
    Callback = function()
        trocaPlaca(true, textoPlaca)
    end
})

 ---------------------------------------------------------------------------------------------------------------------------------
                                                   -- === Tab: Raid Sky === --
-----------------------------------------------------------------------------------------------------------------------------------
local Tab = Window:MakeTab({"Raid Sky", "cloud"})
local Section = Tab:AddSection({"SkyBox Functions"})

local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local LocalPlayer = Players.LocalPlayer

local Remotes = ReplicatedStorage:WaitForChild("Remotes")
local ChangeCharacterBody = Remotes:WaitForChild("ChangeCharacterBody")

local BodyId = "100839513065432"
local CurrentTrack
local Humanoid, Animator
local LoopAnim = false

local function SetupCharacter(char)
	Humanoid = char:WaitForChild("Humanoid")
	Animator = Humanoid:FindFirstChildOfClass("Animator")
	if not Animator then
		Animator = Instance.new("Animator")
		Animator.Parent = Humanoid
	end
end

SetupCharacter(LocalPlayer.Character or LocalPlayer.CharacterAdded:Wait())
LocalPlayer.CharacterAdded:Connect(SetupCharacter)

local function ApplyBody()
	pcall(function()
		ChangeCharacterBody:InvokeServer({
			[1] = tonumber(BodyId)
		})
	end)
end

local function ResetBody()
	pcall(function()
		local args = {
			[1] = {
				[1] = 0,
				[2] = 0,
				[3] = 0,
				[4] = 0,
				[5] = 0,
				[6] = 0
			}
		}
		ChangeCharacterBody:InvokeServer(unpack(args))
	end)
end

local function PlayAnimation()
	if not Animator then return end
	local Anim = Instance.new("Animation")
	Anim.AnimationId = "rbxassetid://70883871260184"
	local track = Animator:LoadAnimation(Anim)
	track.Priority = Enum.AnimationPriority.Action
	track.Looped = false
	track:Play()
	CurrentTrack = track
end

local function StopAnimation()
	LoopAnim = false
	if CurrentTrack then
		pcall(function()
			CurrentTrack:Stop()
		end)
	end
end

Tab:AddToggle({
	Name = "SkyBox FE",
	Description = "",
	Default = false,
	Callback = function(Value)
		if Value then
			LoopAnim = true
			task.spawn(function()
				while LoopAnim do
					PlayAnimation()
					task.wait(0.001)
				end
			end)
			task.delay(1.2, ApplyBody)
		else
			StopAnimation()
			ResetBody()
		end
	end
})

local Camisas = {
    ["C00lkid"] = 88508273882423,
    ["Tubers93"] = 138121234806572,
    ["Night"] = 4921509323,
    ["Sky"] = 14820056722,
    ["Horror"] = 11714553713,
    ["Hacker"] = 9567541545,
    ["Blood"] = 881133247,
}

local CamisaNomes = {}
for nome in pairs(Camisas) do
    table.insert(CamisaNomes, nome)
end

table.sort(CamisaNomes)

Tab:AddDropdown({
    Name = "Shirts",
    Options = CamisaNomes,
    Callback = function(selecionada)
        local id = Camisas[selecionada]
        if id then
            ReplicatedStorage.Remotes.WearShirt:InvokeServer(id)
        end
    end
})


Tab:AddTextBox({
    Name = "Shirt ID",
    PlaceholderText = "Enter the Shirt ID",
    Callback = function(Value)
        local id = tonumber(Value)
        if id then
            pcall(function()
                ReplicatedStorage.Remotes.WearShirt:InvokeServer(id)
            end)
        end
    end
})

local Section = Tab:AddSection({"FleshBang Functions"})

local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer
local ChangeCharacterBody = ReplicatedStorage:WaitForChild("Remotes"):WaitForChild("ChangeCharacterBody")

local LoopAnim = false
local CurrentTrack

local function ApplyFreshBang()
	pcall(function()
		local args = {
			[1] = {
				[1] = 96655874457685,
				[2] = 123402086843885,
				[3] = 78300682916056,
				[4] = 86276701020724,
				[5] = 78409653958165,
				[6] = 120668655481073
			}
		}
		ChangeCharacterBody:InvokeServer(unpack(args))
	end)
end

local function ResetBody()
	pcall(function()
		local args = {
			[1] = {
				[1] = 0,
				[2] = 0,
				[3] = 0,
				[4] = 0,
				[5] = 0,
				[6] = 0
			}
		}
		ChangeCharacterBody:InvokeServer(unpack(args))
	end)
end

local function PlayAnimation()
	local char = LocalPlayer.Character or LocalPlayer.CharacterAdded:Wait()
	local humanoid = char:WaitForChild("Humanoid")
	local animator = humanoid:FindFirstChildOfClass("Animator") or Instance.new("Animator", humanoid)
	local Anim = Instance.new("Animation")
	Anim.AnimationId = "rbxassetid://70883871260184"
	local track = animator:LoadAnimation(Anim)
	track.Priority = Enum.AnimationPriority.Action
	track.Looped = false
	track:Play()
	CurrentTrack = track
end

local function StopAnimation()
	LoopAnim = false
	if CurrentTrack then
		pcall(function()
			CurrentTrack:Stop()
		end)
	end
end

Tab:AddToggle({
	Name = "FreshBang",
	Description = "",
	Default = false,
	Callback = function(Value)
		if Value then
			LoopAnim = true
			task.spawn(function()
				while LoopAnim do
					PlayAnimation()
					task.wait(0.05)
				end
			end)
			task.delay(1.2, ApplyFreshBang)
		else
			StopAnimation()
			ResetBody()
		end
	end
})


local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Players = game:GetService("Players")
local RunService = game:GetService("RunService")

local LocalPlayer = Players.LocalPlayer
local Remotes = ReplicatedStorage:WaitForChild("Remotes")
local ChangeBodyColor = Remotes:WaitForChild("ChangeBodyColor")

local primaryColors = {
	"White","Black","Really red","Bright blue","Bright green",
	"Bright yellow","Bright orange","Bright purple","Bright pink"
}

local rgbColors = {
	"Really red","Bright orange","Bright yellow","Bright green",
	"Bright bluish green","Bright blue","Bright violet","Bright pink"
}

local mode = "None"
local rgbEnabled = false

Tab:AddDropdown({
	Name = "Body Color",
	Options = {"None","Primary Colors","RGB"},
	Default = "None",
	Callback = function(v)
		mode = v
		rgbEnabled = v == "RGB"
		if rgbEnabled then
			task.spawn(function()
				while rgbEnabled do
					for _, c in ipairs(rgbColors) do
						if not rgbEnabled then break end
						ChangeBodyColor:FireServer(c)
						task.wait(0.25)
					end
				end
			end)
		end
	end
})

Tab:AddDropdown({
	Name = "Primary Body Color",
	Options = primaryColors,
	Default = primaryColors[1],
	Callback = function(v)
		if mode == "Primary Colors" then
			ChangeBodyColor:FireServer(v)
		end
	end
})

local rgbAtivo = false
local rgbThread

local cores = {
    "Light reddish violet","Salmon","Sunrise","Carnation pink","Pink","Hot pink",
    "Really red","Tawny","Burgundy","Maroon","Cocoa","Rust","CGA brown","Beige",
    "Brick yellow","Burlap","Fawn brown","Br. yellowish orange","Olive","New Yeller",
    "Br. yellowish green","Mint","Artichoke","Lime green","Grime","Forest green",
    "Parsley green","Earth green","Slime green","Toothpaste","Pastel light blue",
    "Cyan","Bright blue","Really blue","Dark blue","Navy blue","Royal purple",
    "Magenta","Bright violet","Eggplant","Mulberry","Institutional white",
    "Mid gray","Cloudy grey","Flint","Fossil","Medium stone grey",
    "Dark stone grey","Smoky grey","Black","Really black","Dirt brown",
    "Pine Cone","Brown","Dark nougat","Light orange","Pastel brown"
}

local function iniciarRGB()
    if rgbThread then return end
    rgbThread = task.spawn(function()
        while rgbAtivo do
            for _, cor in ipairs(cores) do
                if not rgbAtivo then break end
                pcall(function()
                    ReplicatedStorage.Remotes.ChangeBodyColor:FireServer(cor)
                end)
                task.wait(0.02) 
            end
        end
        rgbThread = nil
    end)
end

Tab:AddToggle({
    Name = "RGB Body (Speed)",
    Default = false,
    Callback = function(v)
        rgbAtivo = v
        if v then
            iniciarRGB()
        end
    end
})

local Section = Tab:AddSection({"Spin Settings (SkyBox FE & FleshBang)"})

local spinEnabled = false
local spinSpeed = 10
local spinDirection = 1 -- 1 = direita, -1 = esquerda

Tab:AddToggle({
	Name = "Spin Body",
	Description = "",
	Default = false,
	Callback = function(v)
		spinEnabled = v
		if v then
			task.spawn(function()
				while spinEnabled do
					local char = LocalPlayer.Character
					if char and char:FindFirstChild("HumanoidRootPart") then
						local root = char.HumanoidRootPart
						root.CFrame = root.CFrame * CFrame.Angles(0, math.rad(spinSpeed * spinDirection), 0)
					end
					task.wait(0.02)
				end
			end)
		end
	end
})

Tab:AddToggle({
    Name = "Spin Direction (Right/Left)",
    Description = "",
    Default = true, -- true = direita, false = esquerda
    Callback = function(v)
        if v then
            spinDirection = 1  -- Direita
        else
            spinDirection = -1 -- Esquerda
        end
    end
})

Tab:AddSlider({
    Name = "Spin Speed",
    Description = "",
    MinValue = 1,
    MaxValue = 1000,
    Default = 10,
    Increase = 1,
    Callback = function(v)
        spinSpeed = v
    end
})

----------------------------------------------------------------------------------------------------------------------------------
                                                         -- Tab:  Avatar --
----------------------------------------------------------------------------------------------------------------------------------
local Tab = Window:MakeTab({"Avatar", "shirt"})

local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Remotes = ReplicatedStorage:WaitForChild("Remotes")

local Section = Tab:AddSection({"Copy Avatar"})
local Target = nil

local function GetPlayerNames()
    local playerNames = {}
    for _, player in ipairs(Players:GetPlayers()) do
        if player.Name ~= LocalPlayer.Name then
            table.insert(playerNames, player.Name)
        end
    end
    return playerNames
end

local Dropdown = Tab:AddDropdown({
    Name = "Player List",
    Description = "",
    Options = GetPlayerNames(),
    Default = "",
    Flag = "player list",
    Callback = function(playername)
        Target = playername
    end
})

local function UpdatePlayers()
    Dropdown:Set(GetPlayerNames())
end

UpdatePlayers()
Players.PlayerAdded:Connect(UpdatePlayers)
Players.PlayerRemoving:Connect(UpdatePlayers)

Tab:AddButton({
    Name = "Update List",
    Callback = UpdatePlayers
})

Tab:AddButton({
    Name = "Copy Avatar",
    Callback = function()
        if not Target then return end
        local LP = LocalPlayer
        local LChar = LP.Character
        local TPlayer = Players:FindFirstChild(Target)
        if not (TPlayer and TPlayer.Character) then return end

        local LHumanoid = LChar and LChar:FindFirstChildOfClass("Humanoid")
        local THumanoid = TPlayer.Character:FindFirstChildOfClass("Humanoid")
        if not (LHumanoid and THumanoid) then return end

        local LDesc = LHumanoid:GetAppliedDescription()
        local PDesc = THumanoid:GetAppliedDescription()

        -- Reset Accessories
        for _, acc in ipairs(LDesc:GetAccessories(true)) do
            if acc.AssetId and tonumber(acc.AssetId) then
                Remotes.Wear:InvokeServer(tonumber(acc.AssetId))
                task.wait(0.2)
            end
        end

        if tonumber(LDesc.Shirt) then Remotes.Wear:InvokeServer(tonumber(LDesc.Shirt)); task.wait(0.2) end
        if tonumber(LDesc.Pants) then Remotes.Wear:InvokeServer(tonumber(LDesc.Pants)); task.wait(0.2) end
        if tonumber(LDesc.Face) then Remotes.Wear:InvokeServer(tonumber(LDesc.Face)); task.wait(0.2) end

        -- Apply Body Parts
        local argsBody = {{PDesc.Torso, PDesc.RightArm, PDesc.LeftArm, PDesc.RightLeg, PDesc.LeftLeg, PDesc.Head}}
        Remotes.ChangeCharacterBody:InvokeServer(unpack(argsBody))
        task.wait(0.5)

        if tonumber(PDesc.Shirt) then Remotes.Wear:InvokeServer(tonumber(PDesc.Shirt)); task.wait(0.3) end
        if tonumber(PDesc.Pants) then Remotes.Wear:InvokeServer(tonumber(PDesc.Pants)); task.wait(0.3) end
        if tonumber(PDesc.Face) then Remotes.Wear:InvokeServer(tonumber(PDesc.Face)); task.wait(0.3) end

        for _, v in ipairs(PDesc:GetAccessories(true)) do
            if v.AssetId and tonumber(v.AssetId) then
                Remotes.Wear:InvokeServer(tonumber(v.AssetId))
                task.wait(0.3)
            end
        end

        -- Skin Colors
        local SkinColor = TPlayer.Character:FindFirstChild("Body Colors")
        if SkinColor then Remotes.ChangeBodyColor:FireServer(tostring(SkinColor.HeadColor)); task.wait(0.3) end

        -- Animations
        if tonumber(PDesc.IdleAnimation) then Remotes.Wear:InvokeServer(tonumber(PDesc.IdleAnimation)); task.wait(0.3) end

        -- RP Name & Bio
        local Bag = TPlayer:FindFirstChild("PlayersBag")
        if Bag then
            if Bag:FindFirstChild("RPName") and Bag.RPName.Value ~= "" then Remotes.RPNameText:FireServer("RolePlayName", Bag.RPName.Value); task.wait(0.3) end
            if Bag:FindFirstChild("RPBio") and Bag.RPBio.Value ~= "" then Remotes.RPNameText:FireServer("RolePlayBio", Bag.RPBio.Value); task.wait(0.3) end
            if Bag:FindFirstChild("RPNameColor") then Remotes.RPNameColor:FireServer("PickingRPNameColor", Bag.RPNameColor.Value); task.wait(0.3) end
            if Bag:FindFirstChild("RPBioColor") then Remotes.RPNameColor:FireServer("PickingRPBioColor", Bag.RPBioColor.Value); task.wait(0.3) end
        end
    end
})

Tab:AddSection({"Custom Skins"})
if not _G.togglesInitialized then _G.togglesInitialized = {} end

local originalSkinSaved = false

local function SaveOriginalSkin()
    if not originalSkinSaved then
        pcall(function()
            local SaveOutfit = ReplicatedStorage:WaitForChild("Remotes"):WaitForChild("SaveOutfit")
            SaveOutfit:InvokeServer(50, "Catholic Hub Original")
            originalSkinSaved = true
        end)
    end
end

local function LoadOriginalSkin()
    pcall(function()
        local LoadOutfit = ReplicatedStorage:WaitForChild("Remotes"):WaitForChild("LoadOutfit")
        LoadOutfit:InvokeServer(50)
    end)
end

Tab:AddToggle({
    Name = "Small Avatar",
    Default = false,
    Callback = function(Value)
        if not _G.togglesInitialized.Small then 
            _G.togglesInitialized.Small = true 

            SaveOriginalSkin()
            return 
        end
        
        local body = {104157277410075, 86280536086607, 81974054542977, 74524984742501, 122626731952977, 134082579}
        if Value then 
            Remotes.ChangeCharacterBody:InvokeServer(body) 
        else 
            LoadOriginalSkin() 
        end
    end
})

Tab:AddToggle({
    Name = "Giant Avatar",
    Default = false,
    Callback = function(Value)
        if not _G.togglesInitialized.Giant then 
            _G.togglesInitialized.Giant = true 

            SaveOriginalSkin()
            return 
        end
        
        local body = {17713016036, 17713016151, 17713015861, 17713021340, 17713016191, 6340213}
        if Value then 
            Remotes.ChangeCharacterBody:InvokeServer(body) 
        else 
            LoadOriginalSkin() 
        end
    end
})

Tab:AddSection({"Effects Avatar"})

local effectList = {
    {name = "Yellow Hearts", id = "18635672195", code = "001HeartsYellow"},
    {name = "Green Hearts", id = "18635727693", code = "002HeartsGreen"},
    {name = "Blue Hearts", id = "18635732186", code = "003HeartsBlue"},
    {name = "Purple Hearts", id = "18635723426", code = "004HeartsPurple"},
    {name = "Pink Hearts", id = "18635726250", code = "005HeartsPink"},
    {name = "Red Hearts", id = "18635729673", code = "006HeartsRed"},
    {name = "Orange Dots", id = "18637252424", code = "010DotsOrange"},
    {name = "Yellow Dots", id = "18637263004", code = "011DotsYellow"},
    {name = "Green Dots", id = "18637265264", code = "013DotsGreen"},
    {name = "Blue Dots", id = "18637256859", code = "014DotsBlue"},
    {name = "Purple Dots", id = "18637261058", code = "015DotsPurple"},
    {name = "Pink Dots", id = "18637259328", code = "016DotsPink"},
    {name = "Red Dots", id = "18637267290", code = "017DotsRed"},
    {name = "White Twinkle", id = "18637115654", code = "020TwinkleWhite"},
    {name = "Yellow Twinkle", id = "18637118923", code = "021TwinkleYellow"},
    {name = "Green Twinkle", id = "18637151114", code = "022TwinkleGreen"},
    {name = "Purple Twinkle", id = "18637153880", code = "023TwinklePurple"},
    {name = "Pink Twinkle", id = "18637157071", code = "024TwinklePink"},
    {name = "Red Twinkle", id = "18637155247", code = "025TwinkleRed"},
    {name = "White Fire", id = "18637074370", code = "030FireWhite"},
    {name = "Orange Fire", id = "18637025451", code = "031FireOrange"},
    {name = "Green Fire", id = "18637078598", code = "032FireGreen"},
    {name = "Blue Fire", id = "18637076370", code = "033FireBlue"},
    {name = "Purple Fire", id = "18637070174", code = "034FirePurple"},
    {name = "Black Fire", id = "18637072603", code = "035FireBlack"},
    {name = "Small Yellow Hearts", id = "18637339451", code = "040SmallHeartsYellow"},
    {name = "Small Green Hearts", id = "18637337576", code = "041SmallHeartsGreen"},
    {name = "Small Blue Hearts", id = "18637345162", code = "042SmallHeartsBlue"},
    {name = "Small Purple Hearts", id = "18637335865", code = "043SmallHeartsPurple"},
    {name = "Small Pink Hearts", id = "18637343416", code = "044SmallHeartsPink"},
    {name = "Small Red Hearts", id = "18637341847", code = "045SmallHeartsRed"},
    {name = "White Sparks", id = "18637383085", code = "050SparksWhite"},
    {name = "Green Sparks", id = "18637385236", code = "051SparksGreen"},
    {name = "Blue Sparks", id = "18637386856", code = "052SparksBlue"},
    {name = "Purple Sparks", id = "18637442447", code = "053SparksPurple"},
    {name = "Pink Sparks", id = "18637445897", code = "054SparksPink"},
    {name = "Red Sparks", id = "18637447550", code = "055SparksRed"},
    {name = "Green Bubbles", id = "18637493072", code = "061BubbleGreen"},
    {name = "Blue Bubbles", id = "18637499282", code = "062BubbleBlue"},
    {name = "Purple Bubbles", id = "18637497343", code = "063BubblePurple"},
    {name = "Red Bubbles", id = "18637500927", code = "064BubbleRed"},
    {name = "White Music", id = "18637675173", code = "070MusicWhite"},
    {name = "Green Music", id = "18637677789", code = "071MusicGreen"},
    {name = "Blue Music", id = "18637680960", code = "072MusicBlue"},
    {name = "Purple Music", id = "18637679384", code = "073MusicPurple"},
    {name = "Red Music", id = "18637672698", code = "074MusicRed"},
    {name = "White Smoke", id = "18637791748", code = "080SmokeWhite"},
    {name = "Yellow Smoke", id = "18637800482", code = "081SmokeYellow"},
    {name = "Orange Smoke", id = "18637793920", code = "082SmokeOrange"},
    {name = "Green Smoke", id = "18637789299", code = "083SmokeGreen"},
    {name = "Blue Smoke", id = "18637803021", code = "084SmokeBlue"},
    {name = "Purple Smoke", id = "18637813360", code = "085SmokePurple"},
    {name = "Red Smoke", id = "18637796598", code = "086SmokeRed"},
    {name = "Black Smoke", id = "18637798529", code = "087SmokeBlack"},
    {name = "White Star", id = "18637942956", code = "090StarWhite"},
    {name = "Orange Star", id = "18637946172", code = "091StarOrange"},
    {name = "Green Star", id = "18637934500", code = "092StarGreen"},
    {name = "Blue Star", id = "18637940338", code = "093StarBlue"},
    {name = "Purple Star", id = "18637944796", code = "094StarPurple"},
    {name = "Pink Star", id = "18637947820", code = "095StarPink"},
    {name = "Red Star", id = "18637949457", code = "096StarRed"}
}

local selectedEffect = effectList[1]

local dropdownOptions = {}
for _, effect in ipairs(effectList) do
    table.insert(dropdownOptions, effect.name)
end

local Dropdown = Tab:AddDropdown({
    Name = "Select Effect",
    Options = dropdownOptions,
    Default = effectList[1].name,
    Callback = function(option)
        for _, effect in ipairs(effectList) do
            if effect.name == option then
                selectedEffect = effect
                break
            end
        end
    end
})

Tab:AddButton({
    Name = "Equip Effect",
    Callback = function()
        game:GetService("ReplicatedStorage").Remotes.ApplyEmmiter:InvokeServer(selectedEffect.id, selectedEffect.code)
    end
})

----------------------------------------------------------------------------------------------------------------------------------
                                                         -- Tab: Avatar & Tool FE --
----------------------------------------------------------------------------------------------------------------------------------
local Tab = Window:MakeTab({"Avatar & Tool FE", "person"})
local section = Tab:AddSection({"FE Avatars"})

---------------------------------------------------------------------------------------------------------------------------------
                                          -- === Tab: House === --
---------------------------------------------------------------------------------------------------------------------------------
local Tab = Window:MakeTab({"House", "Home"})

local isUnbanActive = false
local SelectHouse = nil
local NoclipDoor = nil
local loopRunning = false

Tab:AddSection({"Remove Ban System"})

local function RemoveAllBannedBlocks()
    local count = 0
    for _, obj in ipairs(workspace:GetDescendants()) do
        if obj.Name == "BannedBlock" then
            obj:Destroy()
            count += 1
        end
    end
    return count
end

Tab:AddButton({
    Name = "Remove Ban",
    Description = " ",
    Callback = function()
        local removed = RemoveAllBannedBlocks()
        if removed > 0 then
            game.StarterGui:SetCore("SendNotification", {
                Title = "Remove Ban",
                Text = tostring(removed) .. " BannedBlock(s) removed",
                Duration = 4
            })
        else
            game.StarterGui:SetCore("SendNotification", {
                Title = "Remove Ban",
                Text = "No BannedBlock found.",
                Duration = 3
            })
        end
    end
})

Tab:AddToggle({
    Name = "Loop Remove Ban",
    Description = " ",
    Callback = function(Value)
        loopRunning = Value
        if Value then
            task.spawn(function()
                while loopRunning do
                    local removed = RemoveAllBannedBlocks()
                    if removed > 0 then
                        game.StarterGui:SetCore("SendNotification", {
                            Title = "Remove Ban",
                            Text = tostring(removed) .. " BannedBlock(s) removed",
                            Duration = 3
                        })
                    end
                    task.wait(1)
                end
            end)
        end
    end,
    Default = false,
    Flag = false
})

Tab:AddSection({"Simultaneous Functions for All Houses"})

local RunService = game:GetService("RunService")
local noclipDoor = false
local connection

local function setDoorCollision(state)
    for _, obj in ipairs(workspace:GetDescendants()) do
        if obj.Name == "001_HouseDoors" then
            if obj:IsA("BasePart") then
                obj.CanCollide = state
            elseif obj:IsA("Model") then
                for _, part in ipairs(obj:GetDescendants()) do
                    if part:IsA("BasePart") then
                        part.CanCollide = state
                    end
                end
            end
        end
    end
end

Tab:AddToggle({
    Name = "Noclip Door",
    Description = " ",
    Default = false,
    Callback = function(Value)
        noclipDoor = Value

        if Value then
            setDoorCollision(false)

            connection = RunService.Stepped:Connect(function()
                setDoorCollision(false)
            end)
        else
            if connection then
                connection:Disconnect()
                connection = nil
            end
            setDoorCollision(true)
        end
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
    Name = "Tamanho do Texto ESP",
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
local Section = Tab:AddSection({"Name and Bio VIP Free"})

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
                    -- Obter as cores selecionadas
                    local color1 = colorMap[selectedColor1]
                    local color2 = colorMap[selectedColor2]
                    
                    -- Criar efeito de ida e volta
                    local time = tick() * rgbSpeed
                    local t = (math.sin(time) + 1) / 2  -- Varia de 0 a 1 e volta
                    
                    -- Interpolar entre as cores
                    local currentColor = lerpColor(color1, color2, t)
                    
                    -- Aplicar ao nome e bio
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

-- ===== VALUES =====
local speedValue = 200
local turboValue = 11.3
local defaultWalkSpeed = 16

-- ===== SERVICES =====
local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer

-- ===== UTILS =====
local function getCharacter()
    return LocalPlayer.Character or LocalPlayer.CharacterAdded:Wait()
end

-- ===== HORSE CHECK =====
local function isHorse(model)
    if not model or not model:IsA("Model") then return false end

    -- nomes comuns de cavalo no Brookhaven
    local name = model.Name:lower()
    if name:find("horse") or name:find("cavalo") then
        return true
    end

    -- seat direto no modelo (igual bike/cavalo)
    if model:FindFirstChildWhichIsA("Seat", true)
        or model:FindFirstChildWhichIsA("VehicleSeat", true) then
        return true
    end

    return false
end

-- ===== CAR SPEED =====
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

-- ===== HORSE SPEED =====
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

-- ===== CAR TURBO =====
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

-- ===== BOAT SPEED =====
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

-- ===== APPLY SPEED ALL VEHICLES =====
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

-- ===== APPLY TURBO ALL CARS =====
local function applyTurboAllCars()
    local folder = workspace:FindFirstChild("Vehicles")
    if not folder then return end

    for _, v in pairs(folder:GetChildren()) do
        if v:FindFirstChild("Seats") then
            applyCarTurbo(v)
        end
    end
end

-- ===== PLAYER SPEED (BIKE / SKATE / PATINS) =====
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

-- ===== BOOST ATTACHED MODELS (HOVERBOARD ETC) =====
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

-- ===== UI =====
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



-- ===== AUTO RESET PLAYER SPEED =====

local RunService = game:GetService("RunService")

local usingSpeedItem = false

local function isUsingVehicleOrItem()
    local char = getCharacter()
    local humanoid = char:FindFirstChildWhichIsA("Humanoid")
    if not humanoid then return false end

    -- Se estiver sentado (carro, bike, etc)
    if humanoid.SeatPart then
        return true
    end

    -- Se tiver algum modelo preso ao personagem (hoverboard, skate)
    for _, v in pairs(char:GetChildren()) do
        if v:IsA("Model") and v.PrimaryPart then
            return true
        end
    end

    return false
end

-- Loop leve e seguro
RunService.Heartbeat:Connect(function()
    local char = LocalPlayer.Character
    if not char then return end

    local humanoid = char:FindFirstChildWhichIsA("Humanoid")
    if not humanoid then return end

    local usingNow = isUsingVehicleOrItem()

    -- Começou a usar algo
    if usingNow then
        usingSpeedItem = true

    -- Parou de usar → reseta automaticamente
    elseif usingSpeedItem then
        humanoid.WalkSpeed = defaultWalkSpeed
        usingSpeedItem = false
    end
end)



-- ===== ANTI IMPULSO (BIKE / HORSE / ITEMS) =====

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


local Section = Tab:AddSection({"Spawn Car ( Metheds Kill & Fling )"})

Tab:AddButton({
    Name = "Spawn Bus",
    Description = " ", -- Optional
    Callback = function ()
     local args = {
	"PickingCar",
	"SchoolBus"
}
game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Ca1r"):FireServer(unpack(args))

   print("Button Clicked")
    end
})


Tab:AddButton({
    Name = "Spawn tow truck ( For Fling )",
    Description = " ", -- Optional
    Callback = function ()
        local args = {
	"PickingCar",
	"TowTruck"
}
game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Ca1r"):FireServer(unpack(args))

print("Button Clicked")
    end
})


Tab:AddButton({
    Name = "Spawn truck Car Semi",
    Description = " ", -- Optional
    Callback = function ()
    local args = {
	"PickingCar",
	"Semi"
}
game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Ca1r"):FireServer(unpack(args))

    print("Button Clicked")
    end
})


local Section = Tab:AddSection({"Car Trolls"})

---------------------------------------------------------------------------------------------------------------------------------
                                          -- === Tab: Musica === --
---------------------------------------------------------------------------------------------------------------------------------
local Tab = Window:MakeTab({"Music", "music"}) 
local Section = Tab:AddSection({"Requires GamePass Music"})

local function tocarMusica(id)
    local ReplicatedStorage = game:GetService("ReplicatedStorage")
    
    -- Rádio (ToolMusicText)
    local argsRadio = {
        [1] = "ToolMusicText",
        [2] = id
    }
    ReplicatedStorage:WaitForChild("RE"):WaitForChild("PlayerToolEvent"):FireServer(unpack(argsRadio))
    
    -- Casa (PickHouseMusicText)
    local argsCasa = {
        [1] = "PickHouseMusicText",
        [2] = id
    }
    ReplicatedStorage:WaitForChild("RE"):WaitForChild("1Player1sHous1e"):FireServer(unpack(argsCasa))

    -- Carro (PickingCarMusicText)
    local argsCarro = {
        [1] = "PickingCarMusicText",
        [2] = id
    }
    ReplicatedStorage:WaitForChild("RE"):WaitForChild("1Player1sCa1r"):FireServer(unpack(argsCarro))

    -- Scooter (PickingScooterMusicText)
    local argsScooter = {
        [1] = "PickingScooterMusicText",
        [2] = id
    }
    ReplicatedStorage:WaitForChild("RE"):WaitForChild("1NoMoto1rVehicle1s"):FireServer(unpack(argsScooter))
end

local function isValidMusicId(value)
    return value and value ~= "" and value ~= "Option 1" and not value:match("novas musica adds") and not value:match("musica brasil") and not value:match("musica do meu interece") and not value:match("musica dls por elas") and not value:match("meme abaixo") and not value:match("estourada")
end

Tab:AddTextBox({
    Name = "Music ID",
    PlaceholderText = "Example: 117841711314186",
    Callback = function(value)
        if value and value ~= "" then
            tocarMusica(tostring(value))
        end
    end
})

-- Dropdowns para Tab
local function createMusicDropdown(title, musicOptions, defaultOption)
    local musicNames = {}
    local categoryMap = {}
    for category, sounds in pairs(musicOptions) do
        for _, music in ipairs(sounds) do
            if music.name ~= "" then
                table.insert(musicNames, music.name)
                categoryMap[music.name] = {id = music.id, category = category}
            end
        end
    end

    local function playMusic(soundId)
        tocarMusica(tostring(soundId)) -- Usa a função tocarMusica para tocar em todos os contextos
    end

    Tab:AddDropdown({
        Name = title,
        Description = "",
        Default = defaultOption,
        Multi = false,
        Options = musicNames,
        Callback = function(selectedSound)
            if selectedSound and categoryMap[selectedSound] then
                local soundId = categoryMap[selectedSound].id
                if soundId and soundId ~= "" and soundId ~= "4354908569" then
                    playMusic(soundId)
                end
            end
        end
    })
end

-- Dropdown "Forró"
createMusicDropdown("Forró", {
    ["forro"] = {
        {name = "forró ja cansou", id = "74812784884330"},
        {name = "lenbro ate hoje", id = "71531533552899"},
        {name = "escolha certa", id = "107088620814881"},
        {name = "forró da rezenha", id = "120973520531216"},
        {name = "forró dudu", id = "74404168179733"},
        {name = "forró sao joao", id = "106364874935196"},
        {name = "forró engraçado paia", id = "76524290482399"},
        {name = "100% forro vaquejada", id = "92295159623916"},
        
        {name = "PASTOR MIRIM E A LÍNGUA DOS ANJOS", id = "71153532555470"},
        {name = "PARA NÃO ESQUECER QUEM SOMOS", id = "88937498361674"},
        {name = "Uno zero", id = "112959083808887"},
        {name = "Iate do neymar", id = "135738534706063"},
        {name = "Batidao na aldeia", id = "79953696595578"},
        {name = "", id = ""},
        {name = "", id = ""}
    }
}, "Option 1")

-- Dropdown "Músicas e Memes Aleatório"
createMusicDropdown("Random Music and Memes", {
    ["forro"] = {
        {name = "ANXIETY (Amapiano Re-fix)", id = "101483901475189"}, 
        {name = "Meu corpo, minhas regras", id = "127587901595282"},
        {name = "$$$$gg$$$$gg", id = "137471775091253"},
        {name = "Megalovania but its only the melodies", id = "104500091160463"},
        {name = "androphono strikes back", id = "78312089943968"},
        {name = "Bamm Bamm", id = "128730685516895"},
        {name = "chupa cabra", id = "132890273173295"},
        {name = "longe de mais", id = "124478512057763"},
        {name = "Garoto de Copacabana", id = "135648634110254"},
        {name = "CELL!", id = "117634275895085"},
        {name = "Boa vibe em Ubatuba", id = "139059061493558"},
        {name = "SLIP AWAY", id = "126152928520174"},
        {name = "Alone in Motion", id = "122379348696948"},
        {name = "Fade Away", id = "81002139735874"},
        {name = "Wounds & Wishes", id = "109347979566607"},
        {name = "Ascensão do Monarca", id = "101864243033211"},
        {name = "carro do ovo", id = "3148329638"},
        {name = "ingles bus (fling ou kill bus)", id = "123268013026823"},
        {name = "MIKU MIKU HATSUNE", id = "112783541496955"},
        {name = "Five Nights at Freddy's", id = "110733765539890"},
        {name = "Rat Dance", id = "133496635668044"},
        {name = "Escalando a Seleção Brasileira para a Copa", id = "116546457407236"},
        {name = "", id = ""},
        {name = "", id = ""},
        {name = "", id = ""},
        {name = "", id = ""},
        {name = "", id = ""}
    }
}, "Option 1")

-- Dropdown "Funk"
createMusicDropdown("Funk", {
    ["Funk"] = {
        {name = "Mirrors Demo Funk", id = "73295033713326"}, 
        {name = "7 weeks 3 days funk", id = "82149511707056"},
        {name = "sua mulher funk", id = "90844637105538"},
        {name = "fuga na viatura", id = "131891110268352"},
        {name = "funkphonk fumando verde", id = "112143944982807"},
        {name = "cauma xmara", id = "95664293972405"},
        {name = "que que sharke", id = "129546408528391"},
        {name = "Il Cacto Hipopotamo FUNK", id = "104491656009142"},
        {name = "Espressora Signora FUNK", id = "123394392737234"},
        {name = "trippi troop funk", id = "73049389767013"},
        {name = "bombini funkphonk", id = "88814770244609"},
        {name = "pre treino", id = "136869502216760"},
        {name = "CVRL", id = "124244582950595"},
        {name = "batida Brega Violino (Beat Brega Funk)", id = "99399643204701"},
        {name = "Dança do Canguru (Pke Gaz1nh)", id = "86876136192157"},
        {name = "espere 30segundos!! Ondas sonoras", id = "127757321382838"},
        {name = "MONTAGEM ARABIANA (Pke Gaz1nh)", id = "78076624091098"},
        {name = "Manda o papo (NGI)", id = "132642647937688"},
        {name = "Viver bem", id = "82805460494325"},
        {name = "Faixa estronda", id = "121187736532042"},
        {name = "Ritmo Pixelado", id = "93928823862203"},
        {name = "Viagem Sonora", id = "79349174602261"},
        {name = "Melodia Virtual", id = "139147474886402"},
        {name = "Melodia Serena", id = "97011217688307"},
        {name = "SENTA", id = "124085422276732"},
        {name = "TUNG TUNG TUNG TUNG SAHUR PHONK BRASILEIRO", id = "120353876640055"},
        {name = "crazy-lol", id = "106958630419629"},
        {name = "V7", id = "80348640826643"},
        {name = "UIUAH", id = "82894376737849"},
        {name = "meta ritmo", id = "110091098283354"},
        {name = "CAPPUCCINO ASSASSINO (SPEDUP)", id = "132733033157915"},
        {name = "haha (NGI)", id = "122114766584918"},
        {name = "DO PO", id = "114207745067816"},
        {name = "", id = ""},
        {name = "", id = ""},
        {name = "", id = ""},
        {name = "", id = ""},
        {name = "", id = ""},
        {name = "", id = ""},
        {name = "", id = ""},
        {name = "", id = ""},
        {name = "", id = ""},
        {name = "", id = ""},
        {name = "", id = ""},
        {name = "", id = ""}
    }
}, "Option 1")

-- Dropdown "Phonk"
createMusicDropdown("Phonk", {
    ["phonk"] = {
        {name = "Phonk Agressive", id = "117841711314186"},
        {name = "wyles", id = "85385155970460"},
        {name = "phonk kawai", id = "91502410121438"},
        {name = "querendo da a bucet@", id = "72720721570850"},
        {name = "vem no pocpoc", id = "102333419023382"},
        {name = "tatiu wim", id = "122871512353520"},
        {name = "novinha sapeca", id = "111668097052966"},
        {name = "novinha representa", id = "93786060174790"},
        {name = "phonk1", id = "77501611905348"},
        {name = "phonk2", id = "126887144190812"},
        {name = "phonk osadia", id = "88033569921555"},
        {name = "phonk sarra", id = "132436320685732"},
        {name = "relaionamento sem crush", id = "105832154444494"},
        {name = "phonk3", id = "90323407842935"},
        {name = "novinha dançapanpa", id = "132245626038510"},
        {name = "phonk sexoagreçivo", id = "111995323199676"},
        {name = "phonk4", id = "115016589376700"},
        {name = "phonk5", id = "118740708757685"},
        {name = "phonk6", id = "139435437308948"},
        {name = "phonk chapaquente", id = "109189438638906"},
        {name = "phonk rajada", id = "105126065014034"},
        {name = "rede globo", id = "138487820505005"},
        {name = "phonk indiano", id = "87968531262747"},
        {name = "vapo do vapo", id = "106317184644394"},
        {name = "tutatatutata", id = "112068892721408"},
        {name = "phonk slower", id = "122852029094656"},
        {name = "phonk9", id = "91760524161503"},
        {name = "phonk10", id = "73140398421340"},
        {name = "phonk11", id = "137962454483542"},
        {name = "phonk12", id = "84733736048142"},
        {name = "phonk13", id = "106322173003761"},
        {name = "phonk14", id = "94604796823780"},
        {name = "phonk15", id = "118063577904953"},
        {name = "phonk16", id = "115567432786512"},
        {name = "phonk toq", id = "71304501822029"},
        {name = "phonk hey", id = "132218979961283"},
        {name = "phonk17", id = "102708912256857"},
        {name = "phonk18", id = "140642559093189"},
        {name = "phonk neve", id = "13530439660"},
        {name = "phonk19", id = "87863924786534"},
        {name = "phonk20", id = "133135085604736"},
        {name = "phonk lento", id = "97258811783169"},
        {name = "phonk21", id = "92308400487695"},
        {name = "tipo wym", id = "88064647826500"},
        {name = "estouradassa1", id = "92175624643620"},
        {name = "estouradassa2", id = "108099943758978"},
        {name = "Naaaaa", id = "109784877184952"},
        {name = "trem", id = "114608169341947"},
        {name = "eoropa", id = "111346133543699"},
        {name = "atimosphekika", id = "77857496821844"},
        {name = "phonk ALL THE TIME", id = "123809083385992"},
        {name = "Lifelong Memory", id = "81929101024622"},
        {name = "Automotivo Blondie (Pke Gaz1nh)", id = "74564219749776"},
        {name = "สวัสดีคนไทย v2", id =  "118225359190317"},
        {name = "MTG TU VAI SENTAR (Pke Gaz1nh)", id = "115317874112657"},
        {name = "SARRA FUNK", id = "96249826607044"},
        {name = "Catuquanvan", id = "88038595663211"},
        {name = "F-D-1 (slowed)", id = "124958445624871"},
        {name = "Sucessagem", id = "88551699463723"},
        {name = "ILOVE phonksla", id = "82148953715595"},
        {name = "SPEED SLIDE", id = "118959437310311"},
        {name = "TOMA FUNK PHONK", id = "126291069838831"},
        {name = "PASSO BEM SOLTO X NEW JAZZ", id = "122706595087279"},
        {name = "MONTAGEM BIONICA DIAMANTE", id = "122338822665007"},
        {name = "BALA SELVAGEM!", id = "96180057167470"},
        {name = "Luz <3", id = "74281337525581"},
        {name = "COMO TU", id = "86928685812280"},
        {name = "MONTAGEM SOLAR TROPICANO (SPEED UP)", id = "116461681407294"},
        {name = "MONTAGEM SOLAR TROPICANO (SLOWED)", id = "109308273341422"},
        {name = "YO DE TI", id = "125181345407169"},
        {name = "Beauty, (Phonk), Super sped up", id = "71123357599630"},
        {name = "MONTAGEM BOOMBOX DO MALA FUNK", id = "86537505028256"},
        {name = "BRAZIL DO FUNK", id = "133498554139200"},
        {name = "BRR BRR PATAPIM FUNK", id = "117170901476451"},
        {name = "MONTAGEM TERRA BELA FUNK", id = "134770548505933"},
        {name = "FUNK DO RAVE 1.0", id = "137135395010424"},
        
        {name = " Portao Funk", id = "70900514961735"},
        {name = " Espaço Funk", id = "110519906029322"},
        {name = " FUTABA", id = "91834632690710"},
        {name = " Melódica Explosão De Melodia", id = "98371771055411"},
        {name = " RASGO", id = "98267810117949"},
        {name = " HIPNOTIZA", id = "117668905142866"},
        {name = "CRISTAL NOTURNO", id = "103695219371872"},
        {name = " SKY HIGH", id = "123517126955383"},
        {name = "MIKU top", id = "102771149931910"},
        {name = " ACABU SO FUNK", id = "127870227978818"},
        {name = "CREATIFE FUNK", id = "130525387712209"},
        {name = "GOTH FUNK", id = "97662362226511"},
        {name = "PORTUGESE FUNK", id = "125858109122379"},
        {name = "SUBURBANA", id = "139825057894568"},
        {name = "ESPERA LA NOCHE FUNK", id = "139768056738146"},
        {name = "SIN PERMISO FUNK", id = "92572896648274"},
        {name = "MONTAGEM DACE RAT", id = "98711199754623"},
        {name = " LOVELY FUNK", id = "130633105268814"},
        {name = "STORYMODECOOL", id = "87115976125426"},
        {name = "BLACK COFFEE FUNK", id = "82705137378395"},
        {name = "KOBALT", id = "79381341943021"},
        {name = " andante bacterial", id = "105882833374061"},
        {name = "ANGEL Speed Up", id = "139593870988593"},
        {name = "LUTA ÉPICA", id = "73966367524216"},
        {name = "MALDITA", id = "133814632960968"},
        {name = "DA ZONA NTJ VERSON", id = "105770593501071"},
        {name = "HIPNOTIZA", id = "132015050363205"},
        {name = "MIDZUKI speed up", id = "129151948619922"},
        
        {name = "movimenta funk", id = "114994598691121"},
        {name = "CRISTAL", id = "103445348511856"},
        {name = "Letero funkphonk", id = "99409598156364"},
        {name = "", id = ""},
        {name = "", id = ""},
        {name = "", id = ""},
        {name = "", id = ""},
        {name = "", id = ""},
        {name = "", id = ""},
        {name = "", id = ""},
        {name = "", id = ""},
        {name = "", id = ""}
    }
}, "Option 1")

Tab:AddButton({
    Name = "Stop",
    Description = "",
    Callback = function()
        tocarMusica("")
    end
})

---------------------------------------------------------------------------------------------------------------------------------
                                                   -- === Tab: Protections === --
---------------------------------------------------------------------------------------------------------------------------------
local Tab = Window:MakeTab({"Protections", "Shield"})
local Section = Tab:AddSection({"Advanced Protections"})

local RemoteEvent = Services.ReplicatedStorage:WaitForChild("RE"):WaitForChild("1Playe1rTrigge1rEven1t")
local ClearToolsEvent = Services.ReplicatedStorage:WaitForChild("RE"):WaitForChild("1Clea1rTool1s")

getgenv().AntiToolAllActive = false
getgenv().AntiToolSingleActive = false

local singlePlayerConnection = nil
local allPlayersConnections = {}

local function fastRemote(tool, targetPlayer)
    pcall(function()
        if not tool or not tool:IsA("Tool") or not targetPlayer then return end
        
        for i = 1, 3 do
            task.spawn(function()
                RemoteEvent:FireServer("AcceptedToolToServer", tool.Name, targetPlayer)
            end)
        end
        
        task.spawn(function()
            ClearToolsEvent:FireServer("ClearAllTools")
        end)
    end)
end

local function scanTools(player, char)
    pcall(function()
        if not char then return end
        for _, child in ipairs(char:GetChildren()) do
            if child:IsA("Tool") then
                task.spawn(fastRemote, child, player)
            end
        end
    end)
end

local function monitorSinglePlayer(player)
    pcall(function()
        if player == LocalPlayer then return end
        
        local connections = {}
        
        if player.Character then
            scanTools(player, player.Character)
            table.insert(connections, player.Character.ChildAdded:Connect(function(tool)
                if tool:IsA("Tool") and getgenv().AntiToolSingleActive then
                    task.spawn(fastRemote, tool, player)
                end
            end))
        end
        
        table.insert(connections, player.CharacterAdded:Connect(function(char)
            scanTools(player, char)
            table.insert(connections, char.ChildAdded:Connect(function(tool)
                if tool:IsA("Tool") and getgenv().AntiToolSingleActive then
                    task.spawn(fastRemote, tool, player)
                end
            end))
        end))
        
        table.insert(connections, task.spawn(function()
            while getgenv().AntiToolSingleActive and player.Parent == Services.Players do
                if player.Character then
                    scanTools(player, player.Character)
                end
                task.wait(0.2)
            end
        end))
        
        return connections
    end)
    return {}
end

local function disconnectSinglePlayer()
    pcall(function()
        if singlePlayerConnection then
            for _, conn in ipairs(singlePlayerConnection) do
                if typeof(conn) == "RBXScriptConnection" and conn.Connected then 
                    conn:Disconnect() 
                elseif typeof(conn) == "thread" then
                    task.cancel(conn)
                end
            end
            singlePlayerConnection = nil
        end
    end)
end

local function monitorAllPlayers(player)
    pcall(function()
        if player == LocalPlayer then return end
        if allPlayersConnections[player] then return end
        
        local connections = {}
        allPlayersConnections[player] = connections
        
        if player.Character then
            scanTools(player, player.Character)
            table.insert(connections, player.Character.ChildAdded:Connect(function(tool)
                if tool:IsA("Tool") and getgenv().AntiToolAllActive then
                    task.spawn(fastRemote, tool, player)
                end
            end))
        end
        
        table.insert(connections, player.CharacterAdded:Connect(function(char)
            scanTools(player, char)
            table.insert(connections, char.ChildAdded:Connect(function(tool)
                if tool:IsA("Tool") and getgenv().AntiToolAllActive then
                    task.spawn(fastRemote, tool, player)
                end
            end))
        end))
        
        table.insert(connections, task.spawn(function()
            while getgenv().AntiToolAllActive and player.Parent == Services.Players do
                if player.Character then
                    scanTools(player, player.Character)
                end
                task.wait(0.2)
            end
        end))
    end)
end

local function disconnectAllPlayers()
    pcall(function()
        for _, conns in pairs(allPlayersConnections) do
            for _, conn in ipairs(conns) do
                if typeof(conn) == "RBXScriptConnection" and conn.Connected then 
                    conn:Disconnect() 
                elseif typeof(conn) == "thread" then
                    task.cancel(conn)
                end
            end
        end
        table.clear(allPlayersConnections)
    end)
end

Tab:AddToggle({
    Name = "Ant Tool (local)",
    Default = false,
    Callback = function(state)
        pcall(function()
            getgenv().AntiToolSingleActive = state
            
            if state then
                if not selectedPlayerNameFlings or selectedPlayerNameFlings == "" then
                    getgenv().AntiToolSingleActive = false
                    return
                end
                
                local targetPlayer = Services.Players:FindFirstChild(selectedPlayerNameFlings)
                
                if not targetPlayer then
                    getgenv().AntiToolSingleActive = false
                    return
                end
                
                singlePlayerConnection = monitorSinglePlayer(targetPlayer)
            else
                disconnectSinglePlayer()
            end
        end)
    end
})

Tab:AddToggle({
    Name = "Ant Tool (all)",
    Default = false,
    Callback = function(state)
        pcall(function()
            getgenv().AntiToolAllActive = state
            
            if state then
                for _, player in ipairs(Services.Players:GetPlayers()) do
                    if player ~= LocalPlayer then
                        monitorAllPlayers(player)
                    end
                end
                
                if not allPlayersConnections["_listener"] then
                    allPlayersConnections["_listener"] = {
                        Services.Players.PlayerAdded:Connect(function(player)
                            if getgenv().AntiToolAllActive then
                                monitorAllPlayers(player)
                            end
                        end)
                    }
                end
            else
                disconnectAllPlayers()
            end
        end)
    end
})

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



local vGame = game
local vGetService = vGame.GetService
local vPlayers = vGetService(vGame, "Players")
local vLocalPlayer = vPlayers.LocalPlayer
local vWaitForChild = vLocalPlayer.WaitForChild
local vPlayerScripts = vWaitForChild(vLocalPlayer, "PlayerScripts")

local vEnabled = false
local vConnection = nil
local vScriptName = "BulletVisualizerScript"
local vLocalScriptType = "LocalScript"
local vScriptType = "Script"
local vEventName = "ChildAdded"
local vNameProperty = "Name"
local vIpairs = ipairs
local vTask = task
local vTaskDefer = vTask.defer
local vNil = nil
local vTrue = true
local vFalse = false
local vIsA = "IsA"
local vDestroy = "Destroy"
local vDisconnect = "Disconnect"
local vConnect = "Connect"
local vGetChildren = "GetChildren"

local function vEnableAntiGlitch()
    local vCurrentConnection = vConnection
    if vCurrentConnection then 
        local vOldConnection = vCurrentConnection
        local vDisconnectMethod = vOldConnection[vDisconnect]
        vDisconnectMethod(vOldConnection)
    end
    local vScriptsObject = vPlayerScripts
    local vEvent = vScriptsObject[vEventName]
    local vConnectMethod = vEvent[vConnect]
    local vNewConnection = vConnectMethod(vEvent, function(vChild)
        local vChildObject = vChild
        local vChildName = vChildObject[vNameProperty]
        local vTargetName = vScriptName
        if vChildName == vTargetName then
            local vDeferFunction = vTaskDefer
            vDeferFunction(function()
                local vScriptObject = vChildObject
                local vIsAMethod = vScriptObject[vIsA]
                local vLocalType = vLocalScriptType
                local vIsLocalScript = vIsAMethod(vScriptObject, vLocalType)
                local vScriptTypeCheck = vScriptType
                local vIsScript = vIsAMethod(vScriptObject, vScriptTypeCheck)
                local vShouldDestroy = vIsLocalScript or vIsScript
                if vShouldDestroy then
                    local vScriptToDestroy = vScriptObject
                    local vDestroyMethod = vScriptToDestroy[vDestroy]
                    vDestroyMethod(vScriptToDestroy)
                end
            end)
        end
    end)
    vConnection = vNewConnection
    
    local vScriptsContainer = vPlayerScripts
    local vGetChildrenMethod = vScriptsContainer[vGetChildren]
    local vChildren = vGetChildrenMethod(vScriptsContainer)
    local vIterator = vIpairs
    for vIndex, vChildItem in vIterator(vChildren) do
        local vItemObject = vChildItem
        local vItemName = vItemObject[vNameProperty]
        local vTargetScriptName = vScriptName
        if vItemName == vTargetScriptName then
            local vItemIsAMethod = vItemObject[vIsA]
            local vLocalScriptCheck = vLocalScriptType
            local vItemIsLocalScript = vItemIsAMethod(vItemObject, vLocalScriptCheck)
            local vScriptCheck = vScriptType
            local vItemIsScript = vItemIsAMethod(vItemObject, vScriptCheck)
            local vShouldDestroyItem = vItemIsLocalScript or vItemIsScript
            if vShouldDestroyItem then
                local vItemToDestroy = vItemObject
                local vItemDestroyMethod = vItemToDestroy[vDestroy]
                vItemDestroyMethod(vItemToDestroy)
            end
        end
    end
end

local function vDisableAntiGlitch()
    local vCurrentConnection = vConnection
    if vCurrentConnection then
        local vConnectionToDisconnect = vCurrentConnection
        local vDisconnectMethod = vConnectionToDisconnect[vDisconnect]
        vDisconnectMethod(vConnectionToDisconnect)
        local vNilValue = vNil
        vConnection = vNilValue
    end
end

---------------------------------------------------------------------------------------------------------------------------------
                                                   -- === Tab: Troll === --
---------------------------------------------------------------------------------------------------------------------------------
local Tab = Window:MakeTab({"Troll", "skull"}) 
Tab:AddSection({"Troll Functions in the Player"})

Tab:AddParagraph({"Attention","These Functions are in (Beta)"})

-- Variáveis globais
local SelectedPlayer = nil
local ViewConnection = nil
local LoopTeleportConnection = nil
local flingActive = false
local currentFlingThread = nil
local currentSpin = nil

-- Função para obter lista de jogadores
local function GetPlayers()
    local playerNames = {}
    for _, player in pairs(game.Players:GetPlayers()) do
        if player ~= game.Players.LocalPlayer then
            table.insert(playerNames, player.Name)
        end
    end
    return playerNames
end

-- Função para verificar se o jogador selecionado é válido
local function IsValidPlayer()
    return SelectedPlayer and game.Players:FindFirstChild(SelectedPlayer) ~= nil
end

-- Função para obter o character do jogador selecionado
local function GetSelectedPlayerCharacter()
    if not IsValidPlayer() then return nil end
    return game.Players[SelectedPlayer].Character
end

-- Função para obter o HumanoidRootPart do jogador selecionado
local function GetSelectedPlayerHRP()
    local char = GetSelectedPlayerCharacter()
    return char and char:FindFirstChild("HumanoidRootPart")
end

-- Dropdown principal para seleção de jogador
local DropdownPlayers = Tab:AddDropdown({
    Name = "Target Player",
    Description = " ",
    Options = GetPlayers(),
    Default = "",
    Flag = "dropdown_players",
    Callback = function(Value)
        SelectedPlayer = Value
        print("Player selected:", Value)
    end
})

-- Botão para atualizar lista de jogadores
Tab:AddButton({
    Name = "Update Players List",
    Description = " ", 
    Callback = function()
        DropdownPlayers:Refresh(GetPlayers())
        print("Player list updated!")
    end
})

-- Função para visualizar jogador
Tab:AddToggle({
    Name = "View Player (Head)",
    Description = " ", 
    Callback = function(state)
        local cam = workspace.CurrentCamera
        
        if ViewConnection then
            ViewConnection:Disconnect()
            ViewConnection = nil
        end
        
        if state then
            ViewConnection = game:GetService("RunService").Heartbeat:Connect(function()
                if IsValidPlayer() then
                    local targetPlayer = game.Players[SelectedPlayer]
                    if targetPlayer.Character and targetPlayer.Character:FindFirstChild("Head") then
                        cam.CFrame = CFrame.lookAt(cam.CFrame.Position, targetPlayer.Character.Head.Position)
                        cam.CameraSubject = targetPlayer.Character.Head
                    end
                end
            end)
        else
            local localPlayer = game.Players.LocalPlayer
            if localPlayer.Character and localPlayer.Character:FindFirstChild("Humanoid") then
                cam.CameraSubject = localPlayer.Character.Humanoid
            end
        end
    end,
    Default = false, 
    Flag = "view_player_toggle"
})

-- Função para teleporte em loop
Tab:AddToggle({
    Name = "Loop Teleport Player Target",
    Description = " ", 
    Callback = function(state)
        if LoopTeleportConnection then
            LoopTeleportConnection:Disconnect()
            LoopTeleportConnection = nil
        end
        
        if state then
            LoopTeleportConnection = game:GetService("RunService").Heartbeat:Connect(function()
                if IsValidPlayer() then
                    local targetPlayer = game.Players[SelectedPlayer]
                    local targetChar = targetPlayer.Character
                    local myChar = game.Players.LocalPlayer.Character

                    if targetChar and myChar and targetChar:FindFirstChild("HumanoidRootPart") and myChar:FindFirstChild("HumanoidRootPart") then
                        myChar.HumanoidRootPart.CFrame = targetChar.HumanoidRootPart.CFrame + Vector3.new(2, 0, 0)
                    end
                end
            end)
        end
    end,
    Default = false, 
    Flag = "loop_teleport_toggle"
})

-- Função para teleporte único
Tab:AddButton({
    Name = "Teleport to Player",
    Callback = function()
        local player = game.Players.LocalPlayer
        local target = game.Players:FindFirstChild(SelectedPlayer)
        
        if not player.Character then return end
        if not target or not target.Character then 
            warn("Jogador alvo não encontrado!")
            return 
        end
        
        local playerHRP = player.Character:FindFirstChild("HumanoidRootPart")
        local targetHRP = target.Character:FindFirstChild("HumanoidRootPart")
        
        if playerHRP and targetHRP then
            playerHRP.CFrame = targetHRP.CFrame * CFrame.new(3, 0, 0)
        else
            warn("HumanoidRootPart não encontrado!")
        end
    end
})

Tab:AddSection({"Troll Props Functions"})

Tab:AddButton({
    Name = "Kill Target (Prop)",
    Description = "",
    Callback = function()
        local Players = game:GetService("Players")
        local LocalPlayer = Players.LocalPlayer
        local char = LocalPlayer.Character or LocalPlayer.CharacterAdded:Wait()
        local hrp = char:WaitForChild("HumanoidRootPart")
        
        for i = 1, 10 do

            local args1 = {
                "RequestingPropName",
                "FurnitureBleachers",
                "Furniture"
            }
            game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Clea1rTool1s"):FireServer(unpack(args1))
            
            local args2 = {
                "PickingTools",
                "PropMaker"
            }
            game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Too1l"):InvokeServer(unpack(args2))
            
            task.wait(0.1)
            
            local tool = LocalPlayer.Backpack:WaitForChild("PropMaker")
            tool.Parent = char
            
            local frente = hrp.CFrame.LookVector * (6 + (i * 2))
            local offsetDireita = hrp.CFrame.RightVector * (math.random(-5, 5))
            local pos = hrp.Position + frente + offsetDireita
            
            local args3 = {
                workspace:WaitForChild("Model"):WaitForChild("Sidewalk"),
                Vector3.new(pos.X, pos.Y, pos.Z)
            }
            tool:WaitForChild("Tool_PropMake"):FireServer(unpack(args3))
            
            task.wait(0.1)
        end
        
        task.wait(0.5)
        local PropFolder = workspace:FindFirstChild("WorkspaceCom") and workspace.WorkspaceCom:FindFirstChild("001_TrafficCones")
        if PropFolder then
            for _, prop in pairs(PropFolder:GetChildren()) do
                if prop.Name:find("Prop") then
                    local remote = prop:FindFirstChild("SetCurrentCFrame")
                    if remote then
                        pcall(function()
                            remote:InvokeServer(CFrame.new(0, -9999, 0))
                        end)
                    end
                end
            end
        end
    end
})

Tab:AddButton({
    Name = "Bring Target (Prop)",
    Description = "",
    Callback = function()
        local Players = game:GetService("Players")
        local LocalPlayer = Players.LocalPlayer
        local char = LocalPlayer.Character or LocalPlayer.CharacterAdded:Wait()
        local hrp = char:WaitForChild("HumanoidRootPart")
        
        for i = 1, 10 do
    
            local args1 = {
                "RequestingPropName",
                "FurnitureBleachers",
                "Furniture"
            }
            game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Clea1rTool1s"):FireServer(unpack(args1))
            
            local args2 = {
                "PickingTools",
                "PropMaker"
            }
            game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Too1l"):InvokeServer(unpack(args2))
            
            task.wait(0.1)
            
            local tool = LocalPlayer.Backpack:WaitForChild("PropMaker")
            tool.Parent = char
            
            local angulo = (i / 10) * math.pi * 2
            local raio = 8
            local offsetX = math.cos(angulo) * raio
            local offsetZ = math.sin(angulo) * raio
            local pos = hrp.Position + Vector3.new(offsetX, 0, offsetZ)
            
            local args3 = {
                workspace:WaitForChild("Model"):WaitForChild("Sidewalk"),
                Vector3.new(pos.X, pos.Y, pos.Z)
            }
            tool:WaitForChild("Tool_PropMake"):FireServer(unpack(args3))
            
            task.wait(0.1)
        end
        
        task.wait(0.5)
        local PropFolder = workspace:FindFirstChild("WorkspaceCom") and workspace.WorkspaceCom:FindFirstChild("001_TrafficCones")
        if PropFolder then
            for _, prop in pairs(PropFolder:GetChildren()) do
                if prop.Name:find("Prop") then
                    local remote = prop:FindFirstChild("SetCurrentCFrame")
                    if remote then
                        pcall(function()
                            remote:InvokeServer(hrp.CFrame * CFrame.new(0, 0, -2))
                        end)
                    end
                end
            end
        end
    end
})

Tab:AddSection({"Fuctions Couch (All Beta)"})

local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local VirtualInputManager = game:GetService("VirtualInputManager")
local LocalPlayer = Players.LocalPlayer
local cam = workspace.CurrentCamera

local function executeKill()
    if not IsValidPlayer() then
        warn("No player selected!")
        return
    end
    
    local target = Players:FindFirstChild(SelectedPlayer)
    
    if not target or not target.Character then
        return
    end

    local myChar = LocalPlayer.Character
    if not myChar then
        return
    end
    
    local humanoid = myChar:FindFirstChildOfClass("Humanoid")
    local rootPart = myChar:FindFirstChild("HumanoidRootPart")
    local targetRoot = target.Character:FindFirstChild("HumanoidRootPart")
    
    if not humanoid or not rootPart or not targetRoot then
        return
    end

    local startPos = rootPart.Position
    local deathPos = Vector3.new(145.51, -350.09, 21.58)

    pcall(function()
        ReplicatedStorage.RE["1Clea1rTool1s"]:FireServer("ClearAllTools")
    end)
    
    wait(0.2)
    
    pcall(function()
        ReplicatedStorage.RE["1Too1l"]:InvokeServer("PickingTools", "Couch")
    end)
    
    wait(0.3)

    local couchTool = LocalPlayer.Backpack:FindFirstChild("Couch")
    if couchTool then
        couchTool.Parent = myChar
    end
    
    wait(0.1)
    
    pcall(function()
        VirtualInputManager:SendKeyEvent(true, Enum.KeyCode.F, false, game)
    end)
    
    wait(0.1)

    humanoid:SetStateEnabled(Enum.HumanoidStateType.Seated, false)
    humanoid.PlatformStand = false
    
    if target.Character:FindFirstChild("Head") then
        cam.CameraSubject = target.Character.Head
    end

    local bodyPos = Instance.new("BodyPosition")
    bodyPos.MaxForce = Vector3.new(4000, 4000, 4000)
    bodyPos.Position = rootPart.Position
    bodyPos.Parent = targetRoot

    spawn(function()
        local rotation = 0
        local timeStart = tick()
        
        while tick() - timeStart < 5 do
            if not target.Character or not target.Character:FindFirstChild("HumanoidRootPart") then
                break
            end
            
            local targetHum = target.Character:FindFirstChildOfClass("Humanoid")
            if targetHum and targetHum.Sit then
                break
            end

            rotation = rotation + 50
            local targetPos = targetRoot.Position + Vector3.new(0, 2, 0)
            
            rootPart.CFrame = CFrame.new(targetPos) * CFrame.Angles(math.rad(rotation), 0, 0)
            bodyPos.Position = rootPart.Position + Vector3.new(2, 0, 0)

            wait()
        end

        if bodyPos then
            bodyPos:Destroy()
        end
        
        humanoid:SetStateEnabled(Enum.HumanoidStateType.Seated, true)
        cam.CameraSubject = humanoid

        for _, part in pairs(myChar:GetDescendants()) do
            if part:IsA("BasePart") then
                part.Velocity = Vector3.new(0, 0, 0)
                part.RotVelocity = Vector3.new(0, 0, 0)
            end
        end

        wait(0.1)
        rootPart.CFrame = CFrame.new(deathPos)
        wait(0.3)

        local tool = myChar:FindFirstChild("Couch")
        if tool then
            tool.Parent = LocalPlayer.Backpack
        end

        wait(0.1)
        pcall(function()
            ReplicatedStorage.RE["1Too1l"]:InvokeServer("PickingTools", "Couch")
        end)
        
        wait(0.2)
        rootPart.CFrame = CFrame.new(startPos)
    end)
end

Tab:AddButton({
    Name = "Kill Target (Couch)",
    Description = " ",
    Callback = function()
        executeKill()
    end
})

Tab:AddToggle({
    Name = "Fling Target (Couch)",
    Description = " ",
    Default = false,
    Callback = function(state)
        flingActive = state
        
        if state then
            if not IsValidPlayer() then
                warn("No player selected!")
                return
            end
            
            local target = Players:FindFirstChild(SelectedPlayer)
            if not target or not target.Character then
                return
            end
            
            local root = LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("HumanoidRootPart")
            local tRoot = target.Character and target.Character:FindFirstChild("HumanoidRootPart")
            
            if not root or not tRoot then
                return
            end
            
            local char = LocalPlayer.Character
            local hum = char:FindFirstChildOfClass("Humanoid")
            local original = root.CFrame

            pcall(function()
                ReplicatedStorage.RE["1Clea1rTool1s"]:FireServer("ClearAllTools")
            end)

            task.wait(0.2)

            local args = {
                [1] = "PickingTools",
                [2] = "Couch"
            }
            
            pcall(function()
                ReplicatedStorage.RE["1Too1l"]:InvokeServer(unpack(args))
            end)

            task.wait(0.3)
            
            local tool = LocalPlayer.Backpack:FindFirstChild("Couch")
            if tool then
                tool.Parent = char
            end
            
            task.wait(0.2)
            
            pcall(function()
                VirtualInputManager:SendKeyEvent(true, Enum.KeyCode.F, false, game)
            end)
            
            task.wait(0.25)

            workspace.FallenPartsDestroyHeight = 0/0
            
            local bv = Instance.new("BodyVelocity")
            bv.Name = "FlingForce"
            bv.Velocity = Vector3.new(9e8, 9e8, 9e8)
            bv.MaxForce = Vector3.new(1/0, 1/0, 1/0)
            bv.Parent = root
            
            hum:SetStateEnabled(Enum.HumanoidStateType.Seated, false)
            hum.PlatformStand = false
            
            if target.Character:FindFirstChild("Head") then
                cam.CameraSubject = target.Character.Head
            end

            task.spawn(function()
                local angle = 0
                
                while flingActive and target and target.Character do
                    local tHum = target.Character:FindFirstChildOfClass("Humanoid")
                    if not tHum or tHum.Sit then 
                        break 
                    end
                    
                    if not target.Character:FindFirstChild("HumanoidRootPart") then
                        break
                    end
                    
                    angle = angle + 50

                    local targetRootPart = target.Character.HumanoidRootPart
                    local pos_x = targetRootPart.Position.X + (targetRootPart.Velocity.X / 1.5)
                    local pos_y = targetRootPart.Position.Y + (targetRootPart.Velocity.Y / 1.5)
                    local pos_z = targetRootPart.Position.Z + (targetRootPart.Velocity.Z / 1.5)
                    
                    root.CFrame = CFrame.new(pos_x, pos_y, pos_z) * CFrame.Angles(math.rad(angle), 0, 0)
                    root.Velocity = Vector3.new(9e8, 9e8, 9e8)
                    root.RotVelocity = Vector3.new(9e8, 9e8, 9e8)
                    
                    task.wait()
                end
                
                flingActive = false
                
                if bv then
                    bv:Destroy()
                end
                
                hum:SetStateEnabled(Enum.HumanoidStateType.Seated, true)
                hum.PlatformStand = false
                root.CFrame = original
                cam.CameraSubject = hum
                
                for _, p in pairs(char:GetDescendants()) do
                    if p:IsA("BasePart") then
                        p.Velocity = Vector3.zero
                        p.RotVelocity = Vector3.zero
                    end
                end
                
                hum:UnequipTools()
                
                pcall(function()
                    ReplicatedStorage.RE["1Too1l"]:InvokeServer(unpack(args))
                end)
            end)
        end
    end
})

local function executeJail()
    if not IsValidPlayer() then
        warn("No player selected!")
        return
    end
    
    local target = Players:FindFirstChild(SelectedPlayer)
    
    if not target or not target.Character then
        return
    end

    local myChar = LocalPlayer.Character
    if not myChar then
        return
    end
    
    local humanoid = myChar:FindFirstChildOfClass("Humanoid")
    local rootPart = myChar:FindFirstChild("HumanoidRootPart")
    local targetRoot = target.Character:FindFirstChild("HumanoidRootPart")
    
    if not humanoid or not rootPart or not targetRoot then
        return
    end

    local startPos = rootPart.Position
    local jailPos = Vector3.new(-1292, 3, -1288)

    pcall(function()
        ReplicatedStorage.RE["1Clea1rTool1s"]:FireServer("ClearAllTools")
    end)
    
    wait(0.2)
    
    pcall(function()
        ReplicatedStorage.RE["1Too1l"]:InvokeServer("PickingTools", "Couch")
    end)
    
    wait(0.3)

    local couchTool = LocalPlayer.Backpack:FindFirstChild("Couch")
    if couchTool then
        couchTool.Parent = myChar
    end
    
    wait(0.1)
    
    pcall(function()
        VirtualInputManager:SendKeyEvent(true, Enum.KeyCode.F, false, game)
    end)
    
    wait(0.1)

    humanoid:SetStateEnabled(Enum.HumanoidStateType.Seated, false)
    humanoid.PlatformStand = false
    
    if target.Character:FindFirstChild("Head") then
        cam.CameraSubject = target.Character.Head
    end

    local bodyPos = Instance.new("BodyPosition")
    bodyPos.MaxForce = Vector3.new(4000, 4000, 4000)
    bodyPos.Position = rootPart.Position
    bodyPos.Parent = targetRoot

    spawn(function()
        local rotation = 0
        local timeStart = tick()
        
        while tick() - timeStart < 5 do
            if not target.Character or not target.Character:FindFirstChild("HumanoidRootPart") then
                break
            end
            
            local targetHum = target.Character:FindFirstChildOfClass("Humanoid")
            if targetHum and targetHum.Sit then
                break
            end

            rotation = rotation + 50
            local targetPos = targetRoot.Position + Vector3.new(0, 2, 0)
            
            rootPart.CFrame = CFrame.new(targetPos) * CFrame.Angles(math.rad(rotation), 0, 0)
            bodyPos.Position = rootPart.Position + Vector3.new(2, 0, 0)

            wait()
        end

        if bodyPos then
            bodyPos:Destroy()
        end
        
        humanoid:SetStateEnabled(Enum.HumanoidStateType.Seated, true)
        cam.CameraSubject = humanoid

        for _, part in pairs(myChar:GetDescendants()) do
            if part:IsA("BasePart") then
                part.Velocity = Vector3.new(0, 0, 0)
                part.RotVelocity = Vector3.new(0, 0, 0)
            end
        end

        wait(0.1)
        rootPart.CFrame = CFrame.new(jailPos)
        wait(0.3)

        local tool = myChar:FindFirstChild("Couch")
        if tool then
            tool.Parent = LocalPlayer.Backpack
        end

        wait(0.1)
        pcall(function()
            ReplicatedStorage.RE["1Too1l"]:InvokeServer("PickingTools", "Couch")
        end)
        
        wait(0.2)
        rootPart.CFrame = CFrame.new(startPos)
    end)
end

Tab:AddButton({
    Name = "Jail Target (Couch)",
    Description = " ",
    Callback = function()
        executeJail()
    end
})

local function VoidPlayer()
    if not IsValidPlayer() then
        warn("No player selected!")
        return
    end
    
    local target = Players:FindFirstChild(SelectedPlayer)
    
    if not target or not target.Character then
        return
    end

    local myChar = LocalPlayer.Character
    if not myChar then
        return
    end
    
    local humanoid = myChar:FindFirstChildOfClass("Humanoid")
    local rootPart = myChar:FindFirstChild("HumanoidRootPart")
    local targetRoot = target.Character:FindFirstChild("HumanoidRootPart")
    
    if not humanoid or not rootPart or not targetRoot then
        return
    end

    local startPos = rootPart.Position
    local jailPos = Vector3.new(487, -77, 129)

    pcall(function()
        ReplicatedStorage.RE["1Clea1rTool1s"]:FireServer("ClearAllTools")
    end)
    
    wait(0.2)
    
    pcall(function()
        ReplicatedStorage.RE["1Too1l"]:InvokeServer("PickingTools", "Couch")
    end)
    
    wait(0.3)

    local couchTool = LocalPlayer.Backpack:FindFirstChild("Couch")
    if couchTool then
        couchTool.Parent = myChar
    end
    
    wait(0.1)
    
    pcall(function()
        VirtualInputManager:SendKeyEvent(true, Enum.KeyCode.F, false, game)
    end)
    
    wait(0.1)

    humanoid:SetStateEnabled(Enum.HumanoidStateType.Seated, false)
    humanoid.PlatformStand = false
    
    if target.Character:FindFirstChild("Head") then
        cam.CameraSubject = target.Character.Head
    end

    local bodyPos = Instance.new("BodyPosition")
    bodyPos.MaxForce = Vector3.new(4000, 4000, 4000)
    bodyPos.Position = rootPart.Position
    bodyPos.Parent = targetRoot

    spawn(function()
        local rotation = 0
        local timeStart = tick()
        
        while tick() - timeStart < 5 do
            if not target.Character or not target.Character:FindFirstChild("HumanoidRootPart") then
                break
            end
            
            local targetHum = target.Character:FindFirstChildOfClass("Humanoid")
            if targetHum and targetHum.Sit then
                break
            end

            rotation = rotation + 50
            local targetPos = targetRoot.Position + Vector3.new(0, 2, 0)
            
            rootPart.CFrame = CFrame.new(targetPos) * CFrame.Angles(math.rad(rotation), 0, 0)
            bodyPos.Position = rootPart.Position + Vector3.new(2, 0, 0)

            wait()
        end

        if bodyPos then
            bodyPos:Destroy()
        end
        
        humanoid:SetStateEnabled(Enum.HumanoidStateType.Seated, true)
        cam.CameraSubject = humanoid

        for _, part in pairs(myChar:GetDescendants()) do
            if part:IsA("BasePart") then
                part.Velocity = Vector3.new(0, 0, 0)
                part.RotVelocity = Vector3.new(0, 0, 0)
            end
        end

        wait(0.1)
        rootPart.CFrame = CFrame.new(jailPos)
        wait(0.3)

        local tool = myChar:FindFirstChild("Couch")
        if tool then
            tool.Parent = LocalPlayer.Backpack
        end

        wait(0.1)
        pcall(function()
            ReplicatedStorage.RE["1Too1l"]:InvokeServer("PickingTools", "Couch")
        end)
        
        wait(0.2)
        rootPart.CFrame = CFrame.new(startPos)
    end)
end

Tab:AddButton({
    Name = "Void Place Target (Couch)",
    Description = "Execute Void Player (Void Place)",
    Callback = function()
        VoidPlayer()
    end
})

local function SkyPlayer()
    if not IsValidPlayer() then
        warn("No player selected!")
        return
    end
    
    local target = Players:FindFirstChild(SelectedPlayer)
    
    if not target or not target.Character then
        return
    end

    local myChar = LocalPlayer.Character
    if not myChar then
        return
    end
    
    local humanoid = myChar:FindFirstChildOfClass("Humanoid")
    local rootPart = myChar:FindFirstChild("HumanoidRootPart")
    local targetRoot = target.Character:FindFirstChild("HumanoidRootPart")
    
    if not humanoid or not rootPart or not targetRoot then
        return
    end

    local startPos = rootPart.Position
    local jailPos = Vector3.new(-41, 2633, 139)

    pcall(function()
        ReplicatedStorage.RE["1Clea1rTool1s"]:FireServer("ClearAllTools")
    end)
    
    wait(0.2)
    
    pcall(function()
        ReplicatedStorage.RE["1Too1l"]:InvokeServer("PickingTools", "Couch")
    end)
    
    wait(0.3)

    local couchTool = LocalPlayer.Backpack:FindFirstChild("Couch")
    if couchTool then
        couchTool.Parent = myChar
    end
    
    wait(0.1)
    
    pcall(function()
        VirtualInputManager:SendKeyEvent(true, Enum.KeyCode.F, false, game)
    end)
    
    wait(0.1)

    humanoid:SetStateEnabled(Enum.HumanoidStateType.Seated, false)
    humanoid.PlatformStand = false
    
    if target.Character:FindFirstChild("Head") then
        cam.CameraSubject = target.Character.Head
    end

    local bodyPos = Instance.new("BodyPosition")
    bodyPos.MaxForce = Vector3.new(4000, 4000, 4000)
    bodyPos.Position = rootPart.Position
    bodyPos.Parent = targetRoot

    spawn(function()
        local rotation = 0
        local timeStart = tick()
        
        while tick() - timeStart < 5 do
            if not target.Character or not target.Character:FindFirstChild("HumanoidRootPart") then
                break
            end
            
            local targetHum = target.Character:FindFirstChildOfClass("Humanoid")
            if targetHum and targetHum.Sit then
                break
            end

            rotation = rotation + 50
            local targetPos = targetRoot.Position + Vector3.new(0, 2, 0)
            
            rootPart.CFrame = CFrame.new(targetPos) * CFrame.Angles(math.rad(rotation), 0, 0)
            bodyPos.Position = rootPart.Position + Vector3.new(2, 0, 0)

            wait()
        end

        if bodyPos then
            bodyPos:Destroy()
        end
        
        humanoid:SetStateEnabled(Enum.HumanoidStateType.Seated, true)
        cam.CameraSubject = humanoid

        for _, part in pairs(myChar:GetDescendants()) do
            if part:IsA("BasePart") then
                part.Velocity = Vector3.new(0, 0, 0)
                part.RotVelocity = Vector3.new(0, 0, 0)
            end
        end

        wait(0.1)
        rootPart.CFrame = CFrame.new(jailPos)
        wait(0.3)

        local tool = myChar:FindFirstChild("Couch")
        if tool then
            tool.Parent = LocalPlayer.Backpack
        end

        wait(0.1)
        pcall(function()
            ReplicatedStorage.RE["1Too1l"]:InvokeServer("PickingTools", "Couch")
        end)
        
        wait(0.2)
        rootPart.CFrame = CFrame.new(startPos)
    end)
end

Tab:AddButton({
    Name = "Sky Troll Target (Couch)",
    Description = " ",
    Callback = function()
        SkyPlayer()
    end
})

local function PixelPlayer()
    if not IsValidPlayer() then
        warn("No player selected!")
        return
    end
    
    local target = Players:FindFirstChild(SelectedPlayer)
    
    if not target or not target.Character then
        return
    end

    local myChar = LocalPlayer.Character
    if not myChar then
        return
    end
    
    local humanoid = myChar:FindFirstChildOfClass("Humanoid")
    local rootPart = myChar:FindFirstChild("HumanoidRootPart")
    local targetRoot = target.Character:FindFirstChild("HumanoidRootPart")
    
    if not humanoid or not rootPart or not targetRoot then
        return
    end

    local startPos = rootPart.Position
    local jailPos = Vector3.new(764976, 763728, 29970302)

    pcall(function()
        ReplicatedStorage.RE["1Clea1rTool1s"]:FireServer("ClearAllTools")
    end)
    
    wait(0.2)
    
    pcall(function()
        ReplicatedStorage.RE["1Too1l"]:InvokeServer("PickingTools", "Couch")
    end)
    
    wait(0.3)

    local couchTool = LocalPlayer.Backpack:FindFirstChild("Couch")
    if couchTool then
        couchTool.Parent = myChar
    end
    
    wait(0.1)
    
    pcall(function()
        VirtualInputManager:SendKeyEvent(true, Enum.KeyCode.F, false, game)
    end)
    
    wait(0.1)

    humanoid:SetStateEnabled(Enum.HumanoidStateType.Seated, false)
    humanoid.PlatformStand = false
    
    if target.Character:FindFirstChild("Head") then
        cam.CameraSubject = target.Character.Head
    end

    local bodyPos = Instance.new("BodyPosition")
    bodyPos.MaxForce = Vector3.new(4000, 4000, 4000)
    bodyPos.Position = rootPart.Position
    bodyPos.Parent = targetRoot

    spawn(function()
        local rotation = 0
        local timeStart = tick()
        
        while tick() - timeStart < 5 do
            if not target.Character or not target.Character:FindFirstChild("HumanoidRootPart") then
                break
            end
            
            local targetHum = target.Character:FindFirstChildOfClass("Humanoid")
            if targetHum and targetHum.Sit then
                break
            end

            rotation = rotation + 50
            local targetPos = targetRoot.Position + Vector3.new(0, 2, 0)
            
            rootPart.CFrame = CFrame.new(targetPos) * CFrame.Angles(math.rad(rotation), 0, 0)
            bodyPos.Position = rootPart.Position + Vector3.new(2, 0, 0)

            wait()
        end

        if bodyPos then
            bodyPos:Destroy()
        end
        
        humanoid:SetStateEnabled(Enum.HumanoidStateType.Seated, true)
        cam.CameraSubject = humanoid

        for _, part in pairs(myChar:GetDescendants()) do
            if part:IsA("BasePart") then
                part.Velocity = Vector3.new(0, 0, 0)
                part.RotVelocity = Vector3.new(0, 0, 0)
            end
        end

        wait(0.1)
        rootPart.CFrame = CFrame.new(jailPos)
        wait(0.3)

        local tool = myChar:FindFirstChild("Couch")
        if tool then
            tool.Parent = LocalPlayer.Backpack
        end

        wait(0.1)
        pcall(function()
            ReplicatedStorage.RE["1Too1l"]:InvokeServer("PickingTools", "Couch")
        end)
        
        wait(0.2)
        rootPart.CFrame = CFrame.new(startPos)
    end)
end

Tab:AddButton({
    Name = "Pixel Player (Couch)",
    Description = " ",
    Callback = function()
        PixelPlayer()
    end
})
