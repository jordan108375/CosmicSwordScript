# CosmicSwordScript
Script sword
-- Script untuk Pedang Hitam dengan Aura Cosmic
local sword = Instance.new("Tool")
sword.Name = "Cosmic Sword"
sword.RequiresHandle = true
sword.Parent = game.Players.LocalPlayer.Backpack

local handle = Instance.new("Part")
handle.Name = "Handle"
handle.Size = Vector3.new(1, 5, 1)
handle.BrickColor = BrickColor.new("Really black")
handle.Material = Enum.Material.SmoothPlastic
handle.Anchored = false
handle.CanCollide = false
handle.Parent = sword

local aura = Instance.new("Part")
aura.Size = Vector3.new(8, 8, 8)
aura.Shape = Enum.PartType.Ball
aura.Position = sword.Handle.Position
aura.Anchored = false
aura.CanCollide = false
aura.Material = Enum.Material.SmoothPlastic
aura.BrickColor = BrickColor.new("Bright blue")
aura.Transparency = 0.5
aura.Parent = sword

local particleEmitter = Instance.new("ParticleEmitter")
particleEmitter.Color = ColorSequence.new(Color3.fromRGB(0, 255, 255))
particleEmitter.Texture = "rbxassetid://248457455"
particleEmitter.Lifetime = NumberRange.new(1, 2)
particleEmitter.Rate = 100
particleEmitter.Size = NumberSequence.new(0.5, 2)
particleEmitter.Parent = aura

local damage = 1000

sword.Activated:Connect(function()
    local character = sword.Parent
    local humanoid = character:FindFirstChild("Humanoid")
    if humanoid then
        humanoid:TakeDamage(damage)
        print("Damage 1000 diberikan!")
    end
end)

sword.Equipped:Connect(function()
    sword.Handle.Touched:Connect(function(hit)
        local character = hit.Parent
        local humanoid = character:FindFirstChild("Humanoid")
        if humanoid and character ~= sword.Parent then
            humanoid:TakeDamage(damage)
        end
    end)
end)
