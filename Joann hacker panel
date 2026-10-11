-- Panel Joann Hacker v2 (Integración c00lgui con Control Absoluto de Audio)
local Players = game:GetService("Players")
local Lighting = game:GetService("Lighting")
local Workspace = game:GetService("Workspace")
local LocalPlayer = Players.LocalPlayer
local PlayerGui = LocalPlayer:WaitForChild("PlayerGui")

local MI_TEXTURA_ID = "rbxassetid://130779378408216"

-- Limpieza previa
if Workspace:FindFirstChild("JoannGlobalHint") then Workspace.JoannGlobalHint:Destroy() end
if PlayerGui:FindFirstChild("JoannTrollGui") then PlayerGui.JoannTrollGui:Destroy() end

-- Variable para controlar el estado de la música
local estadoMusica = true

-- 1. Ejecutar c00lgui bloqueando sus imágenes feas en pantalla
task.spawn(function()
    pcall(function()
        local connection
        connection = PlayerGui.ChildAdded:Connect(function(child)
            if child.Name ~= "JoannTrollGui" then
                task.wait()
                for _, descendant in ipairs(child:GetDescendants()) do
                    if descendant:IsA("ImageLabel") or descendant:IsA("ImageButton") then
                        if descendant.Image ~= MI_TEXTURA_ID then
                            descendant.Visible = false
                            descendant:Destroy()
                        end
                    end
                end
            end
        end)
        
        loadstring(game:HttpGet("https://scriptblox.com/raw/Universal-Script-c00lgui-Reborn-By-rc7-v3rx-F3X-Leaked-246234"))()
        
        task.wait(2.5)
        if connection then connection:Disconnect() end
    end)
end)

-- Bucle de control forzado del panel (mantiene la música apagada cuando apretás Stop)
task.spawn(function()
    while true do
        task.wait(0.1)
        if not estadoMusica then
            for _, obj in ipairs(game:GetDescendants()) do
                if obj:IsA("Sound") then
                    obj.Volume = 0
                    obj:Stop()
                end
            end
        end
    end
end)

-- 2. Mensaje Global
local GlobalHint = Instance.new("Hint", Workspace)
GlobalHint.Name = "JoannGlobalHint"
GlobalHint.Text = "🚨 ¡ JUEGO HACKEADO POR JOANN HACKER ! 🚨"

-- 3. Modo Disco Global
local colorCorrection = Instance.new("ColorCorrectionEffect", Lighting)
colorCorrection.Name = "JoannDiscoEffect"
colorCorrection.Enabled = false

local discoActive = false
task.spawn(function()
    while true do
        task.wait(0.3)
        if discoActive then
            colorCorrection.Enabled = true
            colorCorrection.TintColor = Color3.fromHSV(math.random(), 1, 1)
        end
    end
end)

-- 4. Skybox
local currentSky = Lighting:FindFirstChildOfClass("Sky")
if not currentSky then
    currentSky = Instance.new("Sky")
    currentSky.Name = "JoannSkybox"
    currentSky.Parent = Lighting
end

local origBk = currentSky.SkyboxBk
local origDn = currentSky.SkyboxDn
local origFt = currentSky.SkyboxFt
local origLf = currentSky.SkyboxLf
local origRt = currentSky.SkyboxRt
local origUp = currentSky.SkyboxUp

local function cambiarSkybox(activar)
    if currentSky then
        if activar then
            currentSky.SkyboxBk = MI_TEXTURA_ID
            currentSky.SkyboxDn = MI_TEXTURA_ID
            currentSky.SkyboxFt = MI_TEXTURA_ID
            currentSky.SkyboxLf = MI_TEXTURA_ID
            currentSky.SkyboxRt = MI_TEXTURA_ID
            currentSky.SkyboxUp = MI_TEXTURA_ID
        else
            currentSky.SkyboxBk = origBk
            currentSky.SkyboxDn = origDn
            currentSky.SkyboxFt = origFt
            currentSky.SkyboxLf = origLf
            currentSky.SkyboxRt = origRt
            currentSky.SkyboxUp = origUp
        end
    end
end

-- 5. Decal Spam
local function ejecutarDecalSpam()
    local faces = {
        Enum.NormalId.Front, Enum.NormalId.Back, 
        Enum.NormalId.Top, Enum.NormalId.Bottom, 
        Enum.NormalId.Left, Enum.NormalId.Right
    }
    
    for _, part in ipairs(Workspace:GetDescendants()) do
        if part:IsA("BasePart") then
            for _, child in ipairs(part:GetChildren()) do
                if child:IsA("Decal") and child.Name == "JoannSpamDecal" then
                    child:Destroy()
                end
            end
            
            for _, face in ipairs(faces) do
                local decal = Instance.new("Decal")
                decal.Name = "JoannSpamDecal"
                decal.Texture = MI_TEXTURA_ID
                decal.Face = face
                decal.Parent = part
            end
        end
    end
