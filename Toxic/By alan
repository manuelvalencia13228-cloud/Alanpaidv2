-- 💪 TOXIC / BY ALAN PAID v2 - BOOST 14x RENAS AUTO! 💪 (2025)
-- 🚀 Auto Switch: Swift Samurai (Farmeo Rápido) → Chaos Package + x2 Rebirth Pets → 14 RENAS por 1! 🌀🔄
-- Todas las funciones de josevallejopr1 + Rocas + Fast Renas + BOOST PETS PAID 🔥

local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local VirtualUser = game:GetService("VirtualUser")
local Stats = game:GetService("Stats")
local Lighting = game:GetService("Lighting")
local LocalPlayer = Players.LocalPlayer

-- 🌟 ANTI-AFK
local function preventAFK()
    VirtualUser:Button2Down(Vector2.new(0, 0), workspace.CurrentCamera.CFrame)
    task.wait(1)
    VirtualUser:Button2Up(Vector2.new(0, 0), workspace.CurrentCamera.CFrame)
end
Players.LocalPlayer.Idled:Connect(preventAFK)
print("✅ Anti-AFK Activado | TOXIC / BY ALAN PAID v2")

-- 🎨 UI Elerium V2 GRIS OSCURO
local library = loadstring(game:HttpGet("https://raw.githubusercontent.com/memejames/elerium-v2-ui-library/main/Library", true))()
local window = library:AddWindow("💪 TOXIC / BY ALAN PAID v2 💪", {
    main_color = Color3.fromRGB(65, 65, 65),  -- 🔄 GRIS OSCURO PERFECTO
    min_size = Vector2.new(700, 950),
    can_resize = true
})

-- 🏋️ TABS con EMOJIS
local AutoFarm = window:AddTab("🚀 Farm Op 💥")
local RockTab = window:AddTab("🪨 Rocks 🌟")
local RebirthTab = window:AddTab("🔄 Fast Renas ⚡")
local BoostTab = window:AddTab("🌀 Boost 14x Renas 🔥")
local Teleport = window:AddTab("📍 Teleports ✨")
local Killer = window:AddTab("⚔️ Killer 🔥")
local Calculadora = window:AddTab("🧮 Calculator 📊")
local Features = window:AddTab("📈 Stats Tracker 🏆")
local CreditosTab = window:AddTab("🎖️ Créditos ✨")  -- 🆕 CRÉDITOS BONITOS

-- ===========================================
-- VARIABLES BOOST 14x
-- ===========================================
getgenv().HighPingRep = false
getgenv().LowPingRep = false
local autoEatEnabled = false
getgenv().AutoSpinWheel = false
getgenv().AutoRebirth = false
getgenv().RebirthStop = 1e12
getgenv().autoFarmRock = false
getgenv().BoostMode = false

-- 🆕 BOOST PETS
getgenv().SwiftSamurai = "Swift Samurai"
getgenv().ChaosPet = "Chaos Sorcerer"
getgenv().RebirthBoostPets = {"Chaos Sorcerer", "Sarge", "Small Fry", "Chaos Overlord"}

-- Config Original
local PET_NAME = "Swift Samurai"
local ROCK_NAME_5M = "Rock5M"
local PROTEIN_EGG_NAME = "ProteinEgg"
local PROTEIN_EGG_INTERVAL = 30 * 60
local REPS_HIGH = 10
local REPS_LOW = 40
local REP_DELAY = 0.01
local ROCK_INTERVAL = 5

local RockDurabilities = {
    ["Tiny Island Rock"] = 0,
    ["Starter Island Rock"] = 100,
    ["Legend Beach Rock"] = 5000,
    ["Frost Gym Rock"] = 150000,
    ["Mythical Gym Rock"] = 400000,
    ["Eternal Gym Rock"] = 750000,
    ["Legend Gym Rock"] = 1000000,
    ["Muscle King Gym Rock"] = 5000000,
    ["Ancient Jungle Rock"] = 10000000
}
local currentRock = nil

-- ===========================================
-- FUNCIONES BOOST + ORIGINALES
-- ===========================================
local HumanoidRootPart
local lastProteinEggTime = 0
local lastRockTime = 0

local function getPing()
    local success, ping = pcall(function()
        return Stats.Network.ServerStatsItem["Data Ping"]:GetValue()
    end)
    return success and ping or 999
end

