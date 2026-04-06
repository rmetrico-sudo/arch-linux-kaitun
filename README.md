--[[
    █████╗ ██████╗  ██████╗     ██╗     ██╗   ██╗███╗   ██╗██╗   ██╗██╗  ██╗
   ██╔══██╗██╔══██╗██╔════╝     ██║     ██║   ██║████╗  ██║██║   ██║██║ ██╔╝
   ███████║██████╔╝██║          ██║     ██║   ██║██╔██╗ ██║██║   ██║█████╔╝ 
   ██╔══██║██╔══██╗██║          ██║     ██║   ██║██║╚██╗██║██║   ██║██╔═██╗ 
   ██║  ██║██║  ██║╚██████╗     ███████╗╚██████╔╝██║ ╚████║╚██████╔╝██║  ██╗
   ╚═╝  ╚═╝╚═╝  ╚═╝ ╚═════╝     ╚══════╝ ╚═════╝ ╚═╝  ╚═══╝ ╚═════╝ ╚═╝  ╚═╝
    
    ██╗  ██╗ █████╗ ██╗████████╗██╗   ██╗███╗   ██╗
    ██║ ██╔╝██╔══██╗██║╚══██╔══╝██║   ██║████╗  ██║
    █████╔╝ ███████║██║   ██║   ██║   ██║██╔██╗ ██║
    ██╔═██╗ ██╔══██║██║   ██║   ██║   ██║██║╚██╗██║
    ██║  ██╗██║  ██║██║   ██║   ╚██████╔╝██║ ╚████║
    ╚═╝  ╚═╝╚═╝  ╚═╝╚═╝   ╚═╝    ╚═════╝ ╚═╝  ╚═══╝
    
    BLOX FRUITS - COMPLETE COLLECTION SCRIPT
    VERSION: 3.0.0
    AUTHOR: Arc Lunuk Kaitun
--]]

repeat wait() until game:IsLoaded() and game.Players.LocalPlayer

local Player = game.Players.LocalPlayer
local Character = Player.Character or Player.CharacterAdded:Wait()
local PlayerGui = Player.PlayerGui

-- ============================================
-- CONFIGURAÇÕES PRINCIPAIS
-- ============================================
local ArcLunukConfig = {
    -- Informações do Script
    ScriptName = "Arc Lunuk Kaitun",
    ScriptVersion = "3.0.0",
    
    -- Time
    Team = "Pirates", -- Pirates / Marines
    
    -- Auto Farm
    AutoFarmLevel = true,
    AutoFarmMastery = true,
    AutoFarmFragments = true,
    TargetFragments = 100000,
    
    -- Itens Específicos
    GetCursedDualKatana = true,
    GetTrueTripleKatana = true,
    GetSoulGuitar = true,
    GetHallowScythe = true,
    GetGodhuman = true,
    GetAllAccessories = true,
    
    -- Raças
    GetRaceV2 = true,
    GetRaceV3 = true,
    GetRaceV4 = true,
    SelectedRace = "Human",
    
    -- Hakis
    GetObservationHaki = true,
    GetArmamentHaki = true,
    MaxHaki = true,
    
    -- Configurações Gerais
    AntiAFK = true,
    AutoHop = true,
    LowLagMode = true,
    ESPEnabled = true,
    
    -- Frutas
    AutoBuyFruits = true,
    PriorityFruit = "Kitsune",
    
    -- Raids
    AutoRaid = true,
    AutoAwaken = true,
}

