local redzlib =loadstring(game:HttpGet("https://pastefy.app/q1Cquciw/raw"))()

local Window = redzlib:MakeWindow({
    Title = " Spectra Hub | Blox Fruits",
    SubTitle = "炎  by Denolk | Version Hub 1.0.0",
    Logo = "rbxassetid://15464429993",
    TitleSize = 18.5,
    SaveFolder = "Spectra hub"
})

local MinimizeBtn = Window:AddMinimizeButton({
    Button = {
        Image = "rbxassetid://126286543557523",
        BackgroundTransparency = 0,
        Size = UDim2.new(0, 40, 0, 40),
        ScaleType = Enum.ScaleType.Fit
    },
    Corner = { CornerRadius = UDim.new(35, 1) },
})

--------------------------------------------------------------------------------------------------------------------------------
                                                   -- === Tabs === --
---------------------------------------------------------------------------------------------------------------------------------
local TabInfo = Window:MakeTab({"Info", "info"})
local TabFarm = Window:MakeTab({"Farming", "home"})
local TabFish = Window:MakeTab({"Auto Fishing", "fish"})
local TabItem = Window:MakeTab({"Quest | Items", "swords"})
local TabSea = Window:MakeTab({"Sea Events", "sea"})
local TabAuto = Window:MakeTab({"Auto Stats", "line-chart"})
local TabRaid = Window:MakeTab({"Raids | Fruits", "apple"})
local TabTele = Window:MakeTab({"Teleport", "locate"})
local TabPvp = Window:MakeTab({"PvP | Player", "user"})
local TabEsp = Window:MakeTab({"Esp General", "
eyes"})
local TabShop = Window:MakeTab({"Shop", "shoppingCart"})
local TabGrap = Window:MakeTab({"Graphics", "bar-chart"})
local TabSett = Window:MakeTab({"Settings", "settings"})

spawn(function()
	repeat
		task.wait();
	until game:IsLoaded();
	local ChatService = game:GetService("Chat");
	wait(1);
	((require(game.ReplicatedStorage.Notification)).new("<Color=Purple>[ Welcome " .. game.Players.LocalPlayer.DisplayName .. " ]<Color=/>")):Display();
	wait(1);
	((require(game.ReplicatedStorage.Notification)).new("<Color=Yellow>[Spectra Hub | Blox Fruits]<Color=/>")):Display();
	wait(1);
	((require(game.ReplicatedStorage.Notification)).new("<Color=Red>[Developed by Denolk]<Color=/>")):Display();
end);

-----------------------------------------------------------------------------------------------------------------------------Function

_G.AutoFarm = false
_G.Weapon = "Melee" -- Padrão
_G.Distance = 100
local Speed = 300

local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local TweenService = game:GetService("TweenService")
local player = Players.LocalPlayer

local function Stabilize()
    if not player.Character or not player.Character:FindFirstChild("HumanoidRootPart") then return end
    local hrp = player.Character.HumanoidRootPart
    if not hrp:FindFirstChild("VelocityControl") then
        local bv = Instance.new("BodyVelocity")
        bv.Name = "VelocityControl"
        bv.MaxForce = Vector3.new(9e9, 9e9, 9e9)
        bv.Velocity = Vector3.new(0, 0, 0)
        bv.Parent = hrp
    end
end

local function Unstabilize()
    if player.Character and player.Character.HumanoidRootPart:FindFirstChild("VelocityControl") then
        player.Character.HumanoidRootPart.VelocityControl:Destroy()
    end
end

function topos(Pos)
    local character = player.Character
    if not character or not character:FindFirstChild("HumanoidRootPart") then return end
    
    Stabilize() -- Ativa estabilizador ao mover
    local dist = (Pos.Position - character.HumanoidRootPart.Position).Magnitude
    local tween = TweenService:Create(character.HumanoidRootPart, TweenInfo.new(dist/Speed, Enum.EasingStyle.Linear), {CFrame = Pos})
    

    for _, v in pairs(character:GetChildren()) do
        if v:IsA("BasePart") then v.CanCollide = false end
    end
    
    tween:Play()
    return tween
end

function EquipWeapon()
    local inventory = player.Backpack
    local character = player.Character
    if not character then return end
    
    for _, tool in pairs(inventory:GetChildren()) do
        if tool:IsA("Tool") and tool.ToolTip == _G.Weapon then
            character.Humanoid:EquipTool(tool)
        end
    end
end

--- Sea 1 Missions

function CheckQuest()
    local MyLevel = player.Data.Level.Value
    if MyLevel >= 1 and MyLevel <= 9 then
        return "Bandit", "BanditQuest1", 1, CFrame.new(1059, 15, 1550)
    elseif MyLevel >= 10 and MyLevel <= 14 then
        return "Monkey", "JungleQuest", 1, CFrame.new(-1598, 35, 153)
        elseif MyLevel >= 15 and MyLevel <= 29 then
        return "Gorilla", "JungleQuest", 2, CFrame.new(-1598, 35, 153)
    elseif MyLevel >= 30 and MyLevel <= 39 then
        return "Pirate", "BuggyQuest1", 1, CFrame.new(-1141.07483, 4.10001802, 3831.5498)
    elseif MyLevel >= 40 and MyLevel <= 59 then
        return "Brute", "BuggyQuest1", 2, CFrame.new(-1141.07483, 4.10001802, 3831.5498)
    elseif MyLevel >= 60 and MyLevel <= 74 then
        return "Desert Bandit", "DesertQuest", 1, CFrame.new(894.488647, 5.14000702, 4392.43359)
    elseif MyLevel >= 75 and MyLevel <= 89 then
        return "Desert Officer", "DesertQuest", 2, CFrame.new(894.488647, 5.14000702, 4392.43359)
    elseif MyLevel >= 90 and MyLevel <= 99 then
        return "Snow Bandit", "SnowQuest", 1, CFrame.new(1389.74451, 88.1519318, -1298.90796)
    elseif MyLevel >= 100 and MyLevel <= 119 then
        return "Snowman", "SnowQuest", 2, CFrame.new(1389.74451, 88.1519318, -1298.90796)
    elseif MyLevel >= 120 and MyLevel <= 149 then
        return "Chief Petty Officer", "MarineQuest2", 1, CFrame.new(-5039.58643, 27.3500385, 4324.68018)
    elseif MyLevel >= 150 and MyLevel <= 174 then
        return "Sky Bandit", "SkyQuest", 1, CFrame.new(-4839.53027, 716.368591, -2619.44165)
    elseif MyLevel >= 175 and MyLevel <= 189 then
        return "Dark Master", "SkyQuest", 2, CFrame.new(-4839.53027, 716.368591, -2619.44165)
    elseif MyLevel >= 190 and MyLevel <= 209 then
        return "Prisoner", "PrisonerQuest", 1, CFrame.new(5308.93115, 1.65517521, 475.120514)
    elseif MyLevel >= 210 and MyLevel <= 249 then
        return "Dangerous Prisoner", "PrisonerQuest", 2, CFrame.new(5308.93115, 1.65517521, 475.120514)
    elseif MyLevel >= 250 and MyLevel <= 274 then
        return "Toga Warrior", "ColosseumQuest", 1, CFrame.new(-1580.04663, 6.35000277, -2986.47534)
    elseif MyLevel >= 275 and MyLevel <= 299 then
        return "Gladiator", "ColosseumQuest", 2, CFrame.new(-1580.04663, 6.35000277, -2986.47534)
    elseif MyLevel >= 300 and MyLevel <= 324 then
        return "Military Soldier", "MagmaQuest", 1, CFrame.new(-5313.37012, 10.9500084, 8515.29395)
    elseif MyLevel >= 325 and MyLevel <= 374 then
        return "Military Spy", "MagmaQuest", 2, CFrame.new(-5313.37012, 10.9500084, 8515.29395)
    elseif MyLevel >= 375 and MyLevel <= 399 then
        return "Fishman Warrior", "FishmanQuest", 1, CFrame.new(61122.6523, 18.4974422, 1569.39978)
    elseif MyLevel >= 400 and MyLevel <= 449 then
        return "Fishman Commando", "FishmanQuest", 2, CFrame.new(61122.6523, 18.4974422, 1569.39978)
    elseif MyLevel >= 450 and MyLevel <= 474 then
        return "God's Guard", "SkyExp1Quest", 1, CFrame.new(-4721.88867, 843.874695, -1949.96643)
    elseif MyLevel >= 475 and MyLevel <= 524 then
        return "Shanda", "SkyExp1Quest", 2, CFrame.new(-7859.09814, 5544.19043, -381.476196)
    elseif MyLevel >= 525 and MyLevel <= 549 then
        return "Royal Squad", "SkyExp2Quest", 1, CFrame.new(-7906.81592, 5634.6626, -1411.99194)
    elseif MyLevel >= 550 and MyLevel <= 624 then
        return "Royal Soldier", "SkyExp2Quest", 2, CFrame.new(-7906.81592, 5634.6626, -1411.99194)
    elseif MyLevel >= 625 and MyLevel <= 649 then
        return "Galley Pirate", "FountainQuest", 1, CFrame.new(5259.81982, 37.3500175, 4050.0293)
    elseif MyLevel >= 650 and MyLevel < 700 then
        return "Galley Captain", "FountainQuest", 2, CFrame.new(5259.81982, 37.3500175, 4050.0293)

--- Sea 2 Missions

    elseif MyLevel >= 700 and MyLevel <= 724 then
        return "Raider", "Area1Quest", 1, CFrame.new(-429.543518, 71.7699966, 1836.18188)
    elseif MyLevel >= 725 and MyLevel <= 774 then
        return "Mercenary", "Area1Quest", 2, CFrame.new(-429.543518, 71.7699966, 1836.18188)
    elseif MyLevel >= 775 and MyLevel <= 799 then
        return "Swan Pirate", "Area2Quest", 1, CFrame.new(638.43811, 71.769989, 918.282898)
    elseif MyLevel >= 800 and MyLevel <= 874 then
        return "Factory Staff", "Area2Quest", 2, CFrame.new(632.698608, 73.1055908, 918.666321)
    elseif MyLevel >= 875 and MyLevel <= 899 then
        return "Marine Lieutenant", "MarineQuest3", 1, CFrame.new(-2440.79639, 71.7140732, -3216.06812)
    elseif MyLevel >= 900 and MyLevel <= 949 then
        return "Marine Captain", "MarineQuest3", 2, CFrame.new(-2440.79639, 71.7140732, -3216.06812)
    elseif MyLevel >= 950 and MyLevel <= 974 then
        return "Zombie", "ZombieQuest", 1, CFrame.new(-5497.06152, 47.5923004, -795.237061)
    elseif MyLevel >= 975 and MyLevel <= 999 then
        return "Vampire", "ZombieQuest", 2, CFrame.new(-5497.06152, 47.5923004, -795.237061)
    elseif MyLevel >= 1000 and MyLevel <= 1049 then
        return "Snow Trooper", "SnowMountainQuest", 1, CFrame.new(609.858826, 400.119904, -5372.25928)
    elseif MyLevel >= 1050 and MyLevel <= 1099 then
        return "Winter Warrior", "SnowMountainQuest", 2, CFrame.new(609.858826, 400.119904, -5372.25928)
    elseif MyLevel >= 1100 and MyLevel <= 1124 then
        return "Lab Subordinate", "IceSideQuest", 1, CFrame.new(-6064.06885, 15.2422857, -4902.97852)
    elseif MyLevel >= 1125 and MyLevel <= 1174 then
        return "Horned Warrior", "IceSideQuest", 2, CFrame.new(-6064.06885, 15.2422857, -4902.97852)
    elseif MyLevel >= 1175 and MyLevel <= 1199 then
        return "Magma Ninja", "FireSideQuest", 1, CFrame.new(-5428.03174, 15.0622921, -5299.43457)
    elseif MyLevel >= 1200 and MyLevel <= 1249 then
        return "Lava Pirate", "FireSideQuest", 2, CFrame.new(-5428.03174, 15.0622921, -5299.43457)
    elseif MyLevel >= 1250 and MyLevel <= 1274 then
        return "Ship Deckhand", "ShipQuest1", 1, CFrame.new(1037.80127, 125.092171, 32911.6016)
    elseif MyLevel >= 1275 and MyLevel <= 1299 then
        return "Ship Engineer", "ShipQuest1", 2, CFrame.new(1037.80127, 125.092171, 32911.6016)
    elseif MyLevel >= 1300 and MyLevel <= 1324 then
        return "Ship Steward", "ShipQuest2", 1, CFrame.new(968.80957, 125.092171, 33244.125)
    elseif MyLevel >= 1325 and MyLevel <= 1349 then
        return "Ship Officer", "ShipQuest2", 2, CFrame.new(968.80957, 125.092171, 33244.125)
    elseif MyLevel >= 1350 and MyLevel <= 1374 then
        return "Arctic Warrior", "FrostQuest", 1, CFrame.new(5667.6582, 26.7997818, -6486.08984)
    elseif MyLevel >= 1375 and MyLevel <= 1424 then
        return "Snow Lurker", "FrostQuest", 2, CFrame.new(5667.6582, 26.7997818, -6486.08984)
    elseif MyLevel >= 1425 and MyLevel <= 1449 then
        return "Sea Soldier", "ForgottenQuest", 1, CFrame.new(-3054.44458, 235.544281, -10142.8193)
    elseif MyLevel >= 1450 and MyLevel < 1500 then
        return "Water Fighter", "ForgottenQuest", 2, CFrame.new(-3054.44458, 235.544281, -10142.8193)

--- Sea 3 Missions

    elseif MyLevel >= 1500 and MyLevel <= 1524 then
        return "Pirate Millionaire", "PiratePortQuest", 1, CFrame.new(-290.074677, 42.9034653, 5581.58984)
    elseif MyLevel >= 1525 and MyLevel <= 1574 then
        return "Pistol Billionaire", "PiratePortQuest", 2, CFrame.new(-290.074677, 42.9034653, 5581.58984)
    elseif MyLevel >= 1575 and MyLevel <= 1599 then
        return "Dragon Crew Warrior", "AmazonQuest", 1, CFrame.new(5832.83594, 51.6806107, -1101.51563)
    elseif MyLevel >= 1600 and MyLevel <= 1624 then
        return "Dragon Crew Archer", "AmazonQuest", 2, CFrame.new(5833.1147460938, 51.60498046875, -1103.0693359375)
    elseif MyLevel >= 1625 and MyLevel <= 1649 then
        return "Female Islander", "AmazonQuest2", 1, CFrame.new(5446.8793945313, 601.62945556641, 749.45672607422)
    elseif MyLevel >= 1650 and MyLevel <= 1699 then
        return "Giant Islander", "AmazonQuest2", 2, CFrame.new(5446.8793945313, 601.62945556641, 749.45672607422)
    elseif MyLevel >= 1700 and MyLevel <= 1724 then
        return "Marine Commodore", "MarineTreeIsland", 1, CFrame.new(2180.54126, 27.8156815, -6741.5498)
    elseif MyLevel >= 1725 and MyLevel <= 1774 then
        return "Marine Rear Admiral", "MarineTreeIsland", 2, CFrame.new(2179.98828125, 28.731239318848, -6740.0551757813)
    elseif MyLevel >= 1775 and MyLevel <= 1799 then
        return "Fishman Raider", "DeepForestIsland3", 1, CFrame.new(-10581.6563, 330.872955, -8761.18652)
    elseif MyLevel >= 1800 and MyLevel <= 1824 then
        return "Fishman Captain", "DeepForestIsland3", 2, CFrame.new(-10581.6563, 330.872955, -8761.18652)
    elseif MyLevel >= 1825 and MyLevel <= 1849 then
        return "Forest Pirate", "DeepForestIsland", 1, CFrame.new(-13234.04, 331.488495, -7625.40137)
    elseif MyLevel >= 1850 and MyLevel <= 1899 then
        return "Mythological Pirate", "DeepForestIsland", 2, CFrame.new(-13234.04, 331.488495, -7625.40137)
    elseif MyLevel >= 1900 and MyLevel <= 1924 then
        return "Jungle Pirate", "DeepForestIsland2", 1, CFrame.new(-12680.3818, 389.971039, -9902.01953)
    elseif MyLevel >= 1925 and MyLevel <= 1974 then
        return "Musketeer Pirate", "DeepForestIsland2", 2, CFrame.new(-12680.3818, 389.971039, -9902.01953)
    elseif MyLevel >= 1975 and MyLevel <= 1999 then
        return "Reborn Skeleton", "HauntedQuest1", 1, CFrame.new(-9479.2168, 141.215088, 5566.09277)
    elseif MyLevel >= 2000 and MyLevel <= 2024 then
        return "Living Zombie", "HauntedQuest1", 2, CFrame.new(-9479.2168, 141.215088, 5566.09277)
    elseif MyLevel >= 2025 and MyLevel <= 2049 then
        return "Demonic Soul", "HauntedQuest2", 1, CFrame.new(-9516.99316, 172.017181, 6078.46533)
    elseif MyLevel >= 2050 and MyLevel <= 2074 then
        return "Posessed Mummy", "HauntedQuest2", 2, CFrame.new(-9516.99316, 172.017181, 6078.46533)
    elseif MyLevel >= 2075 and MyLevel <= 2099 then
        return "Peanut Scout", "NutsIslandQuest", 1, CFrame.new(-2104.3908691406, 38.104167938232, -10194.21875)
    elseif MyLevel >= 2100 and MyLevel <= 2124 then
        return "Peanut President", "NutsIslandQuest", 2, CFrame.new(-2104.3908691406, 38.104167938232, -10194.21875)
    elseif MyLevel >= 2125 and MyLevel <= 2149 then
        return "Ice Cream Chef", "IceCreamIslandQuest", 1, CFrame.new(-820.64825439453, 65.819526672363, -10965.795898438)
    elseif MyLevel >= 2150 and MyLevel <= 2199 then
        return "Ice Cream Commander", "IceCreamIslandQuest", 2, CFrame.new(-820.64825439453, 65.819526672363, -10965.795898438)
    elseif MyLevel >= 2200 and MyLevel <= 2224 then
        return "Cookie Crafter", "CakeQuest1", 1, CFrame.new(-2021.32007, 37.7982254, -12028.7295)
    elseif MyLevel >= 2225 and MyLevel <= 2249 then
        return "Cake Guard", "CakeQuest1", 2, CFrame.new(-2021.32007, 37.7982254, -12028.7295)
    elseif MyLevel >= 2250 and MyLevel <= 2274 then
        return "Baking Staff", "CakeQuest2", 1, CFrame.new(-1927.91602, 37.7981339, -12842.5391)
    elseif MyLevel >= 2275 and MyLevel <= 2299 then
        return "Head Baker", "CakeQuest2", 2, CFrame.new(-1927.91602, 37.7981339, -12842.5391)
    elseif MyLevel >= 2300 and MyLevel <= 2324 then
        return "Cocoa Warrior", "ChocQuest1", 1, CFrame.new(233.228363, 29.8760013, -12201.2333984375)
    elseif MyLevel >= 2325 and MyLevel <= 2349 then
        return "Chocolate Bar Battler", "ChocQuest1", 2, CFrame.new(233.228363, 29.8760013, -12201.2333984375)
    elseif MyLevel >= 2350 and MyLevel <= 2374 then
        return "Sweet Thief", "ChocQuest2", 1, CFrame.new(150.506637, 30.6936931, -12774.5029296875)
    elseif MyLevel >= 2375 and MyLevel <= 2399 then
        return "Candy Rebel", "ChocQuest2", 2, CFrame.new(150.506637, 30.6936931, -12774.5029296875)
    elseif MyLevel >= 2400 and MyLevel <= 2424 then
        return "Candy Pirate", "CandyQuest1", 1, CFrame.new(-1150.0400390625, 20.3789348, -14446.3349609375)
    elseif MyLevel >= 2425 and MyLevel <= 2449 then
        return "Snow Demon", "CandyQuest1", 2, CFrame.new(-1150.0400390625, 20.3789348, -14446.3349609375)
    elseif MyLevel >= 2450 and MyLevel <= 2474 then
        return "Isle Outlaw", "TikiQuest1", 1, CFrame.new(-16547.748046875, 61.135334, -173.41360473632812)
    elseif MyLevel >= 2475 and MyLevel <= 2524 then
        return "Island Boy", "TikiQuest1", 2, CFrame.new(-16547.748046875, 61.135334, -173.41360473632812)
    elseif MyLevel >= 2525 and MyLevel <= 2549 then
        return "Isle Champion", "TikiQuest2", 2, CFrame.new(-16539.078125, 55.6863288, 1051.5738525390625)
    elseif MyLevel >= 2550 and MyLevel <= 2574 then
        return "Serpent Hunter", "TikiQuest3", 1, CFrame.new(-16661.890625, 105.286231, 1576.69775390625)
    elseif MyLevel >= 2575 then
        return "Skull Slayer", "TikiQuest3", 2, CFrame.new(-16661.890625, 105.286231, 1576.69775390625)
    end
    return nil
end

--------------------------------------------------------------------------------------------------------------------------------
                                                   -- === TabInfo | Info === --
---------------------------------------------------------------------------------------------------------------------------------
TabInfo:AddDiscordInvite({
    Name = "Spectra Hub",
    Description = "Server Discord!",
    Logo = "rbxassetid://126286543557523",
    Invite = "https://discord.gg/vsKDhkJf8D",
})

TabInfo:AddSection({"Player Info"})

TabInfo:AddParagraph({"Welcome", "Welcome to Spectra Hub Blox Fruits Script!"})

local LevelLabel = TabInfo:AddParagraph({"Level", "Loading..."})
local BeliLabel = TabInfo:AddParagraph({"Beli", "Loading..."})
local FragmentLabel = TabInfo:AddParagraph({"Fragments", "Loading..."})
local RaceLabel = TabInfo:AddParagraph({"Race", "Loading..."})

spawn(function()
    while wait(1) do
        pcall(function()
            local player = game:GetService("Players").LocalPlayer
            local data = player.Data
            LevelLabel:SetDesc("Level: "..data.Level.Value)
            BeliLabel:SetDesc("Beli: "..data.Beli.Value)
            FragmentLabel:SetDesc("Fragments: "..data.Fragments.Value)
            RaceLabel:SetDesc("Race: "..CheckRace())
        end)
    end
end)

local function detectExecutor()
    if identifyexecutor then
        return identifyexecutor()
    elseif syn then
        return "Synapse X"
    elseif KRNL_LOADED then
        return "KRNL"
    elseif is_sirhurt_closure then
        return "SirHurt"
    elseif pebc_execute then
        return "ProtoSmasher"
    elseif getexecutorname then
        return getexecutorname()
    else
        return "Executor Unknown"
    end
end

local executorName = detectExecutor()

local Paragraph = TabInfo:AddParagraph({"Executor", executorName})

TabInfo:AddSection({"Script Information"})

local function createInfoBlock(tab, title, initial)
	local block
	local ok = pcall(function()
		block = tab:AddParagraph({ Title = title, Content = initial })
	end)
	if not ok or not block then
		ok = pcall(function()
			block = tab:AddLabel(title .. (initial and ("\n" .. initial) or ""))
		end)
	end
	return block
end

local function setBlockText(block, title, text)
	if not block then return end
	local ok = pcall(function()
		if block.Set then return block:Set(text) end
		if block.SetDesc then return block:SetDesc(text) end
		if block.SetText then return block:SetText(text) end
		if block.Update then return block:Update(text) end
		if block.Refresh then return block:Refresh(text) end
	end)
	if not ok then
		pcall(function()
			if block.Text ~= nil then
				block.Text = title .. "\n" .. text
			end
		end)
	end
end

local function getCurrentDate()
	local currentTime = os.time()
	return os.date("%d/%m/%Y", currentTime)
end

local Players = game:GetService("Players")
local localPlayer = Players.LocalPlayer

local welcomeBlock = createInfoBlock(Tab1, "Welcome! Today is: ", getCurrentDate())

TabInfo:AddParagraph({"You Nickname: " .. (game.Players.LocalPlayer.Name or "Unknown")})

TabInfo:AddParagraph({"You ID: " .. tostring(game.Players.LocalPlayer.UserId or 0)})

local timerBlock   = createInfoBlock(Tab1, "Script Usage Time: ", "00:00:00")
local fpsBlock     = createInfoBlock(Tab1, "Your FPS: ", "FPS: 0")

local RunService = game:GetService("RunService")

local startClock = os.clock()

local currentFPS = 0
RunService.RenderStepped:Connect(function(dt)
	currentFPS = math.floor(1/dt + 0.5)
end)

task.spawn(function()
	while true do
		task.wait(0.5)

		setBlockText(welcomeBlock, "Welcome! Today is: ", getCurrentDate())

		local e = os.clock() - startClock
		local h = math.floor(e/3600)
		local m = math.floor((e%3600)/60)
		local s = math.floor(e%60)
		setBlockText(timerBlock, "Script Usage Time: ", string.format("%02d:%02d:%02d", h, m, s))

		setBlockText(fpsBlock, "Your FPS: ", "FPS: " .. tostring(currentFPS))
	end
end)

local Section = TabInfo:AddSection({"Collaborators"})

TabInfo:AddParagraph({ "Owner:", "Denolk"})
TabInfo:AddParagraph({ "Assistants:", "Assure" })

--------------------------------------------------------------------------------------------------------------------------------
                                                   -- === TabFarm | Farming === --
---------------------------------------------------------------------------------------------------------------------------------
TabFarm:AddSection({"Select Attack Mode"})
TabFarm:AddParagraph({ "In-progress...", "Modes: Normal, Fast, Super Fast, God Mode." })

TabFarm:AddDropdown({
    Name = "Select Weapon",
    Options = {"Melee", "Sword", "Fruit", "Gun"},
    Default = "Melee",
    Callback = function(Value)
        _G.Weapon = Value
    end
})

TabFarm:AddSection({"Types of Auto Farms"})

TabFarm:AddToggle({
    Name = "Auto Farm Level",
    Default = false,
    Callback = function(Value)
        _G.AutoFarm = Value
        if not Value then Unstabilize() end
    end
})

spawn(function()
    while task.wait() do
        if _G.AutoFarm then
            pcall(function()
                local targetMon, questName, questLevel, questPos = CheckQuest()
                local hasQuest = player.PlayerGui.Main.Quest.Visible
                
                if not hasQuest then
                    topos(questPos)
                    if (player.Character.HumanoidRootPart.Position - questPos.Position).Magnitude < 10 then
                        ReplicatedStorage.Remotes.CommF_:InvokeServer("StartQuest", questName, questLevel)
                    end
                else
                    local enemy = workspace.Enemies:FindFirstChild(targetMon)
                    if enemy and enemy:FindFirstChild("HumanoidRootPart") and enemy.Humanoid.Health > 0 then
                        EquipWeapon()

                        topos(enemy.HumanoidRootPart.CFrame * CFrame.new(0, 25, 0))
                        
                        ReplicatedStorage.Modules.Net["RE/RegisterAttack"]:FireServer(0.4)
                        ReplicatedStorage.Modules.Net["RE/RegisterHit"]:FireServer(enemy.HumanoidRootPart, {}, "617888d2")
                    else

                        local spawnPoint = workspace._WorldOrigin.EnemySpawns:FindFirstChild(targetMon)
                        if spawnPoint then topos(spawnPoint.CFrame) end
                    end
                end
            end)
        end
    end
end)

TabFarm:AddToggle({
    Name = "Bring Mode",
    Default = false,
    Callback = function(v)
        _G.AutoFarmMaterial = v
    end
})

--------------------------------------------------------------------------------------------------------------------------------
                                                   -- === TabEsp | Esp General === --
---------------------------------------------------------------------------------------------------------------------------------
local ToggleStates = {
    IslandESP = false,
    ESPPlayer = false,
    ChestESP = false,
    DevilFruitESP = false,
    FlowerESP = false,
    RealFruitESP = false,
    MobESP = false,
    SeaESP = false,
    NpcESP = false,
    MirageIslandESP = false,
    AfdESP = false,
    AuraESP = false,
    LADESP = false,
    GearESP = false
}

local function isnil(thing)
    return (thing == nil)
end

local function round(n)
    return math.floor(tonumber(n) + 0.5)
end

local Number = math.random(1, 1000000)

local function UpdateIslandESP()
    for i,v in pairs(game:GetService("Workspace")["_WorldOrigin"].Locations:GetChildren()) do
        pcall(function()
            if ToggleStates.IslandESP then
                if v.Name ~= "Sea" then
                    if not v:FindFirstChild('NameEsp') then
                        local bill = Instance.new('BillboardGui',v)
                        bill.Name = 'NameEsp'
                        bill.ExtentsOffset = Vector3.new(0, 1, 0)
                        bill.Size = UDim2.new(1,200,1,30)
                        bill.Adornee = v
                        bill.AlwaysOnTop = true
                        local name = Instance.new('TextLabel',bill)
                        name.Font = "GothamBold"
                        name.FontSize = "Size14"
                        name.TextWrapped = true
                        name.Size = UDim2.new(1,0,1,0)
                        name.TextYAlignment = 'Top'
                        name.BackgroundTransparency = 1
                        name.TextStrokeTransparency = 0.5
                        name.TextColor3 = Color3.fromRGB(7, 236, 240)
                    else
                        v['NameEsp'].TextLabel.Text = (v.Name ..'   \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Position).Magnitude/3) ..' Distance')
                    end
                end
            else
                if v:FindFirstChild('NameEsp') then
                    v:FindFirstChild('NameEsp'):Destroy()
                end
            end
        end)
    end
end

local function UpdatePlayerChams()
    for i,v in pairs(game:GetService'Players':GetChildren()) do
        pcall(function()
            if not isnil(v.Character) then
                if ToggleStates.ESPPlayer then
                    if not isnil(v.Character.Head) and not v.Character.Head:FindFirstChild('NameEsp'..Number) then
                        local bill = Instance.new('BillboardGui',v.Character.Head)
                        bill.Name = 'NameEsp'..Number
                        bill.ExtentsOffset = Vector3.new(0, 1, 0)
                        bill.Size = UDim2.new(1,200,1,30)
                        bill.Adornee = v.Character.Head
                        bill.AlwaysOnTop = true
                        local name = Instance.new('TextLabel',bill)
                        name.Font = Enum.Font.GothamSemibold
                        name.FontSize = "Size14"
                        name.TextWrapped = true
                        name.Text = (v.Name ..' \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Character.Head.Position).Magnitude/3) ..' Distance')
                        name.Size = UDim2.new(1,0,1,0)
                        name.TextYAlignment = 'Top'
                        name.BackgroundTransparency = 1
                        name.TextStrokeTransparency = 0.5
                        if v.Team == game.Players.LocalPlayer.Team then
                            name.TextColor3 = Color3.new(0,255,0)
                        else
                            name.TextColor3 = Color3.new(255,0,0)
                        end
                    else
                        v.Character.Head['NameEsp'..Number].TextLabel.Text = (v.Name ..' | '.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Character.Head.Position).Magnitude/3) ..' Distance\nHealth : ' .. round(v.Character.Humanoid.Health*100/v.Character.Humanoid.MaxHealth) .. '%')
                    end
                else
                    if v.Character.Head:FindFirstChild('NameEsp'..Number) then
                        v.Character.Head:FindFirstChild('NameEsp'..Number):Destroy()
                    end
                end
            end
        end)
    end
end

local function UpdateChestChams()
    for i,v in pairs(game.Workspace:GetChildren()) do
        pcall(function()
            if string.find(v.Name,"Chest") then
                if ToggleStates.ChestESP then
                    if not v:FindFirstChild('NameEsp'..Number) then
                        local bill = Instance.new('BillboardGui',v)
                        bill.Name = 'NameEsp'..Number
                        bill.ExtentsOffset = Vector3.new(0, 1, 0)
                        bill.Size = UDim2.new(1,200,1,30)
                        bill.Adornee = v
                        bill.AlwaysOnTop = true
                        local name = Instance.new('TextLabel',bill)
                        name.Font = Enum.Font.GothamSemibold
                        name.FontSize = "Size14"
                        name.TextWrapped = true
                        name.Size = UDim2.new(1,0,1,0)
                        name.TextYAlignment = 'Top'
                        name.BackgroundTransparency = 1
                        name.TextStrokeTransparency = 0.5
                        if v.Name == "Chest1" then
                            name.TextColor3 = Color3.fromRGB(109, 109, 109)
                            name.Text = ("Chest 1" ..' \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Position).Magnitude/3) ..' Distance')
                        end
                        if v.Name == "Chest2" then
                            name.TextColor3 = Color3.fromRGB(173, 158, 21)
                            name.Text = ("Chest 2" ..' \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Position).Magnitude/3) ..' Distance')
                        end
                        if v.Name == "Chest3" then
                            name.TextColor3 = Color3.fromRGB(85, 255, 255)
                            name.Text = ("Chest 3" ..' \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Position).Magnitude/3) ..' Distance')
                        end
                    else
                        v['NameEsp'..Number].TextLabel.Text = (v.Name ..'   \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Position).Magnitude/3) ..' Distance')
                    end
                else
                    if v:FindFirstChild('NameEsp'..Number) then
                        v:FindFirstChild('NameEsp'..Number):Destroy()
                    end
                end
            end
        end)
    end
end

local function UpdateDevilChams()
    for i,v in pairs(game.Workspace:GetChildren()) do
        pcall(function()
            if ToggleStates.DevilFruitESP then
                if string.find(v.Name, "Fruit") then
                    if not v.Handle:FindFirstChild('NameEsp'..Number) then
                        local bill = Instance.new('BillboardGui',v.Handle)
                        bill.Name = 'NameEsp'..Number
                        bill.ExtentsOffset = Vector3.new(0, 1, 0)
                        bill.Size = UDim2.new(1,200,1,30)
                        bill.Adornee = v.Handle
                        bill.AlwaysOnTop = true
                        local name = Instance.new('TextLabel',bill)
                        name.Font = Enum.Font.GothamSemibold
                        name.FontSize = "Size14"
                        name.TextWrapped = true
                        name.Size = UDim2.new(1,0,1,0)
                        name.TextYAlignment = 'Top'
                        name.BackgroundTransparency = 1
                        name.TextStrokeTransparency = 0.5
                        name.TextColor3 = Color3.fromRGB(255, 255, 255)
                        name.Text = (v.Name ..' \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Handle.Position).Magnitude/3) ..' Distance')
                    else
                        v.Handle['NameEsp'..Number].TextLabel.Text = (v.Name ..'   \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Handle.Position).Magnitude/3) ..' Distance')
                    end
                end
            else
                if v.Handle:FindFirstChild('NameEsp'..Number) then
                    v.Handle:FindFirstChild('NameEsp'..Number):Destroy()
                end
            end
        end)
    end
end

local function UpdateFlowerChams()
    for i,v in pairs(game.Workspace:GetChildren()) do
        pcall(function()
            if v.Name == "Flower2" or v.Name == "Flower1" then
                if ToggleStates.FlowerESP then
                    if not v:FindFirstChild('NameEsp'..Number) then
                        local bill = Instance.new('BillboardGui',v)
                        bill.Name = 'NameEsp'..Number
                        bill.ExtentsOffset = Vector3.new(0, 1, 0)
                        bill.Size = UDim2.new(1,200,1,30)
                        bill.Adornee = v
                        bill.AlwaysOnTop = true
                        local name = Instance.new('TextLabel',bill)
                        name.Font = Enum.Font.GothamSemibold
                        name.FontSize = "Size14"
                        name.TextWrapped = true
                        name.Size = UDim2.new(1,0,1,0)
                        name.TextYAlignment = 'Top'
                        name.BackgroundTransparency = 1
                        name.TextStrokeTransparency = 0.5
                        name.TextColor3 = Color3.fromRGB(255, 0, 0)
                        if v.Name == "Flower1" then
                            name.Text = ("Blue Flower" ..' \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Position).Magnitude/3) ..' Distance')
                            name.TextColor3 = Color3.fromRGB(0, 0, 255)
                        end
                        if v.Name == "Flower2" then
                            name.Text = ("Red Flower" ..' \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Position).Magnitude/3) ..' Distance')
                            name.TextColor3 = Color3.fromRGB(255, 0, 0)
                        end
                    else
                        v['NameEsp'..Number].TextLabel.Text = (v.Name ..'   \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Position).Magnitude/3) ..' Distance')
                    end
                else
                    if v:FindFirstChild('NameEsp'..Number) then
                        v:FindFirstChild('NameEsp'..Number):Destroy()
                    end
                end
            end
        end)
    end
end

local function UpdateRealFruitChams()
    local spawners = {"AppleSpawner", "PineappleSpawner", "BananaSpawner"}
    local colors = {
        AppleSpawner = Color3.fromRGB(255, 0, 0),
        PineappleSpawner = Color3.fromRGB(255, 174, 0),
        BananaSpawner = Color3.fromRGB(251, 255, 0)
    }
    
    for _, spawnerName in pairs(spawners) do
        local spawner = game.Workspace:FindFirstChild(spawnerName)
        if spawner then
            for i,v in pairs(spawner:GetChildren()) do
                if v:IsA("Tool") then
                    if ToggleStates.RealFruitESP then
                        if not v.Handle:FindFirstChild('NameEsp'..Number) then
                            local bill = Instance.new('BillboardGui',v.Handle)
                            bill.Name = 'NameEsp'..Number
                            bill.ExtentsOffset = Vector3.new(0, 1, 0)
                            bill.Size = UDim2.new(1,200,1,30)
                            bill.Adornee = v.Handle
                            bill.AlwaysOnTop = true
                            local name = Instance.new('TextLabel',bill)
                            name.Font = Enum.Font.GothamSemibold
                            name.FontSize = "Size14"
                            name.TextWrapped = true
                            name.Size = UDim2.new(1,0,1,0)
                            name.TextYAlignment = 'Top'
                            name.BackgroundTransparency = 1
                            name.TextStrokeTransparency = 0.5
                            name.TextColor3 = colors[spawnerName]
                            name.Text = (v.Name ..' \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Handle.Position).Magnitude/3) ..' Distance')
                        else
                            v.Handle['NameEsp'..Number].TextLabel.Text = (v.Name ..' '.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Handle.Position).Magnitude/3) ..' Distance')
                        end
                    else
                        if v.Handle:FindFirstChild('NameEsp'..Number) then
                            v.Handle:FindFirstChild('NameEsp'..Number):Destroy()
                        end
                    end
                end
            end
        end
    end
end

local function UpdateIslandMirageESP()
    for i,v in pairs(game:GetService("Workspace")["_WorldOrigin"].Locations:GetChildren()) do
        pcall(function()
            if ToggleStates.MirageIslandESP then
                if v.Name == "Mirage Island" then
                    if not v:FindFirstChild('NameEsp') then
                        local bill = Instance.new('BillboardGui',v)
                        bill.Name = 'NameEsp'
                        bill.ExtentsOffset = Vector3.new(0, 1, 0)
                        bill.Size = UDim2.new(1,200,1,30)
                        bill.Adornee = v
                        bill.AlwaysOnTop = true
                        local name = Instance.new('TextLabel',bill)
                        name.Font = "Code"
                        name.FontSize = "Size14"
                        name.TextWrapped = true
                        name.Size = UDim2.new(1,0,1,0)
                        name.TextYAlignment = 'Top'
                        name.BackgroundTransparency = 1
                        name.TextStrokeTransparency = 0.5
                        name.TextColor3 = Color3.fromRGB(80, 245, 245)
                    else
                        v['NameEsp'].TextLabel.Text = (v.Name ..'   \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Position).Magnitude/3) ..' M')
                    end
                end
            else
                if v:FindFirstChild('NameEsp') then
                    v:FindFirstChild('NameEsp'):Destroy()
                end
            end
        end)
    end
end

local function UpdateAfdESP()
    for i,v in pairs(game:GetService("Workspace").NPCs:GetChildren()) do
        pcall(function()
            if ToggleStates.AfdESP then
                if v.Name == "Advanced Fruit Dealer" then
                    if not v:FindFirstChild('NameEsp') then
                        local bill = Instance.new('BillboardGui',v)
                        bill.Name = 'NameEsp'
                        bill.ExtentsOffset = Vector3.new(0, 1, 0)
                        bill.Size = UDim2.new(1,200,1,30)
                        bill.Adornee = v
                        bill.AlwaysOnTop = true
                        local name = Instance.new('TextLabel',bill)
                        name.Font = "Code"
                        name.FontSize = "Size14"
                        name.TextWrapped = true
                        name.Size = UDim2.new(1,0,1,0)
                        name.TextYAlignment = 'Top'
                        name.BackgroundTransparency = 1
                        name.TextStrokeTransparency = 0.5
                        name.TextColor3 = Color3.fromRGB(80, 245, 245)
                    else
                        v['NameEsp'].TextLabel.Text = (v.Name ..'   \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Position).Magnitude/3) ..' M')
                    end
                end
            else
                if v:FindFirstChild('NameEsp') then
                    v:FindFirstChild('NameEsp'):Destroy()
                end
            end
        end)
    end
end

local function UpdateAuraESP()
    for i,v in pairs(game:GetService("Workspace").NPCs:GetChildren()) do
        pcall(function()
            if ToggleStates.AuraESP then
                if v.Name == "Master of Enhancement" then
                    if not v:FindFirstChild('NameEsp') then
                        local bill = Instance.new('BillboardGui',v)
                        bill.Name = 'NameEsp'
                        bill.ExtentsOffset = Vector3.new(0, 1, 0)
                        bill.Size = UDim2.new(1,200,1,30)
                        bill.Adornee = v
                        bill.AlwaysOnTop = true
                        local name = Instance.new('TextLabel',bill)
                        name.Font = "Code"
                        name.FontSize = "Size14"
                        name.TextWrapped = true
                        name.Size = UDim2.new(1,0,1,0)
                        name.TextYAlignment = 'Top'
                        name.BackgroundTransparency = 1
                        name.TextStrokeTransparency = 0.5
                        name.TextColor3 = Color3.fromRGB(80, 245, 245)
                    else
                        v['NameEsp'].TextLabel.Text = (v.Name ..'   \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Position).Magnitude/3) ..' M')
                    end
                end
            else
                if v:FindFirstChild('NameEsp') then
                    v:FindFirstChild('NameEsp'):Destroy()
                end
            end
        end)
    end
end

local function UpdateLSDESP()
    for i,v in pairs(game:GetService("Workspace").NPCs:GetChildren()) do
        pcall(function()
            if ToggleStates.LADESP then
                if v.Name == "Legendary Sword Dealer" then
                    if not v:FindFirstChild('NameEsp') then
                        local bill = Instance.new('BillboardGui',v)
                        bill.Name = 'NameEsp'
                        bill.ExtentsOffset = Vector3.new(0, 1, 0)
                        bill.Size = UDim2.new(1,200,1,30)
                        bill.Adornee = v
                        bill.AlwaysOnTop = true
                        local name = Instance.new('TextLabel',bill)
                        name.Font = "Code"
                        name.FontSize = "Size14"
                        name.TextWrapped = true
                        name.Size = UDim2.new(1,0,1,0)
                        name.TextYAlignment = 'Top'
                        name.BackgroundTransparency = 1
                        name.TextStrokeTransparency = 0.5
                        name.TextColor3 = Color3.fromRGB(80, 245, 245)
                    else
                        v['NameEsp'].TextLabel.Text = (v.Name ..'   \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Position).Magnitude/3) ..' M')
                    end
                end
            else
                if v:FindFirstChild('NameEsp') then
                    v:FindFirstChild('NameEsp'):Destroy()
                end
            end
        end)
    end
end

local function UpdateGeaESP()
    local mysticIsland = game:GetService("Workspace").Map:FindFirstChild("MysticIsland")
    if mysticIsland then
        for i,v in pairs(mysticIsland:GetChildren()) do
            pcall(function()
                if ToggleStates.GearESP then
                    if v.Name == "MeshPart" then
                        if not v:FindFirstChild('NameEsp') then
                            local bill = Instance.new('BillboardGui',v)
                            bill.Name = 'NameEsp'
                            bill.ExtentsOffset = Vector3.new(0, 1, 0)
                            bill.Size = UDim2.new(1,200,1,30)
                            bill.Adornee = v
                            bill.AlwaysOnTop = true
                            local name = Instance.new('TextLabel',bill)
                            name.Font = "Code"
                            name.FontSize = "Size14"
                            name.TextWrapped = true
                            name.Size = UDim2.new(1,0,1,0)
                            name.TextYAlignment = 'Top'
                            name.BackgroundTransparency = 1
                            name.TextStrokeTransparency = 0.5
                            name.TextColor3 = Color3.fromRGB(80, 245, 245)
                        else
                            v['NameEsp'].TextLabel.Text = (v.Name ..'   \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Position).Magnitude/3) ..' M')
                        end
                    end
                else
                    if v:FindFirstChild('NameEsp') then
                        v:FindFirstChild('NameEsp'):Destroy()
                    end
                end
            end)
        end
    end
end

spawn(function()
    while wait() do
        pcall(function()
            if ToggleStates.MobESP then
                for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                    if v:FindFirstChild('HumanoidRootPart') then
                        if not v:FindFirstChild("MobEap") then
                            local BillboardGui = Instance.new("BillboardGui")
                            local TextLabel = Instance.new("TextLabel")
                            BillboardGui.Parent = v  
                            BillboardGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling  
                            BillboardGui.Active = true  
                            BillboardGui.Name = "MobEap"  
                            BillboardGui.AlwaysOnTop = true  
                            BillboardGui.LightInfluence = 1.000  
                            BillboardGui.Size = UDim2.new(0, 200, 0, 50)  
                            BillboardGui.StudsOffset = Vector3.new(0, 2.5, 0)  
                            TextLabel.Parent = BillboardGui  
                            TextLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)  
                            TextLabel.BackgroundTransparency = 1.000  
                            TextLabel.Size = UDim2.new(0, 200, 0, 50)  
                            TextLabel.Font = Enum.Font.GothamBold  
                            TextLabel.TextColor3 = Color3.fromRGB(7, 236, 240)  
                            TextLabel.TextSize = 35  
                        end  
                        local Dis = math.floor((game.Players.LocalPlayer.Character.HumanoidRootPart.Position - v.HumanoidRootPart.Position).Magnitude)  
                        v.MobEap.TextLabel.Text = v.Name.." - "..Dis.." Distance"  
                    end  
                end  
            else  
                for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do  
                    if v:FindFirstChild("MobEap") then  
                        v.MobEap:Destroy()  
                    end  
                end  
            end  
        end)
    end
end)

spawn(function()
    while wait() do
        pcall(function()
            if ToggleStates.SeaESP then
                for i,v in pairs(game:GetService("Workspace").SeaBeasts:GetChildren()) do
                    if v:FindFirstChild('HumanoidRootPart') then
                        if not v:FindFirstChild("Seaesps") then
                            local BillboardGui = Instance.new("BillboardGui")
                            local TextLabel = Instance.new("TextLabel")
                            BillboardGui.Parent = v  
                            BillboardGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling  
                            BillboardGui.Active = true  
                            BillboardGui.Name = "Seaesps"  
                            BillboardGui.AlwaysOnTop = true  
                            BillboardGui.LightInfluence = 1.000  
                            BillboardGui.Size = UDim2.new(0, 200, 0, 50)  
                            BillboardGui.StudsOffset = Vector3.new(0, 2.5, 0)  
                            TextLabel.Parent = BillboardGui  
                            TextLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)  
                            TextLabel.BackgroundTransparency = 1.000  
                            TextLabel.Size = UDim2.new(0, 200, 0, 50)  
                            TextLabel.Font = Enum.Font.GothamBold  
                            TextLabel.TextColor3 = Color3.fromRGB(7, 236, 240)  
                            TextLabel.TextSize = 35  
                        end  
                        local Dis = math.floor((game.Players.LocalPlayer.Character.HumanoidRootPart.Position - v.HumanoidRootPart.Position).Magnitude)  
                        v.Seaesps.TextLabel.Text = v.Name.." - "..Dis.." Distance"  
                    end  
                end  
            else  
                for i,v in pairs (game:GetService("Workspace").SeaBeasts:GetChildren()) do  
                    if v:FindFirstChild("Seaesps") then  
                        v.Seaesps:Destroy()  
                    end  
                end  
            end  
        end)
    end
end)

spawn(function()
    while wait() do
        pcall(function()
            if ToggleStates.NpcESP then
                for i,v in pairs(game:GetService("Workspace").NPCs:GetChildren()) do
                    if v:FindFirstChild('HumanoidRootPart') then
                        if not v:FindFirstChild("NpcEspes") then
                            local BillboardGui = Instance.new("BillboardGui")
                            local TextLabel = Instance.new("TextLabel")
                            BillboardGui.Parent = v  
                            BillboardGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling  
                            BillboardGui.Active = true  
                            BillboardGui.Name = "NpcEspes"  
                            BillboardGui.AlwaysOnTop = true  
                            BillboardGui.LightInfluence = 1.000  
                            BillboardGui.Size = UDim2.new(0, 200, 0, 50)  
                            BillboardGui.StudsOffset = Vector3.new(0, 2.5, 0)  
                            TextLabel.Parent = BillboardGui  
                            TextLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)  
                            TextLabel.BackgroundTransparency = 1.000  
                            TextLabel.Size = UDim2.new(0, 200, 0, 50)  
                            TextLabel.Font = Enum.Font.GothamBold  
                            TextLabel.TextColor3 = Color3.fromRGB(7, 236, 240)  
                            TextLabel.TextSize = 35  
                        end  
                        local Dis = math.floor((game.Players.LocalPlayer.Character.HumanoidRootPart.Position - v.HumanoidRootPart.Position).Magnitude)  
                        v.NpcEspes.TextLabel.Text = v.Name.." - "..Dis.." Distance"  
                    end  
                end  
            else  
                for i,v in pairs (game:GetService("Workspace").NPCs:GetChildren()) do  
                    if v:FindFirstChild("NpcEspes") then  
                        v.NpcEspes:Destroy()  
                    end  
                end  
            end  
        end)
    end
end)

spawn(function()
    while wait(1) do
        UpdateIslandESP()
        UpdatePlayerChams()
        UpdateChestChams()
        UpdateDevilChams()
        UpdateFlowerChams()
        UpdateRealFruitChams()
        UpdateIslandMirageESP()
        UpdateAfdESP()
        UpdateAuraESP()
        UpdateLSDESP()
        UpdateGeaESP()
    end
end)

TabEsp:AddToggle({
    Name = "Island ESP",
    Default = false,
    Callback = function(v)
        ToggleStates.IslandESP = v
    end
})

TabEsp:AddToggle({
    Name = "Player ESP",
    Default = false,
    Callback = function(v)
        ToggleStates.ESPPlayer = v
    end
})

TabEsp:AddToggle({
    Name = "Chest ESP",
    Default = false,
    Callback = function(v)
        ToggleStates.ChestESP = v
    end
})

TabEsp:AddToggle({
    Name = "Devil Fruit ESP",
    Default = false,
    Callback = function(v)
        ToggleStates.DevilFruitESP = v
    end
})

TabEsp:AddToggle({
    Name = "Flower ESP",
    Default = false,
    Callback = function(v)
        ToggleStates.FlowerESP = v
    end
})

TabEsp:AddToggle({
    Name = "Fruit Spawner ESP",
    Default = false,
    Callback = function(v)
        ToggleStates.RealFruitESP = v
    end
})

TabEsp:AddToggle({
    Name = "Mob ESP",
    Default = false,
    Callback = function(v)
        ToggleStates.MobESP = v
    end
})

TabEsp:AddToggle({
    Name = "Sea Beast ESP",
    Default = false,
    Callback = function(v)
        ToggleStates.SeaESP = v
    end
})

TabEsp:AddToggle({
    Name = "NPC ESP",
    Default = false,
    Callback = function(v)
        ToggleStates.NpcESP = v
    end
})

TabEsp:AddToggle({
    Name = "Mirage Island ESP",
    Default = false,
    Callback = function(v)
        ToggleStates.MirageIslandESP = v
    end
})

TabEsp:AddToggle({
    Name = "Advanced Fruit Dealer ESP",
    Default = false,
    Callback = function(v)
        ToggleStates.AfdESP = v
    end
})

TabEsp:AddToggle({
    Name = "Master of Enhancement ESP",
    Default = false,
    Callback = function(v)
        ToggleStates.AuraESP = v
    end
})

TabEsp:AddToggle({
    Name = "Legendary Sword Dealer ESP",
    Default = false,
    Callback = function(v)
        ToggleStates.LADESP = v
    end
})

TabEsp:AddToggle({
    Name = "Gear ESP",
    Default = false,
    Callback = function(v)
        ToggleStates.GearESP = v
    end
})