local function updateCharacterRefs()
    local character = LocalPlayer.Character or LocalPlayer.CharacterAdded:Wait()
    HumanoidRootPart = character:WaitForChild("HumanoidRootPart", 5)
end

-- 🆕 FUNCIÓN AUTO EQUIP PET por NOMBRE
local function equipPetByName(petName)
    local petsFolder = LocalPlayer:FindFirstChild("petsFolder")
    if petsFolder then
        for _, folder in pairs(petsFolder:GetChildren()) do
            for _, pet in pairs(folder:GetChildren()) do
                if pet.Name == petName then
                    ReplicatedStorage.rEvents.equipPetEvent:FireServer("equipPet", pet)
                    print("✅ BOOST: Equipado " .. petName)
                    return true
                end
            end
        end
    end
    warn("❌ Pet no encontrado: " .. petName)
    return false
end

local function equipPet()
    equipPetByName(PET_NAME)
end

local function eatProteinEgg()
    if LocalPlayer.Backpack then
        for _, item in pairs(LocalPlayer.Backpack:GetChildren()) do
            if item.Name == PROTEIN_EGG_NAME then
                ReplicatedStorage.rEvents.eatEvent:FireServer("eat", item)
                break
            end
        end
    end
end

local function hitRock5M()
    local rock = workspace:FindFirstChild(ROCK_NAME_5M)
    if rock and HumanoidRootPart then
        HumanoidRootPart.CFrame = rock.CFrame * CFrame.new(0, 0, -5)
        ReplicatedStorage.rEvents.hitEvent:FireServer("hit", rock)
    end
end

local function doRebirth()
    ReplicatedStorage.rEvents.rebirthEvent:FireServer()
end

local function tpToKingsGym()
    if HumanoidRootPart then
        HumanoidRootPart.CFrame = CFrame.new(-500, 10, 0)
    end
end

local function gettool()
    for _, v in pairs(LocalPlayer.Backpack:GetChildren()) do
        if v.Name == "Punch" and LocalPlayer.Character:FindFirstChild("Humanoid") then
            LocalPlayer.Character.Humanoid:EquipTool(v)
        end
    end
    LocalPlayer.muscleEvent:FireServer("punch", "leftHand")
    LocalPlayer.muscleEvent:FireServer("punch", "rightHand")
end

-- ===========================================
-- LOOP REPS HIGH/LOW (Original)
-- ===========================================
task.spawn(function()
    updateCharacterRefs()
    equipPet()
    lastProteinEggTime = tick()
    lastRockTime = tick()
    while true do
        local ping = getPing()
        
        if getgenv().HighPingRep then
            local farmingPaused = ping > 450 or ping <= 250 == false
            if not farmingPaused and LocalPlayer:FindFirstChild("muscleEvent") then
                for i = 1, REPS_HIGH do LocalPlayer.muscleEvent:FireServer("rep") end
                if tick() - lastProteinEggTime >= PROTEIN_EGG_INTERVAL then eatProteinEgg() lastProteinEggTime = tick() end
                if tick() - lastRockTime >= ROCK_INTERVAL then hitRock5M() lastRockTime = tick() end
            end
        end
        
        if getgenv().LowPingRep then
            local farmingPaused = ping > 5000 or ping <= 100 == false
            if not farmingPaused and LocalPlayer:FindFirstChild("muscleEvent") then
                for i = 1, REPS_LOW do LocalPlayer.muscleEvent:FireServer("rep") end
                if tick() - lastProteinEggTime >= PROTEIN_EGG_INTERVAL then eatProteinEgg() lastProteinEggTime = tick() end
                if tick() - lastRockTime >= ROCK_INTERVAL then hitRock5M() lastRockTime = tick() end
            end
        end
        
        task.wait(REP_DELAY)
    end
end)

-- ===========================================
-- 🆕 LOOP BOOST 14x RENAS (Swift → Chaos)
-- ===========================================
task.spawn(function()
    while true do
        if getgenv().BoostMode and getgenv().AutoRebirth and LocalPlayer:FindFirstChild("leaderstats") then
            local strength = LocalPlayer.leaderstats.Strength.Value
            
            -- FASE 1: Swift Samurai para farmeo RÁPIDO hasta Stop
            if strength < getgenv().RebirthStop then
                equipPetByName(getgenv().SwiftSamurai)
            else
                -- FASE 2: Switch a Chaos Pack + x2 Rebirth Pets ANTES rebirth
                print("🌀 BOOST: Cambiando a Chaos Pets para 14x RENAS!")
                for _, petName in pairs(getgenv().RebirthBoostPets) do
                    equipPetByName(petName)
                    task.wait(0.1)
                end
                task.wait(0.5)
                doRebirth()
                task.wait(2)
                tpToKingsGym()
                print("🔥 BOOST COMPLETO: ¡14x más rápido al siguiente rebirth!")
            end
        end
        task.wait(0.5)
    end
end)

