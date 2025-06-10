local tool = script.Parent
local damage = 20
local debounce = false

-- Called when sword touches something
local function onTouch(hit)
    if not debounce and tool.Parent then
        local character = tool.Parent
        local humanoid = hit.Parent and hit.Parent:FindFirstChild("Humanoid")

        if humanoid and hit.Parent ~= character then
            debounce = true
            humanoid:TakeDamage(damage)
            wait(0.5)
            debounce = false
        end
    end
end

-- Connect touch event when equipped
tool.Equipped:Connect(function()
    tool.Handle.Touched:Connect(onTouch)
end)