end

-- 6. Panel GUI Completo
local ScreenGui = Instance.new("ScreenGui", PlayerGui)
ScreenGui.Name = "JoannTrollGui"
ScreenGui.ResetOnSpawn = false
ScreenGui.IgnoreGuiInset = true

-- Overlay Jumpscare
local JumpscareOverlay = Instance.new("Frame", ScreenGui)
JumpscareOverlay.Name = "JumpscareOverlay"
JumpscareOverlay.Size = UDim2.new(1, 0, 1, 0)
JumpscareOverlay.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
JumpscareOverlay.Visible = false
JumpscareOverlay.ZIndex = 100

local JumpImage = Instance.new("ImageLabel", JumpscareOverlay)
JumpImage.Size = UDim2.new(1, 0, 1, 0)
JumpImage.BackgroundTransparency = 1
JumpImage.Image = MI_TEXTURA_ID
JumpImage.ZIndex = 101

local JumpText = Instance.new("TextLabel", JumpscareOverlay)
JumpText.Size = UDim2.new(1, 0, 0, 80)
JumpText.Position = UDim2.new(0, 0, 0.8, 0)
JumpText.BackgroundTransparency = 1
JumpText.Text = "¡¡ TE SORPRENDIÓ JOANN HACKER !! 😱"
JumpText.TextColor3 = Color3.fromRGB(255, 0, 0)
JumpText.TextStrokeColor3 = Color3.fromRGB(255, 255, 255)
JumpText.TextStrokeTransparency = 0
JumpText.Font = Enum.Font.GothamBold
JumpText.TextSize = 32
JumpText.ZIndex = 102

-- Main Frame
local MainFrame = Instance.new("Frame", ScreenGui)
MainFrame.Size = UDim2.new(0, 270, 0, 325)
MainFrame.Position = UDim2.new(0.08, 0, 0.25, 0)
MainFrame.BackgroundColor3 = Color3.fromRGB(18, 18, 22)
MainFrame.BorderSizePixel = 0
MainFrame.Active = true
MainFrame.Draggable = true

Instance.new("UICorner", MainFrame).CornerRadius = UDim.new(0, 12)
local MainStroke = Instance.new("UIStroke", MainFrame)
MainStroke.Color = Color3.fromRGB(190, 45, 210)
MainStroke.Thickness = 2.5

-- TopBar
local TopBar = Instance.new("Frame", MainFrame)
TopBar.Size = UDim2.new(1, 0, 0, 38)
TopBar.BackgroundColor3 = Color3.fromRGB(140, 30, 180)
TopBar.BorderSizePixel = 0
Instance.new("UICorner", TopBar).CornerRadius = UDim.new(0, 12)

local Title = Instance.new("TextLabel", TopBar)
Title.Size = UDim2.new(1, 0, 1, 0)
Title.BackgroundTransparency = 1
Title.Text = "⚡ JOANN HACKER PANEL v2 ⚡"
Title.TextColor3 = Color3.fromRGB(255, 255, 255)
Title.Font = Enum.Font.GothamBold
Title.TextSize = 13

-- Botón Disco
local DiscoBtn = Instance.new("TextButton", MainFrame)
DiscoBtn.Size = UDim2.new(0.88, 0, 0, 34)
DiscoBtn.Position = UDim2.new(0.06, 0, 0, 48)
DiscoBtn.BackgroundColor3 = Color3.fromRGB(80, 30, 140)
DiscoBtn.Text = "Activar Modo Disco 🪩"
DiscoBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
DiscoBtn.Font = Enum.Font.GothamBold
DiscoBtn.TextSize = 12
Instance.new("UICorner", DiscoBtn).CornerRadius = UDim.new(0, 8)

DiscoBtn.MouseButton1Click:Connect(function()
    discoActive = not discoActive
    if discoActive then
        DiscoBtn.Text = "Apagar Modo Disco 🪩"
        DiscoBtn.BackgroundColor3 = Color3.fromRGB(40, 160, 40)
    else
        DiscoBtn.Text = "Activar Modo Disco 🪩"
        DiscoBtn.BackgroundColor3 = Color3.fromRGB(80, 30, 140)
        colorCorrection.Enabled = false
    end
end)

-- Botón Skybox
local SkyBtn = Instance.new("TextButton", MainFrame)
SkyBtn.Size = UDim2.new(0.88, 0, 0, 34)
SkyBtn.Position = UDim2.new(0.06, 0, 0, 88)
SkyBtn.BackgroundColor3 = Color3.fromRGB(40, 90, 180)
SkyBtn.Text = "Poner Skybox 🌌"
SkyBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
SkyBtn.Font = Enum.Font.GothamBold
SkyBtn.TextSize = 12
Instance.new("UICorner", SkyBtn).CornerRadius = UDim.new(0, 8)