-- Spin Wheel Loop
task.spawn(function()
    while true do
        if getgenv().AutoSpinWheel then
            pcall(function()
                ReplicatedStorage.rEvents.openFortuneWheelRemote:InvokeServer("openFortuneWheel", ReplicatedStorage.fortuneWheelChances["Fortune Wheel"])
            end)
        end
        task.wait(0.1)
    end
end)

-- ===========================================
-- FARM TAB 🔥
-- ===========================================
AutoFarm:AddSwitch("🐌 Strength Op (Ping >250ms) [10 Reps]", function(state) getgenv().HighPingRep = state end)
AutoFarm:AddSwitch("⚡ Strength Op (Ping <150ms) [40 Reps]", function(state) getgenv().LowPingRep = state end)
AutoFarm:AddSwitch("🥚 Auto Eat Egg 30 Min", function(state) autoEatEnabled = state end)
AutoFarm:AddSwitch("🎡 Auto Spin Fortune Wheel", function(state) getgenv().AutoSpinWheel = state end)
AutoFarm:AddSwitch("🕶️ Hide All Frames", function(bool)
    for _, obj in pairs(ReplicatedStorage:GetChildren()) do if obj.Name:match("Frame$") then obj.Visible = not bool end end
end)
AutoFarm:AddButton("🛡️ Anti Lag Full", function()
    for _, v in pairs(game:GetDescendants()) do
        if v:IsA("ParticleEmitter") or v:IsA("Smoke") or v:IsA("Fire") or v:IsA("Sparkles") then v.Enabled = false end
    end
    Lighting.GlobalShadows = false; Lighting.FogEnd = 9e9; settings().Rendering.QualityLevel = 1
    game:GetService("StarterGui"):SetCore("SendNotification", {Title = "🛡️ Anti Lag PAID", Duration = 5})
end)
AutoFarm:AddButton("✨ Full Opti + 50 Plataformas", function()
    for _, gui in pairs(LocalPlayer.PlayerGui:GetChildren()) do if gui:IsA("ScreenGui") then gui:Destroy() end end
    for _, v in pairs(Lighting:GetChildren()) do if v:IsA("Sky") then v:Destroy() end end
    local darkSky = Instance.new("Sky", Lighting); darkSky.SkyboxBk = "rbxassetid://0"
    for i = 1, 50 do
        local part = Instance.new("Part"); part.Anchored = true; part.CanCollide = true; part.Transparency = 1
        part.Size = Vector3.new(20000, 1, 20000); part.Position = Vector3.new(math.random(-10000,10000), math.random(-50,50), math.random(-10000,10000)); part.Parent = workspace
    end
end)

-- ===========================================
-- ROCK TAB 🪨
-- ===========================================
RockTab:AddLabel("🪨 Auto Farm Rocas por Durabilidad 💪")
for rockName, durReq in pairs(RockDurabilities) do
    RockTab:AddSwitch("🪨 " .. rockName .. " (" .. durReq .. ")", function(bool)
        currentRock = rockName; getgenv().autoFarmRock = bool
        if bool then task.spawn(function()
            while getgenv().autoFarmRock do task.wait()
                if LocalPlayer.Durability.Value >= durReq and LocalPlayer.Character:FindFirstChild("LeftHand") and LocalPlayer.Character:FindFirstChild("RightHand") then
                    for _, v in pairs(workspace.machinesFolder:GetDescendants()) do
                        if v.Name == "neededDurability" and v.Value == durReq then
                            local rock = v.Parent.Rock
                            firetouchinterest(rock, LocalPlayer.Character.RightHand, 0); firetouchinterest(rock, LocalPlayer.Character.RightHand, 1)
                            firetouchinterest(rock, LocalPlayer.Character.LeftHand, 0); firetouchinterest(rock, LocalPlayer.Character.LeftHand, 1)
                            gettool(); break
                        end
                    end
                end
            end end)
        end
    end)
end