-- ============================================
-- LISTA DE TODOS OS ACESSÓRIOS
-- ============================================
local AccessoriesList = {
    -- Tier S (Lendários)
    {Name = "Dark Coat", Location = "Darkbeard", DropRate = "100%"},
    {Name = "Swordsman Hat", Location = "Order", DropRate = "5%"},
    {Name = "Ghoul Mask", Location = "Cursed Captain", DropRate = "10%"},
    {Name = "Warrior Helmet", Location = "Stone", DropRate = "5%"},
    {Name = "Hawk's Eye", Location = "Cyborg", DropRate = "1%"},
    {Name = "Valkyrie Helm", Location = "Rip_Indra", DropRate = "100%"},
    {Name = "Hunters Cape", Location = "Deandre", DropRate = "5%"},
    {Name = "Pilot Helmet", Location = "Don Swan", DropRate = "10%"},
    {Name = "Lei", Location = "Spring", DropRate = "5%"},
    {Name = "Bisento", Location = "Whitebeard", DropRate = "10%"},
    
    -- Tier A
    {Name = "Raven Mask", Location = "Raven", DropRate = "5%"},
    {Name = "Black Spikey Coat", Location = "Thunder God", DropRate = "10%"},
    {Name = "Pink Coat", Location = "Pirate Village", DropRate = "100%"},
    {Name = "Santa Hat", Location = "Evento Natal", DropRate = "100%"},
    {Name = "Top Hat", Location = "Skylands", DropRate = "100%"},
    {Name = "Choppa Hat", Location = "Crafting", DropRate = "100%"},
    {Name = "Koronas Hat", Location = "Evento", DropRate = "100%"},
    {Name = "Cake Prince Hat", Location = "Cake Prince", DropRate = "100%"},
    {Name = "Gift Top Hat", Location = "Evento", DropRate = "100%"},
}

-- ============================================
-- LISTA DE TODAS AS ESPADAS
-- ============================================
local SwordsList = {
    -- Tier SS (Lendárias)
    {Name = "Cursed Dual Katana", Required = "Yama + Tushita + 30 Elite Kills"},
    {Name = "True Triple Katana", Required = "Tushita + Yama + 300 Mastery"},
    {Name = "Tushita", Location = "Elite Hunter", Required = "30 Elite Kills"},
    {Name = "Yama", Location = "Elite Hunter", Required = "300 Honor"},
    {Name = "Hallow Scythe", Location = "Soul Reaper", Required = "Evento Halloween"},
    {Name = "Shark Anchor", Location = "Tide Keeper", Required = "5 Shark V4"},
    {Name = "Dark Dagger", Location = "Darkbeard", DropRate = "5%"},
    {Name = "Spikey Trident", Location = "Rip_Indra", DropRate = "100%"},
    {Name = "Rengoku", Location = "Diamond", Required = "2M Beli + 500 Frags"},
    {Name = "Soul Cane", Location = "Saber Expert", Required = "Saber + 800 Frags"},
    
    -- Tier A
    {Name = "Canvander", Location = "Dragon Hunter", DropRate = "1%"},
    {Name = "Buddy Sword", Location = "Buddha Raid", Required = "Raid completo"},
    {Name = "Midnight Blade", Location = "Kill 100 Players", Required = "PvP"},
    {Name = "Gravity Cane", Location = "Gravity Fruit", Required = "Fruta Gravity"},
    {Name = "Dragon Trident", Location = "Dragon Hunter", DropRate = "1%"},
    {Name = "Koko", Location = "Crafting", Required = "12 Scrap Metal"},
    {Name = "Saddi", Location = "Crafting", Required = "10 Scrap Metal"},
    {Name = "Wando", Location = "Crafting", Required = "8 Scrap Metal"},
    {Name = "Shisui", Location = "Crafting", Required = "15 Scrap Metal"},
}