local skyPuesto = false
SkyBtn.MouseButton1Click:Connect(function()
    skyPuesto = not skyPuesto
    if skyPuesto then
        cambiarSkybox(true)
        SkyBtn.Text = "Quitar Skybox 🌌"
        SkyBtn.BackgroundColor3 = Color3.fromRGB(40, 160, 40)
    else
        cambiarSkybox(false)
        SkyBtn.Text = "Poner Skybox 🌌"
        SkyBtn.BackgroundColor3 = Color3.fromRGB(40, 90, 180)
    end
end)

-- Botón Decal Spam
local DecalBtn = Instance.new("TextButton", MainFrame)
DecalBtn.Size = UDim2.new(0.88, 0, 0, 34)
DecalBtn.Position = UDim2.new(0.06, 0, 0, 128)
DecalBtn.BackgroundColor3 = Color3.fromRGB(180, 30, 90)
DecalBtn.Text = "🖼️ Decal Spam Mapa"
DecalBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
DecalBtn.Font = Enum.Font.GothamBold
DecalBtn.TextSize = 12
Instance.new("UICorner", DecalBtn).CornerRadius = UDim.new(0, 8)

DecalBtn.MouseButton1Click:Connect(function()
    ejecutarDecalSpam()
end)

-- Botón Jumpscare
local JumpscareBtn = Instance.new("TextButton", MainFrame)
JumpscareBtn.Size = UDim2.new(0.88, 0, 0, 34)
JumpscareBtn.Position = UDim2.new(0.06, 0, 0, 168)
JumpscareBtn.BackgroundColor3 = Color3.fromRGB(200, 60, 0)
JumpscareBtn.Text = "💥 ¡Lanzar Jumpscare!"
JumpscareBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
JumpscareBtn.Font = Enum.Font.GothamBold
JumpscareBtn.TextSize = 12
Instance.new("UICorner", JumpscareBtn).CornerRadius = UDim.new(0, 8)

JumpscareBtn.MouseButton1Click:Connect(function()
    JumpscareOverlay.Visible = true
    task.delay(2.5, function()
        JumpscareOverlay.Visible = false
    end)
end)

-- Botón Play (Permite la reproducción y sube el volumen)
local PlayBtn = Instance.new("TextButton", MainFrame)
PlayBtn.Size = UDim2.new(0.42, 0, 0, 34)
PlayBtn.Position = UDim2.new(0.06, 0, 0, 208)
PlayBtn.BackgroundColor3 = Color3.fromRGB(40, 160, 40)
PlayBtn.Text = "Play 🎵"
PlayBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
PlayBtn.Font = Enum.Font.GothamBold
PlayBtn.TextSize = 11
Instance.new("UICorner", PlayBtn).CornerRadius = UDim.new(0, 8)

PlayBtn.MouseButton1Click:Connect(function()
    estadoMusica = true
    for _, obj in ipairs(game:GetDescendants()) do
        if obj:IsA("Sound") then
            obj.Volume = 10
            obj:Play()
        end
    end
end)

-- Botón Stop (Bloquea el bucle de c00lgui y apaga todo el sonido al instante)
local StopBtn = Instance.new("TextButton", MainFrame)
StopBtn.Size = UDim2.new(0.42, 0, 0, 34)
StopBtn.Position = UDim2.new(0.52, 0, 0, 208)
StopBtn.BackgroundColor3 = Color3.fromRGB(160, 40, 40)
StopBtn.Text = "Stop 🔇"
StopBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
StopBtn.Font = Enum.Font.GothamBold
StopBtn.TextSize = 11
Instance.new("UICorner", StopBtn).CornerRadius = UDim.new(0, 8)

StopBtn.MouseButton1Click:Connect(function()
    estadoMusica = false
    for _, obj in ipairs(game:GetDescendants()) do
        if obj:IsA("Sound") then
            obj.Volume = 0
            obj:Stop()
        end
    end
end)

-- Botón Cerrar
local CloseBtn = Instance.new("TextButton", MainFrame)
CloseBtn.Size = UDim2.new(0.88, 0, 0, 34)
CloseBtn.Position = UDim2.new(0.06, 0, 0, 250)
CloseBtn.BackgroundColor3 = Color3.fromRGB(70, 70, 70)
CloseBtn.Text = "Cerrar Panel ❌"
CloseBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
CloseBtn.Font = Enum.Font.GothamBold
CloseBtn.TextSize = 12
Instance.new("UICorner", CloseBtn).CornerRadius = UDim.new(0, 8)

CloseBtn.MouseButton1Click:Connect(function()
    ScreenGui:Destroy()
end)
