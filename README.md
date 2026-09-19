local player = game.Players.LocalPlayer
local screenGui = script.Parent
local blackFrame = screenGui:WaitForChild("BlackFrame")
local userInputService = game:GetService("UserInputService")

-- กำหนดปุ่มสำหรับเปิด/ปิด (ในที่นี้ใช้ปุ่ม F บนคีย์บอร์ด)
local toggleKey = Enum.KeyCode.F

-- ตัวแปรเก็บสถานะจอดำ
local isBlack = false

local function toggleBlackScreen()
	isBlack = not isBlack
	blackFrame.Visible = isBlack
	
	if isBlack then
		print("เปิดจอดำ")
	else
		print("ปิดจอดำ")
	end
end

-- ตรวจสอบการกดปุ่ม
userInputService.InputBegan:Connect(function(input, gameProcessed)
	-- ถ้าผู้เล่นไม่ได้พิมพ์แชทอยู่
	if not gameProcessed and input.KeyCode == toggleKey then
		toggleBlackScreen()
	end
end)