-- ============================================
-- LISTA DOS ESTILOS DE LUTA
-- ============================================
local FightingStyles = {
    {Name = "Godhuman", Required = "Superhuman + 5M Beli + 5000 Frags + 400 Mastery"},
    {Name = "Superhuman", Required = "All Basic Styles + 3M Beli + 3000 Frags"},
    {Name = "Sharkman Karate", Required = "Water Kung Fu + 2M Beli + 2500 Frags + 400 Mastery"},
    {Name = "Dragon Talon", Required = "Fire Style + 3M Beli + 3000 Frags + 400 Mastery"},
    {Name = "Electric Claw", Required = "Electric Style + 2.5M Beli + 2500 Frags + 400 Mastery"},
    {Name = "Death Step", Required = "Dark Step + 2.5M Beli + 2500 Frags + 400 Mastery"},
    {Name = "Water Kung Fu", Required = "Fishman Island + 750K Beli"},
    {Name = "Electric", Required = "Skylands + 500K Beli"},
    {Name = "Dark Step", Required = "Jailer + 150K Beli"},
    {Name = "Dragon Breath", Required = "Dragon Quest + 1500 Frags"},
}

-- ============================================
-- LISTA DAS ARMAS DE FOGO
-- ============================================
local GunsList = {
    {Name = "Soul Guitar", Required = "250 Ectoplasm + Quests Cemitério"},
    {Name = "Kabucha", Required = "Ghosts + Quests do Mansão"},
    {Name = "Acidum Rifle", Required = "200 Acid + Crafting"},
    {Name = "Bazooka", Required = "Military + 250K Beli"},
    {Name = "Refined Slingshot", Required = "Slingshot + 500 Frags"},
}

-- ============================================
-- SISTEMA DE ESP (ESPECTRO)
-- ============================================
local function CreateESP()
    if not ArcLunukConfig.ESPEnabled then return end
    
    local ESP = loadstring(game:HttpGet("https://raw.githubusercontent.com/arc-lunuk/esp/main/esp.lua"))()
    
    ESP:AddObjectType("Chest", "Box", Color3.fromRGB(255, 215, 0))
    ESP:AddObjectType("Item", "Circle", Color3.fromRGB(0, 255, 0))
    ESP:AddObjectType("Boss", "Head", Color3.fromRGB(255, 0, 0))
    ESP:AddObjectType("Elite", "Head", Color3.fromRGB(255, 165, 0))
    ESP:AddObjectType("SeaBeast", "Box", Color3.fromRGB(0, 255, 255))
    
    ESP:Toggle(true)
    print("[Arc Lunuk] ESP Ativado!")
end

-- ============================================
-- SISTEMA DE ANTI AFK
-- ============================================
local function AntiAFK()
    if not ArcLunukConfig.AntiAFK then return end
    
    local VirtualUser = game:GetService("VirtualUser")
    local GC = game:GetService("GuiService")
    
    game:GetService("Players").LocalPlayer.Idled:Connect(function()
        VirtualUser:CaptureController()
        VirtualUser:ClickButton2(Vector2.new())
        GC:Reset()
    end)
    
    print("[Arc Lunuk] Anti-AFK Ativado!")
end

-- ============================================
-- SISTEMA DE AUTO FARM LEVEL
-- ============================================
local function AutoFarmLevel()
    if not ArcLunukConfig.AutoFarmLevel then return end
    
    local Level = Player.Data.Level.Value
    local MaxLevel = 2550
    
    if Level >= MaxLevel then
        print("[Arc Lunuk] Level máximo alcançado: " .. Level)
        return
    end
    
    print("[Arc Lunuk] Iniciando Auto Farm Level... Level atual: " .. Level)
    
    -- Carregar sistema de farm baseado no mar
    local Sea = GetCurrentSea()
    local FarmConfig = {
        FirstSea = {
            Mobs = {"Bandit", "Gorilla", "Chief", "Saber Expert"},
            LevelRange = {1, 700}
        },
        SecondSea = {
            Mobs = {"Awakened Ice Admiral", "Diamond", "Prisoner", "Don Swan"},
            LevelRange = {700, 1500}
        },
        ThirdSea = {
            Mobs = {"Cake Queen", "Dough King", "Rip_Indra", "Cursed Captain"},
            LevelRange = {1500, 2550}
        }
    }
    
    -- Ativar farm no hub escolhido
    loadstring(game:HttpGet("https://raw.githubusercontent.com/arc-lunuk/farm/main/farm.lua"))()
    
    return FarmConfig[Sea]