-- ===========================================
-- FAST RENAS TAB 🔄
-- ===========================================
RebirthTab:AddSwitch("🔄 Auto Rebirth Fast", function(state) getgenv().AutoRebirth = state end)
RebirthTab:AddTextBox("🛑 Rebirth Stop (1T, 1Qa)", function(text)
    local num = tonumber(text:gsub("[TQaBKM]", "")) or 0
    local mult = ({T=1e12, Qa=1e15, B=1e9, M=1e6, K=1e3})[text:match("[TQBKM]")] or 1
    getgenv().RebirthStop = num * mult
end)
RebirthTab:AddButton("🔄 Rebirth Ahora", doRebirth)
RebirthTab:AddButton("🏋️ TP Muscle King Gym", tpToKingsGym)

-- ===========================================
-- 🆕 BOOST 14x TAB 🌀
-- ===========================================
BoostTab:AddLabel("🌀 BOOST 14x RENAS: Swift Samurai → Chaos Pack 🔥")
BoostTab:AddLabel("💡 Activa con Auto Rebirth + Low Ping Reps")
BoostTab:AddSwitch("🚀 Auto Boost 14x Renas", function(state)
    getgenv().BoostMode = state
    if state then
        print("🌀 BOOST 14x ACTIVADO! Swift → Chaos para x14 velocidad!")
    end
end)

BoostTab:AddTextBox("⚔️ Pet Farmeo Rápido (Swift Samurai)", function(text)
    getgenv().SwiftSamurai = text
end)

BoostTab:AddTextBox("🌀 Pet x2 Renas (Chaos Sorcerer)", function(text)
    getgenv().ChaosPet = text
end)

BoostTab:AddButton("🔄 Equip Chaos Pack Ahora", function()
    for _, pet in pairs(getgenv().RebirthBoostPets) do equipPetByName(pet) end
end)

BoostTab:AddButton("📝 Lista Tus Pets", function()
    local petsFolder = LocalPlayer:FindFirstChild("petsFolder")
    if petsFolder then
        local petList = {}
        for _, folder in pairs(petsFolder:GetChildren()) do
            for _, pet in pairs(folder:GetChildren()) do table.insert(petList, pet.Name) end
        end
        print("📋 TUS PETS: " .. table.concat(petList, ", "))
    end
end)

BoostTab:AddLabel("🎯 Chaos Pack = 14x más rápido post-rebirth!")

-- ===========================================
-- TELEPORTS 📍
-- ===========================================
local TPs = {
    ["🏠 Spawn"] = CFrame.new(2, 8, 115),
    ["🔥 Muscle King Gym"] = CFrame.new(-500, 10, 0),
    ["❄️ Frozen Island"] = CFrame.new(-2600, 3.67, -403),
    ["🌟 Secret Area"] = CFrame.new(1947, 2, 6191),
    ["🏝️ Tiny Island"] = CFrame.new(-34, 7, 1903)
}
for name, cf in pairs(TPs) do
    Teleport:AddButton(name, function() if HumanoidRootPart then HumanoidRootPart.CFrame = cf end end)
end

-- ===========================================
-- 🆕 CRÉDITOS BONITOS 🎖️
-- ===========================================
CreditosTab:AddParagraph("🏆 TOXIC / BY ALAN PAID v2 🏆", "💎 Script PREMIUM con BOOST 14x RENAS")
CreditosTab:AddParagraph("👑 Creador", "ALAN - El mejor dev de Muscle Legends 💪")
CreditosTab:AddParagraph("🙏 AGRADECIMIENTOS ESPECIALES 🙏", "A TODA la comunidad que usa y apoya día a día\nGracias por hacer esto posible 🔥\n¡Cada usuario es parte de la familia TOXIC!")
CreditosTab:AddParagraph("📅 Actualizado", "28 Noviembre 2025 - Siempre OP")
CreditosTab:AddParagraph("💝 Mensaje Final", "¡Gracias por confiar en TOXIC / BY ALAN!\n¡A romper Muscle Legends juntos! 🚀✨")

-- 🌈 NOTIF FINAL v2
game:GetService("StarterGui"):SetCore("SendNotification", {
    Title = "💪 TOXIC / BY ALAN PAID v2 - GRIS EDITION 🌀";
    Text = "✅ BOOST 14x ACTIVADO! Swift → Chaos = 14 RENAS x1 | Color GRIS 🔥";
    Duration = 10
})
print("🎉 TOXIC / BY ALAN PAID v2 GRIS COMPLETO con BOOST 14x! 🚀💪")