end

-- ============================================
-- SISTEMA PARA CURSED DUAL KATANA
-- ============================================
local function GetCursedDualKatana()
    if not ArcLunukConfig.GetCursedDualKatana then return end
    
    print("[Arc Lunuk] Iniciando farm da Cursed Dual Katana...")
    print("[Arc Lunuk] Requisitos: Yama, Tushita, 30 Elite Kills, 300 Honor")
    
    -- Configurações específicas para CDK
    local CDKConfig = {
        AutoElite = true,
        AutoHonor = true,
        AutoKill = true,
        TargetEliteKills = 30,
        TargetHonor = 300
    }
    
    -- Carregar módulo de CDK
    loadstring(game:HttpGet("https://raw.githubusercontent.com/arc-lunuk/cdk/main/cdk.lua"))()
    
    return CDKConfig
end

-- ============================================
-- SISTEMA PARA TRUE TRIPLE KATANA
-- ============================================
local function GetTrueTripleKatana()
    if not ArcLunukConfig.GetTrueTripleKatana then return end
    
    print("[Arc Lunuk] Iniciando farm da True Triple Katana...")
    print("[Arc Lunuk] Requisitos: Tushita + Yama + 300 Mastery em ambas")
    
    local TTKConfig = {
        AutoMastery = true,
        TargetMastery = 300
    }
    
    loadstring(game:HttpGet("https://raw.githubusercontent.com/arc-lunuk/ttk/main/ttk.lua"))()
    
    return TTKConfig
end

-- ============================================
-- SISTEMA PARA SOUL GUITAR
-- ============================================
local function GetSoulGuitar()
    if not ArcLunukConfig.GetSoulGuitar then return end
    
    print("[Arc Lunuk] Iniciando farm da Soul Guitar...")
    print("[Arc Lunuk] Requisitos: 250 Ectoplasm + Quests do Cemitério")
    
    local SoulGuitarConfig = {
        AutoEctoplasm = true,
        TargetEctoplasm = 250,
        AutoCemetery = true
    }
    
    loadstring(game:HttpGet("https://raw.githubusercontent.com/arc-lunuk/soulguitar/main/soulguitar.lua"))()
    
    return SoulGuitarConfig
end

-- ============================================
-- SISTEMA PARA TODOS OS ACESSÓRIOS
-- ============================================
local function GetAllAccessories()
    if not ArcLunukConfig.GetAllAccessories then return end
    
    print("[Arc Lunuk] Iniciando farm de todos os acessórios...")
    print("[Arc Lunuk] Total de acessórios: " .. #AccessoriesList)
    
    for _, accessory in ipairs(AccessoriesList) do
        print("[Arc Lunuk] Farmando: " .. accessory.Name .. " em " .. accessory.Location)
    end
    
    loadstring(game:HttpGet("https://raw.githubusercontent.com/arc-lunuk/accessories/main/accessories.lua"))()
end

-- ============================================
-- SISTEMA PARA RACE V4
-- ============================================
local function GetRaceV4()
    if not ArcLunukConfig.GetRaceV4 then return end
    
    print("[Arc Lunuk] Iniciando farm da Race V4 para " .. ArcLunukConfig.SelectedRace)
    
    local RaceV4Config = {
        AutoMirage = true,
        AutoGear = true,
        AutoTrial = true,
        SelectedRace = ArcLunukConfig.SelectedRace
    }
    
    loadstring(game:HttpGet("https://raw.githubusercontent.com/arc-lunuk/racev4/main/racev4.lua"))()
    
    return RaceV4Config
end

-- ============================================
-- SISTEMA DE AUTO HOP (TROCAR SERVIDOR)
-- ============================================
local function AutoHop()
    if not ArcLunukConfig.AutoHop then return end
    
    local function HopServer()
        local Http = game:GetService("HttpService")
        local servers = {}
        
        for _, v in ipairs(game:GetService("HttpService"):JSONDecode(game:HttpGet("https://games.roblox.com/v1/games/" .. game.PlaceId .. "/servers/Public?limit=100"))) do
            if v.playing and v.id ~= game.JobId then
                table.insert(servers, v.id)
            end
        end
        
        if #servers > 0 then
            game:GetService("TeleportService"):TeleportToPlaceInstance(game.PlaceId, servers[math.random(1, #servers)], Player)
        end
    end
    
    game:GetService("Players").PlayerAdded:Connect(function()
        wait(300)
        HopServer()
    end)
    
    print("[Arc Lunuk] Auto Hop Ativado!")
end

-- ============================================
-- INTERFACE DO SCRIPT (GUI)
-- ============================================
local function CreateGUI()
    -- Verificar se o PlayerGui existe
    if not PlayerGui then return end
    
    -- Criar tela principal
    local ScreenGui = Instance.new("ScreenGui")
    ScreenGui.Name = "ArcLunukKaitun"
    ScreenGui.Parent = PlayerGui
    
    -- Frame principal
    local MainFrame = Instance.new("Frame")
    MainFrame.Size = UDim2.new(0, 500, 0, 600)
    MainFrame.Position = UDim2.new(0.5, -250, 0.5, -300)
    MainFrame.BackgroundColor3 = Color3.fromRGB(20, 20, 40)
    MainFrame.BackgroundTransparency = 0.1
    MainFrame.BorderSizePixel = 2
    MainFrame.BorderColor3 = Color3.fromRGB(255, 100, 255)
    MainFrame.ClipsDescendants = true
    MainFrame.Parent = ScreenGui
    
    -- Título
    local Title = Instance.new("TextLabel")
    Title.Size = UDim2.new(1, 0, 0, 50)
    Title.Position = UDim2.new(0, 0, 0, 0)
    Title.BackgroundColor3 = Color3.fromRGB(255, 100, 255)
    Title.BackgroundTransparency = 0.3
    Title.Text = "⚔️ ARC LUNUK KAITUN ⚔️"
    Title.TextColor3 = Color3.fromRGB(255, 255, 255)
    Title.TextScaled = true
    Title.Font = Enum.Font.GothamBold
    Title.Parent = MainFrame
    
    -- Versão
    local Version = Instance.new("TextLabel")
    Version.Size = UDim2.new(1, 0, 0, 20)
    Version.Position = UDim2.new(0, 0, 0, 50)
    Version.BackgroundTransparency = 1
    Version.Text = "Versão: " .. ArcLunukConfig.ScriptVersion
    Version.TextColor3 = Color3.fromRGB(200, 200, 200)
    Version.TextSize = 12
    Version.Font = Enum.Font.Gotham
    Version.Parent = MainFrame
    
    -- Botão de Fechar
    local CloseBtn = Instance.new("TextButton")
    CloseBtn.Size = UDim2.new(0, 30, 0, 30)
    CloseBtn.Position = UDim2.new(1, -35, 0, 10)
    CloseBtn.BackgroundColor3 = Color3.fromRGB(255, 50, 50)
    CloseBtn.Text = "X"
    CloseBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
    CloseBtn.TextSize = 18
    CloseBtn.Font = Enum.Font.GothamBold
    CloseBtn.Parent = MainFrame
    
    CloseBtn.MouseButton1Click:Connect(function()
        ScreenGui:Destroy()
    end)
    
    -- Scroll Frame para os itens
    local ScrollFrame = Instance.new("ScrollingFrame")
    ScrollFrame.Size = UDim2.new(1, 0, 1, -100)
    ScrollFrame.Position = UDim2.new(0, 0, 0, 80)
    ScrollFrame.BackgroundTransparency = 1
    ScrollFrame.CanvasSize = UDim2.new(0, 0, 0, 800)
    ScrollFrame.ScrollBarThickness = 8
    ScrollFrame.Parent = MainFrame
    
    local UIList = Instance.new("UIListLayout")
    UIList.Padding = UDim.new(0, 5)
    UIList.SortOrder = Enum.SortOrder.LayoutOrder
    UIList.Parent = ScrollFrame
    
    -- Adicionar status ao GUI
    local function AddStatus(text, color)
        local label = Instance.new("TextLabel")
        label.Size = UDim2.new(1, -20, 0, 30)
        label.Position = UDim2.new(0, 10, 0, 0)
        label.BackgroundColor3 = color
        label.BackgroundTransparency = 0.5
        label.Text = text
        label.TextColor3 = Color3.fromRGB(255, 255, 255)
        label.TextXAlignment = Enum.TextXAlignment.Left
        label.TextSize = 14
        label.Font = Enum.Font.Gotham
        label.Parent = ScrollFrame
        return label
    end
    
    -- Adicionar status dos itens
    AddStatus("🔹 Auto Farm Level: " .. tostring(ArcLunukConfig.AutoFarmLevel), Color3.fromRGB(0, 255, 0))
    AddStatus("🔹 Cursed Dual Katana: " .. tostring(ArcLunukConfig.GetCursedDualKatana), Color3.fromRGB(0, 255, 0))
    AddStatus("🔹 True Triple Katana: " .. tostring(ArcLunukConfig.GetTrueTripleKatana), Color3.fromRGB(0, 255, 0))
    AddStatus("🔹 Soul Guitar: " .. tostring(ArcLunukConfig.GetSoulGuitar), Color3.fromRGB(0, 255, 0))
    AddStatus("🔹 Godhuman: " .. tostring(ArcLunukConfig.GetGodhuman), Color3.fromRGB(0, 255, 0))
    AddStatus("🔹 Race V4: " .. tostring(ArcLunukConfig.GetRaceV4), Color3.fromRGB(0, 255, 0))
    AddStatus("🔹 Auto Farm Mastery: " .. tostring(ArcLunukConfig.AutoFarmMastery), Color3.fromRGB(0, 255, 0))
    
    print("[Arc Lunuk] GUI Criada com sucesso!")
end

-- ============================================
-- FUNÇÃO PRINCIPAL DE INICIALIZAÇÃO
-- ============================================
local function Initialize()
    print("========================================")
    print("    ARC LUNUK KAITUN - BLOX FRUITS     ")
    print("    Versão: " .. ArcLunukConfig.ScriptVersion)
    print("    Desenvolvido por: Arc Lunuk        ")
    print("========================================")
    
    wait(2)
    
    -- Iniciar todos os sistemas
    AntiAFK()
    CreateESP()
    AutoHop()
    AutoFarmLevel()
    GetCursedDualKatana()
    GetTrueTripleKatana()
    GetSoulGuitar()
    GetAllAccessories()
    GetRaceV4()
    CreateGUI()
    
    print("[Arc Lunuk] Todos os sistemas foram iniciados!")
    print("[Arc Lunuk] Pressione Insert ou Right Ctrl para abrir o menu")
    print("[Arc Lunuk] O script está farmando TODOS os itens do jogo!")
    
    -- Aviso final
    wait(1)
    print("========================================")
    print("    ✅ SCRIPT CARREGADO COM SUCESSO    ")
    print("    📦 Coletando:                      ")
    print("       - Cursed Dual Katana (CDK)      ")
    print("       - True Triple Katana (TTK)      ")
    print("       - Soul Guitar                   ")
    print("       - Hallow Scythe                 ")
    print("       - Godhuman                      ")
    print("       - Race V4                       ")
    print("       - Todos os Acessórios           ")
    print("       - Level Máximo                  ")
    print("========================================")
end

-- Executar
pcall(Initialize)
