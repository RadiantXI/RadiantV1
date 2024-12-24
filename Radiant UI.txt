--[[

Rayfield Interface Suite
by Sirius

shlex | Designing + Programming
iRay  | Programming
Max   | Programming

]]



local InterfaceBuild = '1VEX'
local Release = "Build 1.55"
local RayfieldFolder = "Rayfield"
local ConfigurationFolder = RayfieldFolder.."/Configurations"
local ConfigurationExtension = ".rfld"

local HttpService = game:GetService("HttpService")
local request = (syn and syn.request) or (fluxus and fluxus.request) or (http and http.request) or http_request or request

local function getExecutor() 
    local name, version
    if identifyexecutor then 
        name, version = identifyexecutor()
    end
    return { Name = name or "", Version = version or "" }
end

if request then
    pcall(request, {
        Url = "https://analytics.sirius.menu/v1/report/0193dbf8-7da1-79de-b399-2c0f68b0a9ad",
        Method = "POST",
        Headers = {
            ["Content-Type"] = "application/json"
        },
        Body = HttpService:JSONEncode({
            Executor = getExecutor(),
            Script = {
                Interface = InterfaceBuild,
                Release = Release
            }
        })
    })
end

local RayfieldLibrary = {
	Flags = {},
	Theme = {
		Default = {
			TextColor = Color3.fromRGB(240, 240, 240),

			Background = Color3.fromRGB(25, 25, 25),
			Topbar = Color3.fromRGB(34, 34, 34),
			Shadow = Color3.fromRGB(20, 20, 20),

			NotificationBackground = Color3.fromRGB(20, 20, 20),
			NotificationActionsBackground = Color3.fromRGB(230, 230, 230),

			TabBackground = Color3.fromRGB(80, 80, 80),
			TabStroke = Color3.fromRGB(85, 85, 85),
			TabBackgroundSelected = Color3.fromRGB(210, 210, 210),
			TabTextColor = Color3.fromRGB(240, 240, 240),
			SelectedTabTextColor = Color3.fromRGB(50, 50, 50),

			ElementBackground = Color3.fromRGB(35, 35, 35),
			ElementBackgroundHover = Color3.fromRGB(40, 40, 40),
			SecondaryElementBackground = Color3.fromRGB(25, 25, 25),
			ElementStroke = Color3.fromRGB(50, 50, 50),
			SecondaryElementStroke = Color3.fromRGB(40, 40, 40),

			SliderBackground = Color3.fromRGB(50, 138, 220),
			SliderProgress = Color3.fromRGB(50, 138, 220),
			SliderStroke = Color3.fromRGB(58, 163, 255),

			ToggleBackground = Color3.fromRGB(30, 30, 30),
			ToggleEnabled = Color3.fromRGB(0, 146, 214),
			ToggleDisabled = Color3.fromRGB(100, 100, 100),
			ToggleEnabledStroke = Color3.fromRGB(0, 170, 255),
			ToggleDisabledStroke = Color3.fromRGB(125, 125, 125),
			ToggleEnabledOuterStroke = Color3.fromRGB(100, 100, 100),
			ToggleDisabledOuterStroke = Color3.fromRGB(65, 65, 65),

			DropdownSelected = Color3.fromRGB(40, 40, 40),
			DropdownUnselected = Color3.fromRGB(30, 30, 30),

			InputBackground = Color3.fromRGB(30, 30, 30),
			InputStroke = Color3.fromRGB(65, 65, 65),
			PlaceholderColor = Color3.fromRGB(178, 178, 178)
		},

		Ocean = {
			TextColor = Color3.fromRGB(230, 240, 240),

			Background = Color3.fromRGB(20, 30, 30),
			Topbar = Color3.fromRGB(25, 40, 40),
			Shadow = Color3.fromRGB(15, 20, 20),

			NotificationBackground = Color3.fromRGB(25, 35, 35),
			NotificationActionsBackground = Color3.fromRGB(230, 240, 240),

			TabBackground = Color3.fromRGB(40, 60, 60),
			TabStroke = Color3.fromRGB(50, 70, 70),
			TabBackgroundSelected = Color3.fromRGB(100, 180, 180),
			TabTextColor = Color3.fromRGB(210, 230, 230),
			SelectedTabTextColor = Color3.fromRGB(20, 50, 50),

			ElementBackground = Color3.fromRGB(30, 50, 50),
			ElementBackgroundHover = Color3.fromRGB(40, 60, 60),
			SecondaryElementBackground = Color3.fromRGB(30, 45, 45),
			ElementStroke = Color3.fromRGB(45, 70, 70),
			SecondaryElementStroke = Color3.fromRGB(40, 65, 65),

			SliderBackground = Color3.fromRGB(0, 110, 110),
			SliderProgress = Color3.fromRGB(0, 140, 140),
			SliderStroke = Color3.fromRGB(0, 160, 160),

			ToggleBackground = Color3.fromRGB(30, 50, 50),
			ToggleEnabled = Color3.fromRGB(0, 130, 130),
			ToggleDisabled = Color3.fromRGB(70, 90, 90),
			ToggleEnabledStroke = Color3.fromRGB(0, 160, 160),
			ToggleDisabledStroke = Color3.fromRGB(85, 105, 105),
			ToggleEnabledOuterStroke = Color3.fromRGB(50, 100, 100),
			ToggleDisabledOuterStroke = Color3.fromRGB(45, 65, 65),

			DropdownSelected = Color3.fromRGB(30, 60, 60),
			DropdownUnselected = Color3.fromRGB(25, 40, 40),

			InputBackground = Color3.fromRGB(30, 50, 50),
			InputStroke = Color3.fromRGB(50, 70, 70),
			PlaceholderColor = Color3.fromRGB(140, 160, 160)
		},

		AmberGlow = {
			TextColor = Color3.fromRGB(255, 245, 230),

			Background = Color3.fromRGB(45, 30, 20),
			Topbar = Color3.fromRGB(55, 40, 25),
			Shadow = Color3.fromRGB(35, 25, 15),

			NotificationBackground = Color3.fromRGB(50, 35, 25),
			NotificationActionsBackground = Color3.fromRGB(245, 230, 215),

			TabBackground = Color3.fromRGB(75, 50, 35),
			TabStroke = Color3.fromRGB(90, 60, 45),
			TabBackgroundSelected = Color3.fromRGB(230, 180, 100),
			TabTextColor = Color3.fromRGB(250, 220, 200),
			SelectedTabTextColor = Color3.fromRGB(50, 30, 10),

			ElementBackground = Color3.fromRGB(60, 45, 35),
			ElementBackgroundHover = Color3.fromRGB(70, 50, 40),
			SecondaryElementBackground = Color3.fromRGB(55, 40, 30),
			ElementStroke = Color3.fromRGB(85, 60, 45),
			SecondaryElementStroke = Color3.fromRGB(75, 50, 35),

			SliderBackground = Color3.fromRGB(220, 130, 60),
			SliderProgress = Color3.fromRGB(250, 150, 75),
			SliderStroke = Color3.fromRGB(255, 170, 85),

			ToggleBackground = Color3.fromRGB(55, 40, 30),
			ToggleEnabled = Color3.fromRGB(240, 130, 30),
			ToggleDisabled = Color3.fromRGB(90, 70, 60),
			ToggleEnabledStroke = Color3.fromRGB(255, 160, 50),
			ToggleDisabledStroke = Color3.fromRGB(110, 85, 75),
			ToggleEnabledOuterStroke = Color3.fromRGB(200, 100, 50),
			ToggleDisabledOuterStroke = Color3.fromRGB(75, 60, 55),

			DropdownSelected = Color3.fromRGB(70, 50, 40),
			DropdownUnselected = Color3.fromRGB(55, 40, 30),

			InputBackground = Color3.fromRGB(60, 45, 35),
			InputStroke = Color3.fromRGB(90, 65, 50),
			PlaceholderColor = Color3.fromRGB(190, 150, 130)
		},

		Light = {
			TextColor = Color3.fromRGB(40, 40, 40),

			Background = Color3.fromRGB(245, 245, 245),
			Topbar = Color3.fromRGB(230, 230, 230),
			Shadow = Color3.fromRGB(200, 200, 200),

			NotificationBackground = Color3.fromRGB(250, 250, 250),
			NotificationActionsBackground = Color3.fromRGB(240, 240, 240),

			TabBackground = Color3.fromRGB(235, 235, 235),
			TabStroke = Color3.fromRGB(215, 215, 215),
			TabBackgroundSelected = Color3.fromRGB(255, 255, 255),
			TabTextColor = Color3.fromRGB(80, 80, 80),
			SelectedTabTextColor = Color3.fromRGB(0, 0, 0),

			ElementBackground = Color3.fromRGB(240, 240, 240),
			ElementBackgroundHover = Color3.fromRGB(225, 225, 225),
			SecondaryElementBackground = Color3.fromRGB(235, 235, 235),
			ElementStroke = Color3.fromRGB(210, 210, 210),
			SecondaryElementStroke = Color3.fromRGB(210, 210, 210),

			SliderBackground = Color3.fromRGB(150, 180, 220),
			SliderProgress = Color3.fromRGB(100, 150, 200), 
			SliderStroke = Color3.fromRGB(120, 170, 220),

			ToggleBackground = Color3.fromRGB(220, 220, 220),
			ToggleEnabled = Color3.fromRGB(0, 146, 214),
			ToggleDisabled = Color3.fromRGB(150, 150, 150),
			ToggleEnabledStroke = Color3.fromRGB(0, 170, 255),
			ToggleDisabledStroke = Color3.fromRGB(170, 170, 170),
			ToggleEnabledOuterStroke = Color3.fromRGB(100, 100, 100),
			ToggleDisabledOuterStroke = Color3.fromRGB(180, 180, 180),

			DropdownSelected = Color3.fromRGB(230, 230, 230),
			DropdownUnselected = Color3.fromRGB(220, 220, 220),

			InputBackground = Color3.fromRGB(240, 240, 240),
			InputStroke = Color3.fromRGB(180, 180, 180),
			PlaceholderColor = Color3.fromRGB(140, 140, 140)
		},

		Amethyst = {
			TextColor = Color3.fromRGB(240, 240, 240),

			Background = Color3.fromRGB(30, 20, 40),
			Topbar = Color3.fromRGB(40, 25, 50),
			Shadow = Color3.fromRGB(20, 15, 30),

			NotificationBackground = Color3.fromRGB(35, 20, 40),
			NotificationActionsBackground = Color3.fromRGB(240, 240, 250),

			TabBackground = Color3.fromRGB(60, 40, 80),
			TabStroke = Color3.fromRGB(70, 45, 90),
			TabBackgroundSelected = Color3.fromRGB(180, 140, 200),
			TabTextColor = Color3.fromRGB(230, 230, 240),
			SelectedTabTextColor = Color3.fromRGB(50, 20, 50),

			ElementBackground = Color3.fromRGB(45, 30, 60),
			ElementBackgroundHover = Color3.fromRGB(50, 35, 70),
			SecondaryElementBackground = Color3.fromRGB(40, 30, 55),
			ElementStroke = Color3.fromRGB(70, 50, 85),
			SecondaryElementStroke = Color3.fromRGB(65, 45, 80),

			SliderBackground = Color3.fromRGB(100, 60, 150),
			SliderProgress = Color3.fromRGB(130, 80, 180),
			SliderStroke = Color3.fromRGB(150, 100, 200),

			ToggleBackground = Color3.fromRGB(45, 30, 55),
			ToggleEnabled = Color3.fromRGB(120, 60, 150),
			ToggleDisabled = Color3.fromRGB(94, 47, 117),
			ToggleEnabledStroke = Color3.fromRGB(140, 80, 170),
			ToggleDisabledStroke = Color3.fromRGB(124, 71, 150),
			ToggleEnabledOuterStroke = Color3.fromRGB(90, 40, 120),
			ToggleDisabledOuterStroke = Color3.fromRGB(80, 50, 110),

			DropdownSelected = Color3.fromRGB(50, 35, 70),
			DropdownUnselected = Color3.fromRGB(35, 25, 50),

			InputBackground = Color3.fromRGB(45, 30, 60),
			InputStroke = Color3.fromRGB(80, 50, 110),
			PlaceholderColor = Color3.fromRGB(178, 150, 200)
		},

		Green = {
			TextColor = Color3.fromRGB(30, 60, 30),

			Background = Color3.fromRGB(235, 245, 235),
			Topbar = Color3.fromRGB(210, 230, 210),
			Shadow = Color3.fromRGB(200, 220, 200),

			NotificationBackground = Color3.fromRGB(240, 250, 240),
			NotificationActionsBackground = Color3.fromRGB(220, 235, 220),

			TabBackground = Color3.fromRGB(215, 235, 215),
			TabStroke = Color3.fromRGB(190, 210, 190),
			TabBackgroundSelected = Color3.fromRGB(245, 255, 245),
			TabTextColor = Color3.fromRGB(50, 80, 50),
			SelectedTabTextColor = Color3.fromRGB(20, 60, 20),

			ElementBackground = Color3.fromRGB(225, 240, 225),
			ElementBackgroundHover = Color3.fromRGB(210, 225, 21…:Create(KeyMain.NoteTitle, TweenInfo.new(0.4, Enum.EasingStyle.Exponential), {TextTransparency = 1}):Play()
						TweenService:Create(KeyMain.NoteMessage, TweenInfo.new(0.4, Enum.EasingStyle.Exponential), {TextTransparency = 1}):Play()
						TweenService:Create(KeyMain.Hide, TweenInfo.new(0.4, Enum.EasingStyle.Exponential), {ImageTransparency = 1}):Play()
						task.wait(0.45)
						Players.LocalPlayer:Kick("No Attempts Remaining")
						game:Shutdown()
					end
					KeyMain.Input.InputBox.Text = ""
					AttemptsRemaining = AttemptsRemaining - 1
					TweenService:Create(KeyMain, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {Size = UDim2.new(0, 467, 0, 175)}):Play()
					TweenService:Create(KeyMain, TweenInfo.new(0.4, Enum.EasingStyle.Elastic), {Position = UDim2.new(0.495,0,0.5,0)}):Play()
					task.wait(0.1)
					TweenService:Create(KeyMain, TweenInfo.new(0.4, Enum.EasingStyle.Elastic), {Position = UDim2.new(0.505,0,0.5,0)}):Play()
					task.wait(0.1)
					TweenService:Create(KeyMain, TweenInfo.new(0.4, Enum.EasingStyle.Exponential), {Position = UDim2.new(0.5,0,0.5,0)}):Play()
					TweenService:Create(KeyMain, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {Size = UDim2.new(0, 500, 0, 187)}):Play()
				end
			end)

			KeyMain.Hide.MouseButton1Click:Connect(function()
				TweenService:Create(KeyMain, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundTransparency = 1}):Play()
				TweenService:Create(KeyMain, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {Size = UDim2.new(0, 467, 0, 175)}):Play()
				TweenService:Create(KeyMain.Shadow.Image, TweenInfo.new(0.5, Enum.EasingStyle.Exponential), {ImageTransparency = 1}):Play()
				TweenService:Create(KeyMain.Title, TweenInfo.new(0.4, Enum.EasingStyle.Exponential), {TextTransparency = 1}):Play()
				TweenService:Create(KeyMain.Subtitle, TweenInfo.new(0.5, Enum.EasingStyle.Exponential), {TextTransparency = 1}):Play()
				TweenService:Create(KeyMain.KeyNote, TweenInfo.new(0.5, Enum.EasingStyle.Exponential), {TextTransparency = 1}):Play()
				TweenService:Create(KeyMain.Input, TweenInfo.new(0.5, Enum.EasingStyle.Exponential), {BackgroundTransparency = 1}):Play()
				TweenService:Create(KeyMain.Input.UIStroke, TweenInfo.new(0.5, Enum.EasingStyle.Exponential), {Transparency = 1}):Play()
				TweenService:Create(KeyMain.Input.InputBox, TweenInfo.new(0.5, Enum.EasingStyle.Exponential), {TextTransparency = 1}):Play()
				TweenService:Create(KeyMain.NoteTitle, TweenInfo.new(0.4, Enum.EasingStyle.Exponential), {TextTransparency = 1}):Play()
				TweenService:Create(KeyMain.NoteMessage, TweenInfo.new(0.4, Enum.EasingStyle.Exponential), {TextTransparency = 1}):Play()
				TweenService:Create(KeyMain.Hide, TweenInfo.new(0.4, Enum.EasingStyle.Exponential), {ImageTransparency = 1}):Play()
				task.wait(0.51)
				RayfieldLibrary:Destroy()
				KeyUI:Destroy()
			end)
		else
			Passthrough = true
		end
	end
	if Settings.KeySystem then
		repeat task.wait() until Passthrough
	end

	Notifications.Template.Visible = false
	Notifications.Visible = true
	Rayfield.Enabled = true

	task.wait(0.5)
	TweenService:Create(Main, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {BackgroundTransparency = 0}):Play()
	TweenService:Create(Main.Shadow.Image, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {ImageTransparency = 0.6}):Play()
	task.wait(0.1)
	TweenService:Create(LoadingFrame.Title, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {TextTransparency = 0}):Play()
	task.wait(0.05)
	TweenService:Create(LoadingFrame.Subtitle, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {TextTransparency = 0}):Play()
	task.wait(0.05)
	TweenService:Create(LoadingFrame.Version, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {TextTransparency = 0}):Play()


	Elements.Template.LayoutOrder = 100000
	Elements.Template.Visible = false

	Elements.UIPageLayout.FillDirection = Enum.FillDirection.Horizontal
	TabList.Template.Visible = false

	-- Tab
	local FirstTab = false
	local Window = {}
	function Window:CreateTab(Name, Image)
		local SDone = false
		local TabButton = TabList.Template:Clone()
		TabButton.Name = Name
		TabButton.Title.Text = Name
		TabButton.Parent = TabList
		TabButton.Title.TextWrapped = false
		TabButton.Size = UDim2.new(0, TabButton.Title.TextBounds.X + 30, 0, 30)

		if Image then
			if typeof(Image) == 'string' then
				local asset = getIcon(Image)

				TabButton.Image.Image = 'rbxassetid://'..asset.id
				TabButton.Image.ImageRectOffset = asset.imageRectOffset
				TabButton.Image.ImageRectSize = asset.imageRectSize
			else
				TabButton.Image.Image = "rbxassetid://"..Image
			end

			TabButton.Title.AnchorPoint = Vector2.new(0, 0.5)
			TabButton.Title.Position = UDim2.new(0, 37, 0.5, 0)
			TabButton.Image.Visible = true
			TabButton.Title.TextXAlignment = Enum.TextXAlignment.Left
			TabButton.Size = UDim2.new(0, TabButton.Title.TextBounds.X + 52, 0, 30)
		end



		TabButton.BackgroundTransparency = 1
		TabButton.Title.TextTransparency = 1
		TabButton.Image.ImageTransparency = 1
		TabButton.UIStroke.Transparency = 1

		TabButton.Visible = true

		-- Create Elements Page
		local TabPage = Elements.Template:Clone()
		TabPage.Name = Name
		TabPage.Visible = true

		TabPage.LayoutOrder = #Elements:GetChildren()

		for _, TemplateElement in ipairs(TabPage:GetChildren()) do
			if TemplateElement.ClassName == "Frame" and TemplateElement.Name ~= "Placeholder" then
				TemplateElement:Destroy()
			end
		end

		TabPage.Parent = Elements
		if not FirstTab then
			Elements.UIPageLayout.Animated = false
			Elements.UIPageLayout:JumpTo(TabPage)
			Elements.UIPageLayout.Animated = true
		end

		TabButton.UIStroke.Color = SelectedTheme.TabStroke

		if Elements.UIPageLayout.CurrentPage == TabPage then
			TabButton.BackgroundColor3 = SelectedTheme.TabBackgroundSelected
			TabButton.Image.ImageColor3 = SelectedTheme.SelectedTabTextColor
			TabButton.Title.TextColor3 = SelectedTheme.SelectedTabTextColor
		else
			TabButton.BackgroundColor3 = SelectedTheme.TabBackground
			TabButton.Image.ImageColor3 = SelectedTheme.TabTextColor
			TabButton.Title.TextColor3 = SelectedTheme.TabTextColor
		end


		-- Animate
		task.wait(0.1)
		if FirstTab then
			TabButton.BackgroundColor3 = SelectedTheme.TabBackground
			TabButton.Image.ImageColor3 = SelectedTheme.TabTextColor
			TabButton.Title.TextColor3 = SelectedTheme.TabTextColor
			TweenService:Create(TabButton, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {BackgroundTransparency = 0.7}):Play()
			TweenService:Create(TabButton.Title, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {TextTransparency = 0.2}):Play()
			TweenService:Create(TabButton.Image, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {ImageTransparency = 0.2}):Play()
			TweenService:Create(TabButton.UIStroke, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {Transparency = 0.5}):Play()
		else
			FirstTab = Name
			TabButton.BackgroundColor3 = SelectedTheme.TabBackgroundSelected
			TabButton.Image.ImageColor3 = SelectedTheme.SelectedTabTextColor
			TabButton.Title.TextColor3 = SelectedTheme.SelectedTabTextColor
			TweenService:Create(TabButton.Image, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {ImageTransparency = 0}):Play()
			TweenService:Create(TabButton, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {BackgroundTransparency = 0}):Play()
			TweenService:Create(TabButton.Title, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {TextTransparency = 0}):Play()
		end


		TabButton.Interact.MouseButton1Click:Connect(function()
			if Minimised then return end
			TweenService:Create(TabButton, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {BackgroundTransparency = 0}):Play()
			TweenService:Create(TabButton.UIStroke, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {Transparency = 1}):Play()
			TweenService:Create(TabButton.Title, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {TextTransparency = 0}):Play()
			TweenService:Create(TabButton.Image, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {ImageTransparency = 0}):Play()
			TweenService:Create(TabButton, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {BackgroundColor3 = SelectedTheme.TabBackgroundSelected}):Play()
			TweenService:Create(TabButton.Title, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {TextColor3 = SelectedTheme.SelectedTabTextColor}):Play()
			TweenService:Create(TabButton.Image, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {ImageColor3 = SelectedTheme.SelectedTabTextColor}):Play()

			for _, OtherTabButton in ipairs(TabList:GetChildren()) do
				if OtherTabButton.Name ~= "Template" and OtherTabButton.ClassName == "Frame" and OtherTabButton ~= TabButton and OtherTabButton.Name ~= "Placeholder" then
					TweenService:Create(OtherTabButton, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {BackgroundColor3 = SelectedTheme.TabBackground}):Play()
					TweenService:Create(OtherTabButton.Title, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {TextColor3 = SelectedTheme.TabTextColor}):Play()
					TweenService:Create(OtherTabButton.Image, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {ImageColor3 = SelectedTheme.TabTextColor}):Play()
					TweenService:Create(OtherTabButton, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {BackgroundTransparency = 0.7}):Play()
					TweenService:Create(OtherTabButton.Title, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {TextTransparency = 0.2}):Play()
					TweenService:Create(OtherTabButton.Image, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {ImageTransparency = 0.2}):Play()
					TweenService:Create(OtherTabButton.UIStroke, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {Transparency = 0.5}):Play()
				end
			end
			if Elements.UIPageLayout.CurrentPage ~= TabPage then
				Elements.UIPageLayout:JumpTo(TabPage)
			end

		end)

		local Tab = {}

		-- Button
		function Tab:CreateButton(ButtonSettings)
			local ButtonValue = {}

			local Button = Elements.Template.Button:Clone()
			Button.Name = ButtonSettings.Name
			Button.Title.Text = ButtonSettings.Name
			Button.Visible = true
			Button.Parent = TabPage

			Button.BackgroundTransparency = 1
			Button.UIStroke.Transparency = 1
			Button.Title.TextTransparency = 1

			TweenService:Create(Button, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {BackgroundTransparency = 0}):Play()
			TweenService:Create(Button.UIStroke, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {Transparency = 0}):Play()
			TweenService:Create(Button.Title, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {TextTransparency = 0}):Play()	


			Button.Interact.MouseButton1Click:Connect(function()
				local Success, Response = pcall(ButtonSettings.Callback)
				if not Success then
					TweenService:Create(Button, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundColor3 = Color3.fromRGB(85, 0, 0)}):Play()
					TweenService:Create(Button.ElementIndicator, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {TextTransparency = 1}):Play()
					TweenService:Create(Button.UIStroke, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {Transparency = 1}):Play()
					Button.Title.Text = "Callback Error"
					print("Rayfield | "..ButtonSettings.Name.." Callback Error " ..tostring(Response))
					warn('Check docs.sirius.menu for help with Rayfield specific development.')
					task.wait(0.5)
					Button.Title.Text = ButtonSettings.Name
					TweenService:Create(Button, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundColor3 = SelectedTheme.ElementBackground}):Play()
					TweenService:Create(Button.ElementIndicator, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {TextTransparency = 0.9}):Play()
					TweenService:Create(Button.UIStroke, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {Transparency = 0}):Play()
				else
					SaveConfiguration()
					TweenService:Create(Button, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundColor3 = SelectedTheme.ElementBackgroundHover}):Play()
					TweenService:Create(Button.ElementIndicator, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {TextTransparency = 1}):Play()
					TweenService:Create(Button.UIStroke, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {Transparency = 1}):Play()
					task.wait(0.2)
					TweenService:Create(Button, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundColor3 = SelectedTheme.ElementBackground}):Play()
					TweenService:Create(Button.ElementIndicator, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {TextTransparency = 0.9}):Play()
					TweenService:Create(Button.UIStroke, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {Transparency = 0}):Play()
				end
			end)

			Button.MouseEnter:Connect(function()
				TweenService:Create(Button, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundColor3 = SelectedTheme.ElementBackgroundHover}):Play()
				TweenService:Create(Button.ElementIndicator, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {TextTransparency = 0.7}):Play()
			end)

			Button.MouseLeave:Connect(function()
				TweenService:Create(Button, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundColor3 = SelectedTheme.ElementBackground}):Play()
				TweenService:Create(Button.ElementIndicator, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {TextTransparency = 0.9}):Play()
			end)

			function ButtonValue:Set(NewButton)
				Button.Title.Text = NewButton
				Button.Name = NewButton
			end

			return ButtonValue
		end

		-- ColorPicker
		function Tab:CreateColorPicker(ColorPickerSettings) -- by Throit
			ColorPickerSettings.Type = "ColorPicker"
			local ColorPicker = Elements.Template.ColorPicker:Clone()
			local Background = ColorPicker.CPBackground
			local Display = Background.Display
			local Main = Background.MainCP
			local Slider = ColorPicker.ColorSlider
			ColorPicker.ClipsDescendants = true
			ColorPicker.Name = ColorPickerSettings.Name
			ColorPicker.Title.Text = ColorPickerSettings.Name
			ColorPicker.Visible = true
			ColorPicker.Parent = TabPage
			ColorPicker.Size = UDim2.new(1, -10, 0, 45)
			Background.Size = UDim2.new(0, 39, 0, 22)
			Display.BackgroundTransparency = 0
			Main.MainPoint.ImageTransparency = 1
			ColorPicker.Interact.Size = UDim2.new(1, 0, 1, 0)
			ColorPicker.Interact.Position = UDim2.new(0.5, 0, 0.5, 0)
			ColorPicker.RGB.Position = UDim2.new(0, 17, 0, 70)
			ColorPicker.HexInput.Position = UDim2.new(0, 17, 0, 90)
			Main.ImageTransparency = 1
			Background.BackgroundTransparency = 1

			for _, rgbinput in ipairs(ColorPicker.RGB:GetChildren()) do
				if rgbinput:IsA("Frame") then
					rgbinput.BackgroundColor3 = SelectedTheme.InputBackground
					rgbinput.UIStroke.Color = SelectedTheme.InputStroke
				end
			end

			ColorPicker.HexInput.BackgroundColor3 = SelectedTheme.InputBackground
			ColorPicker.HexInput.UIStroke.Color = SelectedTheme.InputStroke

			local opened = false 
			local mouse = Players.LocalPlayer:GetMouse()
			Main.Image = "http://www.roblox.com/asset/?id=11415645739"
			local mainDragging = false 
			local sliderDragging = false 
			ColorPicker.Interact.MouseButton1Down:Connect(function()
				task.spawn(function()
					TweenService:Create(ColorPicker, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundColor3 = SelectedTheme.ElementBackgroundHover}):Play()
					TweenService:Create(ColorPicker.UIStroke, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {Transparency = 1}):Play()
					task.wait(0.2)
					TweenService:Create(ColorPicker, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundColor3 = SelectedTheme.ElementBackground}):Play()
					TweenService:Create(ColorPicker.UIStroke, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {Transparency = 0}):Play()
				end)

				if not opened then
					opened = true 
					TweenService:Create(Background, TweenInfo.new(0.45, Enum.EasingStyle.Exponential), {Size = UDim2.new(0, 18, 0, 15)}):Play()
					task.wait(0.1)
					TweenService:Create(ColorPicker, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {Size = UDim2.new(1, -10, 0, 120)}):Play()
					TweenService:Create(Background, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {Size = UDim2.new(0, 173, 0, 86)}):Play()
					TweenService:Create(Display, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundTransparency = 1}):Play()
					TweenService:Create(ColorPicker.Interact, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {Position = UDim2.new(0.289, 0, 0.5, 0)}):Play()
					TweenService:Create(ColorPicker.RGB, TweenInfo.new(0.8, Enum.EasingStyle.Exponential), {Position = UDim2.new(0, 17, 0, 40)}):Play()
					TweenService:Create(ColorPicker.HexInput, TweenInfo.new(0.5, Enum.EasingStyle.Exponential), {Position = UDim2.new(0, 17, 0, 73)}):Play()
					TweenService:Create(ColorPicker.Interact, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {Size = UDim2.new(0.574, 0, 1, 0)}):Play()
					TweenService:Create(Main.MainPoint, TweenInfo.new(0.2, Enum.EasingStyle.Exponential), {ImageTransparency = 0}):Play()
					TweenService:Create(Main, TweenInfo.new(0.2, Enum.EasingStyle.Exponential), {ImageTransparency = SelectedTheme ~= RayfieldLibrary.Theme.Default and 0.25 or 0.1}):Play()
					TweenService:Create(Background, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundTransparency = 0}):Play()
				else
					opened = false
					TweenService:Create(ColorPicker, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {Size = UDim2.new(1, -10, 0, 45)}):Play()
					TweenService:Create(Background, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {Size = UDim2.new(0, 39, 0, 22)}):Play()
					TweenService:Create(ColorPicker.Interact, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {Size = UDim2.new(1, 0, 1, 0)}):Play()
					TweenService:Create(ColorPicker.Interact, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {Position = UDim2.new(0.5, 0, 0.5, 0)}):Play()
					TweenService:Create(ColorPicker.RGB, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {Position = UDim2.new(0, 17, 0, 70)}):Play()
					TweenService:Create(ColorPicker.HexInput, TweenInfo.new(0.5, Enum.EasingStyle.Exponential), {Position = UDim2.new(0, 17, 0, 90)}):Play()
					TweenService:Create(Display, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundTransparency = 0}):Play()
					TweenService:Create(Main.MainPoint, TweenInfo.new(0.2, Enum.EasingStyle.Exponential), {ImageTransparency = 1}):Play()
					TweenService:Create(Main, TweenInfo.new(0.2, Enum.EasingStyle.Exponential), {ImageTransparency = 1}):Play()
					TweenService:Create(Background, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundTransparency = 1}):Play()
				end

			end)

			UserInputService.InputEnded:Connect(function(input, gameProcessed) if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then 
					mainDragging = false
					sliderDragging = false
				end end)
			Main.MouseButton1Down:Connect(function()
				if opened then
					mainDragging = true 
				end
			end)
			Main.MainPoint.MouseButton1Down:Connect(function()
				if opened then
					mainDragging = true 
				end
			end)
			Slider.MouseButton1Down:Connect(function()
				sliderDragging = true 
			end)
			Slider.SliderPoint.MouseButton1Down:Connect(function()
				sliderDragging = true 
			end)
			local h,s,v = ColorPickerSettings.Color:ToHSV()
			local color = Color3.fromHSV(h,s,v) 
			local hex = string.format("#%02X%02X%02X",color.R*0xFF,color.G*0xFF,color.B*0xFF)
			ColorPicker.HexInput.InputBox.Text = hex
			local function setDisplay()
				--Main
				Main.MainPoint.Position = UDim2.new(s,-Main.MainPoint.AbsoluteSize.X/2,1-v,-Main.MainPoint.AbsoluteSize.Y/2)
				Main.MainPoint.ImageColor3 = Color3.fromHSV(h,s,v)
				Background.BackgroundColor3 = Color3.fromHSV(h,1,1)
				Display.BackgroundColor3 = Color3.fromHSV(h,s,v)
				--Slider 
				local x = h * Slider.AbsoluteSize.X
				Slider.SliderPoint.Position = UDim2.new(0,x-Slider.SliderPoint.AbsoluteSize.X/2,0.5,0)
				Slider.SliderPoint.ImageColor3 = Color3.fromHSV(h,1,1)
				local color = Color3.fromHSV(h,s,v) 
				local r,g,b = math.floor((color.R*255)+0.5),math.floor((color.G*255)+0.5),math.floor((color.B*255)+0.5)
				ColorPicker.RGB.RInput.InputBox.Text = tostring(r)
				ColorPicker.RGB.GInput.InputBox.Text = tostring(g)
				ColorPicker.RGB.BInput.InputBox.Text = tostring(b)
				hex = string.format("#%02X%02X%02X",color.R*0xFF,color.G*0xFF,color.B*0xFF)
				ColorPicker.HexInput.InputBox.Text = hex
			end
			setDisplay()
			ColorPicker.HexInput.InputBox.FocusLost:Connect(function()
				if not pcall(function()
						local r, g, b = string.match(ColorPicker.HexInput.InputBox.Text, "^#?(%w%w)(%w%w)(%w%w)$")
						local rgbColor = Color3.fromRGB(tonumber(r, 16),tonumber(g, 16), tonumber(b, 16))
						h,s,v = rgbColor:ToHSV()
						hex = ColorPicker.HexInput.InputBox.Text
						setDisplay()
						ColorPickerSettings.Color = rgbColor
					end) 
				then 
					ColorPicker.HexInput.InputBox.Text = hex 
				end
				pcall(function()ColorPickerSettings.Callback(Color3.fromHSV(h,s,v))end)
				local r,g,b = math.floor((h*255)+0.5),math.floor((s*255)+0.5),math.floor((v*255)+0.5)
				ColorPickerSettings.Color = Color3.fromRGB(r,g,b)
				SaveConfiguration()
			end)
			--RGB
			local function rgbBoxes(box,toChange)
				local value = tonumber(box.Text) 
				local color = Color3.fromHSV(h,s,v) 
				local oldR,oldG,oldB = math.floor((color.R*255)+0.5),math.floor((color.G*255)+0.5),math.floor((color.B*255)+0.5)
				local save 
				if toChange == "R" then save = oldR;oldR = value elseif toChange == "G" then save = oldG;oldG = value else save = oldB;oldB = value end
				if value then 
					value = math.clamp(value,0,255)
					h,s,v = Color3.fromRGB(oldR,oldG,oldB):ToHSV()

					setDisplay()
				else 
					box.Text = tostring(save)
				end
				local r,g,b = math.floor((h*255)+0.5),math.floor((s*255)+0.5),math.floor((v*255)+0.5)
				ColorPickerSettings.Color = Color3.fromRGB(r,g,b)
				SaveConfiguration()
			end
			ColorPicker.RGB.RInput.InputBox.FocusLost:connect(function()
				rgbBoxes(ColorPicker.RGB.RInput.InputBox,"R")
				pcall(function()ColorPickerSettings.Callback(Color3.fromHSV(h,s,v))end)
			end)
			ColorPicker.RGB.GInput.InputBox.FocusLost:connect(function()
				rgbBoxes(ColorPicker.RGB.GInput.InputBox,"G")
				pcall(function()ColorPickerSettings.Callback(Color3.fromHSV(h,s,v))end)
			end)
			ColorPicker.RGB.BInput.InputBox.FocusLost:connect(function()
				rgbBoxes(ColorPicker.RGB.BInput.InputBox,"B")
				pcall(function()ColorPickerSettings.Callback(Color3.fromHSV(h,s,v))end)
			end)

			RunService.RenderStepped:connect(function()
				if mainDragging then 
					local localX = math.clamp(mouse.X-Main.AbsolutePosition.X,0,Main.AbsoluteSize.X)
					local localY = math.clamp(mouse.Y-Main.AbsolutePosition.Y,0,Main.AbsoluteSize.Y)
					Main.MainPoint.Position = UDim2.new(0,localX-Main.MainPoint.AbsoluteSize.X/2,0,localY-Main.MainPoint.AbsoluteSize.Y/2)
					s = localX / Main.AbsoluteSize.X
					v = 1 - (localY / Main.AbsoluteSize.Y)
					Display.BackgroundColor3 = Color3.fromHSV(h,s,v)
					Main.MainPoint.ImageColor3 = Color3.fromHSV(h,s,v)
					Background.BackgroundColor3 = Color3.fromHSV(h,1,1)
					local color = Color3.fromHSV(h,s,v) 
					local r,g,b = math.floor((color.R*255)+0.5),math.floor((color.G*255)+0.5),math.floor((color.B*255)+0.5)
					ColorPicker.RGB.RInput.InputBox.Text = tostring(r)
					ColorPicker.RGB.GInput.InputBox.Text = tostring(g)
					ColorPicker.RGB.BInput.InputBox.Text = tostring(b)
					ColorPicker.HexInput.InputBox.Text = string.format("#%02X%02X%02X",color.R*0xFF,color.G*0xFF,color.B*0xFF)
					pcall(function()ColorPickerSettings.Callback(Color3.fromHSV(h,s,v))end)
					ColorPickerSettings.Color = Color3.fromRGB(r,g,b)
					SaveConfiguration()
				end
				if sliderDragging then 
					local localX = math.clamp(mouse.X-Slider.AbsolutePosition.X,0,Slider.AbsoluteSize.X)
					h = localX / Slider.AbsoluteSize.X
					Display.BackgroundColor3 = Color3.fromHSV(h,s,v)
					Slider.SliderPoint.Position = UDim2.new(0,localX-Slider.SliderPoint.AbsoluteSize.X/2,0.5,0)
					Slider.SliderPoint.ImageColor3 = Color3.fromHSV(h,1,1)
					Background.BackgroundColor3 = Color3.fromHSV(h,1,1)
					Main.MainPoint.ImageColor3 = Color3.fromHSV(h,s,v)
					local color = Color3.fromHSV(h,s,v) 
					local r,g,b = math.floor((color.R*255)+0.5),math.floor((color.G*255)+0.5),math.floor((color.B*255)+0.5)
					ColorPicker.RGB.RInput.InputBox.Text = tostring(r)
					ColorPicker.RGB.GInput.InputBox.Text = tostring(g)
					ColorPicker.RGB.BInput.InputBox.Text = tostring(b)
					ColorPicker.HexInput.InputBox.Text = string.format("#%02X%02X%02X",color.R*0xFF,color.G*0xFF,color.B*0xFF)
					pcall(function()ColorPickerSettings.Callback(Color3.fromHSV(h,s,v))end)
					ColorPickerSettings.Color = Color3.fromRGB(r,g,b)
					SaveConfiguration()
				end
			end)

			if Settings.ConfigurationSaving then
				if Settings.ConfigurationSaving.Enabled and ColorPickerSettings.Flag then
					RayfieldLibrary.Flags[ColorPickerSettings.Flag] = ColorPickerSettings
				end
			end

			function ColorPickerSettings:Set(RGBColor)
				ColorPickerSettings.Color = RGBColor
				h,s,v = ColorPickerSettings.Color:ToHSV()
				color = Color3.fromHSV(h,s,v)
				setDisplay()
			end

			ColorPicker.MouseEnter:Connect(function()
				TweenService:Create(ColorPicker, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundColor3 = SelectedTheme.ElementBackgroundHover}):Play()
			end)

			ColorPicker.MouseLeave:Connect(function()
				TweenService:Create(ColorPicker, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundColor3 = SelectedTheme.ElementBackground}):Play()
			end)

			Rayfield.Main:GetPropertyChangedSignal('BackgroundColor3'):Connect(function()
				for _, rgbinput in ipairs(ColorPicker.RGB:GetChildren()) do
					if rgbinput:IsA("Frame") then
						rgbinput.BackgroundColor3 = SelectedTheme.InputBackground
						rgbinput.UIStroke.Color = SelectedTheme.InputStroke
					end
				end

				ColorPicker.HexInput.BackgroundColor3 = SelectedTheme.InputBackground
				ColorPicker.HexInput.UIStroke.Color = SelectedTheme.InputStroke
			end)

			return ColorPickerSettings
		end

		-- Section
		function Tab:CreateSection(SectionName)

			local SectionValue = {}

			if SDone then
				local SectionSpace = Elements.Template.SectionSpacing:Clone()
				SectionSpace.Visible = true
				SectionSpace.Parent = TabPage
			end

			local Section = Elements.Template.SectionTitle:Clone()
			Section.Title.Text = SectionName
			Section.Visible = true
			Section.Parent = TabPage

			Section.Title.TextTransparency = 1
			TweenService:Create(Section.Title, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {TextTransparency = 0.4}):Play()

			function SectionValue:Set(NewSection)
				Section.Title.Text = NewSection
			end

			SDone = true

			return SectionValue
		end

		-- Divider
		function Tab:CreateDivider()
			local DividerValue = {}

			local Divider = Elements.Template.Divider:Clone()
			Divider.Visible = true
			Divider.Parent = TabPage

			Divider.Divider.BackgroundTransparency = 1
			TweenService:Create(Divider.Divider, TweenInfo.new(0.5, Enum.EasingStyle.Exponential), {BackgroundTransparency = 0.85}):Play()

			function DividerValue:Set(Value)
				Divider.Visible = Value
			end

			return DividerValue
		end

		-- Label
		function Tab:CreateLabel(LabelText : string, Icon: number, Color : Color3, IgnoreTheme : boolean)
			local LabelValue = {}

			local Label = Elements.Template.Label:Clone()
			Label.Title.Text = LabelText
			Label.Visible = true
			Label.Parent = TabPage

			Label.BackgroundColor3 = Color or SelectedTheme.SecondaryElementBackground
			Label.UIStroke.Color = Color or SelectedTheme.SecondaryElementStroke

			if Icon then
				if typeof(Icon) == 'string' then
					local asset = getIcon(Icon)

					Label.Icon.Image = 'rbxassetid://'..asset.id
					Label.Icon.ImageRectOffset = asset.imageRectOffset
					Label.Icon.ImageRectSize = asset.imageRectSize
				else
					Label.Icon.Image = "rbxassetid://" .. (Icon or 0)
				end
			else
				Label.Icon.Image = "rbxassetid://" .. 0
			end

			if Icon and Label:FindFirstChild('Icon') then
				Label.Title.Position = UDim2.new(0, 45, 0.5, 0)
				Label.Title.Size = UDim2.new(1, -100, 0, 14)

				if Icon then
					if typeof(Icon) == 'string' then
						local asset = getIcon(Icon)

						Label.Icon.Image = 'rbxassetid://'..asset.id
						Label.Icon.ImageRectOffset = asset.imageRectOffset
						Label.Icon.ImageRectSize = asset.imageRectSize
					else
						Label.Icon.Image = "rbxassetid://" .. (Icon or 0)
					end
				else
					Label.Icon.Image = "rbxassetid://" .. 0
				end

				Label.Icon.Visible = true
			end

			Label.Icon.ImageTransparency = 1
			Label.BackgroundTransparency = 1
			Label.UIStroke.Transparency = 1
			Label.Title.TextTransparency = 1

			TweenService:Create(Label, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {BackgroundTransparency = Color and 0.8 or 0}):Play()
			TweenService:Create(Label.UIStroke, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {Transparency = Color and 0.7 or 0}):Play()
			TweenService:Create(Label.Icon, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {ImageTransparency = 0.2}):Play()
			TweenService:Create(Label.Title, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {TextTransparency = Color and 0.2 or 0}):Play()	

			function LabelValue:Set(NewLabel, Icon, Color)
				Label.Title.Text = NewLabel

				if Color then
					Label.BackgroundColor3 = Color or SelectedTheme.SecondaryElementBackground
					Label.UIStroke.Color = Color or SelectedTheme.SecondaryElementStroke
				end

				if Icon and Label:FindFirstChild('Icon') then
					Label.Title.Position = UDim2.new(0, 45, 0.5, 0)
					Label.Title.Size = UDim2.new(1, -100, 0, 14)

					if Icon then
						if typeof(Icon) == 'string' then
							local asset = getIcon(Icon)

							Label.Icon.Image = 'rbxassetid://'..asset.id
							Label.Icon.ImageRectOffset = asset.imageRectOffset
							Label.Icon.ImageRectSize = asset.imageRectSize
						else
							Label.Icon.Image = "rbxassetid://" .. (Icon or 0)
						end
					else
						Label.Icon.Image = "rbxassetid://" .. 0
					end

					Label.Icon.Visible = true
				end
			end

			Rayfield.Main:GetPropertyChangedSignal('BackgroundColor3'):Connect(function()
				Label.BackgroundColor3 = IgnoreTheme and (Color or Label.BackgroundColor3) or SelectedTheme.SecondaryElementBackground
				Label.UIStroke.Color = IgnoreTheme and (Color or Label.BackgroundColor3) or SelectedTheme.SecondaryElementStroke
			end)

			return LabelValue
		end

		-- Paragraph
		function Tab:CreateParagraph(ParagraphSettings)
			local ParagraphValue = {}

			local Paragraph = Elements.Template.Paragraph:Clone()
			Paragraph.Title.Text = ParagraphSettings.Title
			Paragraph.Content.Text = ParagraphSettings.Content
			Paragraph.Visible = true
			Paragraph.Parent = TabPage

			Paragraph.BackgroundTransparency = 1
			Paragraph.UIStroke.Transparency = 1
			Paragraph.Title.TextTransparency = 1
			Paragraph.Content.TextTransparency = 1

			Paragraph.BackgroundColor3 = SelectedTheme.SecondaryElementBackground
			Paragraph.UIStroke.Color = SelectedTheme.SecondaryElementStroke

			TweenService:Create(Paragraph, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {BackgroundTransparency = 0}):Play()
			TweenService:Create(Paragraph.UIStroke, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {Transparency = 0}):Play()
			TweenService:Create(Paragraph.Title, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {TextTransparency = 0}):Play()	
			TweenService:Create(Paragraph.Content, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {TextTransparency = 0}):Play()	

			function ParagraphValue:Set(NewParagraphSettings)
				Paragraph.Title.Text = NewParagraphSettings.Title
				Paragraph.Content.Text = NewParagraphSettings.Content
			end

			Rayfield.Main:GetPropertyChangedSignal('BackgroundColor3'):Connect(function()
				Paragraph.BackgroundColor3 = SelectedTheme.SecondaryElementBackground
				Paragraph.UIStroke.Color = SelectedTheme.SecondaryElementStroke
			end)

			return ParagraphValue
		end

		-- Input
		function Tab:CreateInput(InputSettings)
			local Input = Elements.Template.Input:Clone()
			Input.Name = InputSettings.Name
			Input.Title.Text = InputSettings.Name
			Input.Visible = true
			Input.Parent = TabPage

			Input.BackgroundTransparency = 1
			Input.UIStroke.Transparency = 1
			Input.Title.TextTransparency = 1

			Input.InputFrame.InputBox.Text = InputSettings.CurrentValue or ''

			Input.InputFrame.BackgroundColor3 = SelectedTheme.InputBackground
			Input.InputFrame.UIStroke.Color = SelectedTheme.InputStroke

			TweenService:Create(Input, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {BackgroundTransparency = 0}):Play()
			TweenService:Create(Input.UIStroke, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {Transparency = 0}):Play()
			TweenService:Create(Input.Title, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {TextTransparency = 0}):Play()	

			Input.InputFrame.InputBox.PlaceholderText = InputSettings.PlaceholderText
			Input.InputFrame.Size = UDim2.new(0, Input.InputFrame.InputBox.TextBounds.X + 24, 0, 30)

			Input.InputFrame.InputBox.FocusLost:Connect(function()
				local Success, Response = pcall(function()
					InputSettings.Callback(Input.InputFrame.InputBox.Text)
					InputSettings.CurrentValue = Input.InputFrame.InputBox.Text
				end)

				if not Success then
					TweenService:Create(Input, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundColor3 = Color3.fromRGB(85, 0, 0)}):Play()
					TweenService:Create(Input.UIStroke, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {Transparency = 1}):Play()
					Input.Title.Text = "Callback Error"
					print("Rayfield | "..InputSettings.Name.." Callback Error " ..tostring(Response))
					warn('Check docs.sirius.menu for help with Rayfield specific development.')
					task.wait(0.5)
					Input.Title.Text = InputSettings.Name
					TweenService:Create(Input, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundColor3 = SelectedTheme.ElementBackground}):Play()
					TweenService:Create(Input.UIStroke, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {Transparency = 0}):Play()
				end

				if InputSettings.RemoveTextAfterFocusLost then
					Input.InputFrame.InputBox.Text = ""
				end

				SaveConfiguration()
			end)

			Input.MouseEnter:Connect(function()
				TweenService:Create(Input, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundColor3 = SelectedTheme.ElementBackgroundHover}):Play()
			end)

			Input.MouseLeave:Connect(function()
				TweenService:Create(Input, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundColor3 = SelectedTheme.ElementBackground}):Play()
			end)

			Input.InputFrame.InputBox:GetPropertyChangedSignal("Text"):Connect(function()
				TweenService:Create(Input.InputFrame, TweenInfo.new(0.55, Enum.EasingStyle.Exponential, Enum.EasingDirection.Out), {Size = UDim2.new(0, Input.InputFrame.InputBox.TextBounds.X + 24, 0, 30)}):Play()
			end)

			function InputSettings:Set(text)
				Input.InputFrame.InputBox.Text = text
				SaveConfiguration()
			end

			if Settings.ConfigurationSaving then
				if Settings.ConfigurationSaving.Enabled and InputSettings.Flag then
					RayfieldLibrary.Flags[InputSettings.Flag] = InputSettings
				end
			end

			Rayfield.Main:GetPropertyChangedSignal('BackgroundColor3'):Connect(function()
				Input.InputFrame.BackgroundColor3 = SelectedTheme.InputBackground
				Input.InputFrame.UIStroke.Color = SelectedTheme.InputStroke
			end)

			return InputSettings
		end

		-- Dropdown
		function Tab:CreateDropdown(DropdownSettings)
			local Dropdown = Elements.Template.Dropdown:Clone()
			if string.find(DropdownSettings.Name,"closed") then
				Dropdown.Name = "Dropdown"
			else
				Dropdown.Name = DropdownSettings.Name
			end
			Dropdown.Title.Text = DropdownSettings.Name
			Dropdown.Visible = true
			Dropdown.Parent = TabPage

			Dropdown.List.Visible = false
			if DropdownSettings.CurrentOption then
				if type(DropdownSettings.CurrentOption) == "string" then
					DropdownSettings.CurrentOption = {DropdownSettings.CurrentOption}
				end
				if not DropdownSettings.MultipleOptions and type(DropdownSettings.CurrentOption) == "table" then
					DropdownSettings.CurrentOption = {DropdownSettings.CurrentOption[1]}
				end
			else
				DropdownSettings.CurrentOption = {}
			end

			if DropdownSettings.MultipleOptions then
				if DropdownSettings.CurrentOption and type(DropdownSettings.CurrentOption) == "table" then
					if #DropdownSettings.CurrentOption == 1 then
						Dropdown.Selected.Text = DropdownSettings.CurrentOption[1]
					elseif #DropdownSettings.CurrentOption == 0 then
						Dropdown.Selected.Text = "None"
					else
						Dropdown.Selected.Text = "Various"
					end
				else
					DropdownSettings.CurrentOption = {}
					Dropdown.Selected.Text = "None"
				end
			else
				Dropdown.Selected.Text = DropdownSettings.CurrentOption[1] or "None"
			end

			Dropdown.Toggle.ImageColor3 = SelectedTheme.TextColor
			TweenService:Create(Dropdown, TweenInfo.new(0.4, Enum.EasingStyle.Exponential), {BackgroundColor3 = SelectedTheme.ElementBackground}):Play()

			Dropdown.BackgroundTransparency = 1
			Dropdown.UIStroke.Transparency = 1
			Dropdown.Title.TextTransparency = 1

			Dropdown.Size = UDim2.new(1, -10, 0, 45)

			TweenService:Create(Dropdown, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {BackgroundTransparency = 0}):Play()
			TweenService:Create(Dropdown.UIStroke, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {Transparency = 0}):Play()
			TweenService:Create(Dropdown.Title, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {TextTransparency = 0}):Play()	

			for _, ununusedoption in ipairs(Dropdown.List:GetChildren()) do
				if ununusedoption.ClassName == "Frame" and ununusedoption.Name ~= "Placeholder" then
					ununusedoption:Destroy()
				end
			end

			Dropdown.Toggle.Rotation = 180

			Dropdown.Interact.MouseButton1Click:Connect(function()
				TweenService:Create(Dropdown, TweenInfo.new(0.4, Enum.EasingStyle.Exponential), {BackgroundColor3 = SelectedTheme.ElementBackgroundHover}):Play()
				TweenService:Create(Dropdown.UIStroke, TweenInfo.new(0.4, Enum.EasingStyle.Exponential), {Transparency = 1}):Play()
				task.wait(0.1)
				TweenService:Create(Dropdown, TweenInfo.new(0.4, Enum.EasingStyle.Exponential), {BackgroundColor3 = SelectedTheme.ElementBackground}):Play()
				TweenService:Create(Dropdown.UIStroke, TweenInfo.new(0.4, Enum.EasingStyle.Exponential), {Transparency = 0}):Play()
				if Debounce then return end
				if Dropdown.List.Visible then
					Debounce = true
					TweenService:Create(Dropdown, TweenInfo.new(0.5, Enum.EasingStyle.Exponential), {Size = UDim2.new(1, -10, 0, 45)}):Play()
					for _, DropdownOpt in ipairs(Dropdown.List:GetChildren()) do
						if DropdownOpt.ClassName == "Frame" and DropdownOpt.Name ~= "Placeholder" then
							TweenService:Create(DropdownOpt, TweenInfo.new(0.3, Enum.EasingStyle.Exponential), {BackgroundTransparency = 1}):Play()
							TweenService:Create(DropdownOpt.UIStroke, TweenInfo.new(0.3, Enum.EasingStyle.Exponential), {Transparency = 1}):Play()
							TweenService:Create(DropdownOpt.Title, TweenInfo.new(0.3, Enum.EasingStyle.Exponential), {TextTransparency = 1}):Play()
						end
					end
					TweenService:Create(Dropdown.List, TweenInfo.new(0.3, Enum.EasingStyle.Exponential), {ScrollBarImageTransparency = 1}):Play()
					TweenService:Create(Dropdown.Toggle, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {Rotation = 180}):Play()	
					task.wait(0.35)
					Dropdown.List.Visible = false
					Debounce = false
				else
					TweenService:Create(Dropdown, TweenInfo.new(0.5, Enum.EasingStyle.Exponential), {Size = UDim2.new(1, -10, 0, 180)}):Play()
					Dropdown.List.Visible = true
					TweenService:Create(Dropdown.List, TweenInfo.new(0.3, Enum.EasingStyle.Exponential), {ScrollBarImageTransparency = 0.7}):Play()
					TweenService:Create(Dropdown.Toggle, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {Rotation = 0}):Play()	
					for _, DropdownOpt in ipairs(Dropdown.List:GetChildren()) do
						if DropdownOpt.ClassName == "Frame" and DropdownOpt.Name ~= "Placeholder" then
							if DropdownOpt.Name ~= Dropdown.Selected.Text then
								TweenService:Create(DropdownOpt.UIStroke, TweenInfo.new(0.3, Enum.EasingStyle.Exponential), {Transparency = 0}):Play()
							end
							TweenService:Create(DropdownOpt, TweenInfo.new(0.3, Enum.EasingStyle.Exponential), {BackgroundTransparency = 0}):Play()
							TweenService:Create(DropdownOpt.Title, TweenInfo.new(0.3, Enum.EasingStyle.Exponential), {TextTransparency = 0}):Play()
						end
					end
				end
			end)

			Dropdown.MouseEnter:Connect(function()
				if not Dropdown.List.Visible then
					TweenService:Create(Dropdown, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundColor3 = SelectedTheme.ElementBackgroundHover}):Play()
				end
			end)

			Dropdown.MouseLeave:Connect(function()
				TweenService:Create(Dropdown, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundColor3 = SelectedTheme.ElementBackground}):Play()
			end)

			local function SetDropdownOptions()
				for _, Option in ipairs(DropdownSettings.Options) do
					local DropdownOption = Elements.Template.Dropdown.List.Template:Clone()
					DropdownOption.Name = Option
					DropdownOption.Title.Text = Option
					DropdownOption.Parent = Dropdown.List
					DropdownOption.Visible = true

					DropdownOption.BackgroundTransparency = 1
					DropdownOption.UIStroke.Transparency = 1
					DropdownOption.Title.TextTransparency = 1

					--local Dropdown = Tab:CreateDropdown({
					--	Name = "Dropdown Example",
					--	Options = {"Option 1","Option 2"},
					--	CurrentOption = {"Option 1"},
					--  MultipleOptions = true,
					--	Flag = "Dropdown1",
					--	Callback = function(TableOfOptions)

					--	end,
					--})


					DropdownOption.Interact.ZIndex = 50
					DropdownOption.Interact.MouseButton1Click:Connect(function()
						if not DropdownSettings.MultipleOptions and table.find(DropdownSettings.CurrentOption, Option) then 
							return
						end

						if table.find(DropdownSettings.CurrentOption, Option) then
							table.remove(DropdownSettings.CurrentOption, table.find(DropdownSettings.CurrentOption, Option))
							if DropdownSettings.MultipleOptions then
								if #DropdownSettings.CurrentOption == 1 then
									Dropdown.Selected.Text = DropdownSettings.CurrentOption[1]
								elseif #DropdownSettings.CurrentOption == 0 then
									Dropdown.Selected.Text = "None"
								else
									Dropdown.Selected.Text = "Various"
								end
							else
								Dropdown.Selected.Text = DropdownSettings.CurrentOption[1]
							end
						else
							if not DropdownSettings.MultipleOptions then
								table.clear(DropdownSettings.CurrentOption)
							end
							table.insert(DropdownSettings.CurrentOption, Option)
							if DropdownSettings.MultipleOptions then
								if #DropdownSettings.CurrentOption == 1 then
									Dropdown.Selected.Text = DropdownSettings.CurrentOption[1]
								elseif #DropdownSettings.CurrentOption == 0 then
									Dropdown.Selected.Text = "None"
								else
									Dropdown.Selected.Text = "Various"
								end
							else
								Dropdown.Selected.Text = DropdownSettings.CurrentOption[1]
							end
							TweenService:Create(DropdownOption.UIStroke, TweenInfo.new(0.3, Enum.EasingStyle.Exponential), {Transparency = 1}):Play()
							TweenService:Create(DropdownOption, TweenInfo.new(0.3, Enum.EasingStyle.Exponential), {BackgroundColor3 = SelectedTheme.DropdownSelected}):Play()
							Debounce = true
						end


						local Success, Response = pcall(function()
							DropdownSettings.Callback(DropdownSettings.CurrentOption)
						end)

						if not Success then
							TweenService:Create(Dropdown, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundColor3 = Color3.fromRGB(85, 0, 0)}):Play()
							TweenService:Create(Dropdown.UIStroke, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {Transparency = 1}):Play()
							Dropdown.Title.Text = "Callback Error"
							print("Rayfield | "..DropdownSettings.Name.." Callback Error " ..tostring(Response))
							warn('Check docs.sirius.menu for help with Rayfield specific development.')
							task.wait(0.5)
							Dropdown.Title.Text = DropdownSettings.Name
							TweenService:Create(Dropdown, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundColor3 = SelectedTheme.ElementBackground}):Play()
							TweenService:Create(Dropdown.UIStroke, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {Transparency = 0}):Play()
						end

						for _, droption in ipairs(Dropdown.List:GetChildren()) do
							if droption.ClassName == "Frame" and droption.Name ~= "Placeholder" and not table.find(DropdownSettings.CurrentOption, droption.Name) then
								TweenService:Create(droption, TweenInfo.new(0.3, Enum.EasingStyle.Exponential), {BackgroundColor3 = SelectedTheme.DropdownUnselected}):Play()
							end
						end
						if not DropdownSettings.MultipleOptions then
							task.wait(0.1)
							TweenService:Create(Dropdown, TweenInfo.new(0.5, Enum.EasingStyle.Exponential), {Size = UDim2.new(1, -10, 0, 45)}):Play()
							for _, DropdownOpt in ipairs(Dropdown.List:GetChildren()) do
								if DropdownOpt.ClassName == "Frame" and DropdownOpt.Name ~= "Placeholder" then
									TweenService:Create(DropdownOpt, TweenInfo.new(0.3, Enum.EasingStyle.Exponential), {BackgroundTransparency = 1}):Play()
									TweenService:Create(DropdownOpt.UIStroke, TweenInfo.new(0.3, Enum.EasingStyle.Exponential), {Transparency = 1}):Play()
									TweenService:Create(DropdownOpt.Title, TweenInfo.new(0.3, Enum.EasingStyle.Exponential), {TextTransparency = 1}):Play()
								end
							end
							TweenService:Create(Dropdown.List, TweenInfo.new(0.3, Enum.EasingStyle.Exponential), {ScrollBarImageTransparency = 1}):Play()
							TweenService:Create(Dropdown.Toggle, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {Rotation = 180}):Play()	
							task.wait(0.35)
							Dropdown.List.Visible = false
						end
						Debounce = false
						SaveConfiguration()
					end)

					Rayfield.Main:GetPropertyChangedSignal('BackgroundColor3'):Connect(function()
						DropdownOption.UIStroke.Color = SelectedTheme.ElementStroke
					end)
				end
			end
			SetDropdownOptions()

			for _, droption in ipairs(Dropdown.List:GetChildren()) do
				if droption.ClassName == "Frame" and droption.Name ~= "Placeholder" then
					if not table.find(DropdownSettings.CurrentOption, droption.Name) then
						droption.BackgroundColor3 = SelectedTheme.DropdownUnselected
					else
						droption.BackgroundColor3 = SelectedTheme.DropdownSelected
					end

					Rayfield.Main:GetPropertyChangedSignal('BackgroundColor3'):Connect(function()
						if not table.find(DropdownSettings.CurrentOption, droption.Name) then
							droption.BackgroundColor3 = SelectedTheme.DropdownUnselected
						else
							droption.BackgroundColor3 = SelectedTheme.DropdownSelected
						end
					end)
				end
			end

			function DropdownSettings:Set(NewOption)
				DropdownSettings.CurrentOption = NewOption

				if typeof(DropdownSettings.CurrentOption) == "string" then
					DropdownSettings.CurrentOption = {DropdownSettings.CurrentOption}
				end

				if not DropdownSettings.MultipleOptions then
					DropdownSettings.CurrentOption = {DropdownSettings.CurrentOption[1]}
				end

				if DropdownSettings.MultipleOptions then
					if #DropdownSettings.CurrentOption == 1 then
						Dropdown.Selected.Text = DropdownSettings.CurrentOption[1]
					elseif #DropdownSettings.CurrentOption == 0 then
						Dropdown.Selected.Text = "None"
					else
						Dropdown.Selected.Text = "Various"
					end
				else
					Dropdown.Selected.Text = DropdownSettings.CurrentOption[1]
				end


				local Success, Response = pcall(function()
					DropdownSettings.Callback(NewOption)
				end)
				if not Success then
					TweenService:Create(Dropdown, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundColor3 = Color3.fromRGB(85, 0, 0)}):Play()
					TweenService:Create(Dropdown.UIStroke, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {Transparency = 1}):Play()
					Dropdown.Title.Text = "Callback Error"
					print("Rayfield | "..DropdownSettings.Name.." Callback Error " ..tostring(Response))
					warn('Check docs.sirius.menu for help with Rayfield specific development.')
					task.wait(0.5)
					Dropdown.Title.Text = DropdownSettings.Name
					TweenService:Create(Dropdown, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundColor3 = SelectedTheme.ElementBackground}):Play()
					TweenService:Create(Dropdown.UIStroke, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {Transparency = 0}):Play()
				end

				for _, droption in ipairs(Dropdown.List:GetChildren()) do
					if droption.ClassName == "Frame" and droption.Name ~= "Placeholder" then
						if not table.find(DropdownSettings.CurrentOption, droption.Name) then
							droption.BackgroundColor3 = SelectedTheme.DropdownUnselected
						else
							droption.BackgroundColor3 = SelectedTheme.DropdownSelected
						end
					end
				end
				--SaveConfiguration()
			end

			function DropdownSettings:Refresh(optionsTable: table) -- updates a dropdown with new options from optionsTable
				DropdownSettings.Options = optionsTable
				for _, option in Dropdown.List:GetChildren() do
					if option.ClassName == "Frame" and option.Name ~= "Placeholder" then
						option:Destroy()
					end
				end
				SetDropdownOptions()
			end

			if Settings.ConfigurationSaving then
				if Settings.ConfigurationSaving.Enabled and DropdownSettings.Flag then
					RayfieldLibrary.Flags[DropdownSettings.Flag] = DropdownSettings
				end
			end

			Rayfield.Main:GetPropertyChangedSignal('BackgroundColor3'):Connect(function()
				Dropdown.Toggle.ImageColor3 = SelectedTheme.TextColor
				TweenService:Create(Dropdown, TweenInfo.new(0.4, Enum.EasingStyle.Exponential), {BackgroundColor3 = SelectedTheme.ElementBackground}):Play()
			end)

			return DropdownSettings
		end

		-- Keybind
		function Tab:CreateKeybind(KeybindSettings)
			local CheckingForKey = false
			local Keybind = Elements.Template.Keybind:Clone()
			Keybind.Name = KeybindSettings.Name
			Keybind.Title.Text = KeybindSettings.Name
			Keybind.Visible = true
			Keybind.Parent = TabPage

			Keybind.BackgroundTransparency = 1
			Keybind.UIStroke.Transparency = 1
			Keybind.Title.TextTransparency = 1

			Keybind.KeybindFrame.BackgroundColor3 = SelectedTheme.InputBackground
			Keybind.KeybindFrame.UIStroke.Color = SelectedTheme.InputStroke

			TweenService:Create(Keybind, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {BackgroundTransparency = 0}):Play()
			TweenService:Create(Keybind.UIStroke, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {Transparency = 0}):Play()
			TweenService:Create(Keybind.Title, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {TextTransparency = 0}):Play()	

			Keybind.KeybindFrame.KeybindBox.Text = KeybindSettings.CurrentKeybind
			Keybind.KeybindFrame.Size = UDim2.new(0, Keybind.KeybindFrame.KeybindBox.TextBounds.X + 24, 0, 30)

			Keybind.KeybindFrame.KeybindBox.Focused:Connect(function()
				CheckingForKey = true
				Keybind.KeybindFrame.KeybindBox.Text = ""
			end)
			Keybind.KeybindFrame.KeybindBox.FocusLost:Connect(function()
				CheckingForKey = false
				if Keybind.KeybindFrame.KeybindBox.Text == nil or "" then
					Keybind.KeybindFrame.KeybindBox.Text = KeybindSettings.CurrentKeybind
					SaveConfiguration()
				end
			end)

			Keybind.MouseEnter:Connect(function()
				TweenService:Create(Keybind, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundColor3 = SelectedTheme.ElementBackgroundHover}):Play()
			end)

			Keybind.MouseLeave:Connect(function()
				TweenService:Create(Keybind, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundColor3 = SelectedTheme.ElementBackground}):Play()
			end)

			UserInputService.InputBegan:Connect(function(input, processed)

				if CheckingForKey then
					if input.KeyCode ~= Enum.KeyCode.Unknown and input.KeyCode ~= Enum.KeyCode.K then
						local SplitMessage = string.split(tostring(input.KeyCode), ".")
						local NewKeyNoEnum = SplitMessage[3]
						Keybind.KeybindFrame.KeybindBox.Text = tostring(NewKeyNoEnum)
						KeybindSettings.CurrentKeybind = tostring(NewKeyNoEnum)
						Keybind.KeybindFrame.KeybindBox:ReleaseFocus()
						SaveConfiguration()
					end
				elseif KeybindSettings.CurrentKeybind ~= nil and (input.KeyCode == Enum.KeyCode[KeybindSettings.CurrentKeybind] and not processed) then -- Test
					local Held = true
					local Connection
					Connection = input.Changed:Connect(function(prop)
						if prop == "UserInputState" then
							Connection:Disconnect()
							Held = false
						end
					end)

					if not KeybindSettings.HoldToInteract then
						local Success, Response = pcall(KeybindSettings.Callback)
						if not Success then
							TweenService:Create(Keybind, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundColor3 = Color3.fromRGB(85, 0, 0)}):Play()
							TweenService:Create(Keybind.UIStroke, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {Transparency = 1}):Play()
							Keybind.Title.Text = "Callback Error"
							print("Rayfield | "..KeybindSettings.Name.." Callback Error " ..tostring(Response))
							warn('Check docs.sirius.menu for help with Rayfield specific development.')
							task.wait(0.5)
							Keybind.Title.Text = KeybindSettings.Name
							TweenService:Create(Keybind, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundColor3 = SelectedTheme.ElementBackground}):Play()
							TweenService:Create(Keybind.UIStroke, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {Transparency = 0}):Play()
						end
					else
						task.wait(0.25)
						if Held then
							local Loop; Loop = RunService.Stepped:Connect(function()
								if not Held then
									KeybindSettings.Callback(false) -- maybe pcall this
									Loop:Disconnect()
								else
									KeybindSettings.Callback(true) -- maybe pcall this
								end
							end)
						end
					end
				end
			end)

			Keybind.KeybindFrame.KeybindBox:GetPropertyChangedSignal("Text"):Connect(function()
				TweenService:Create(Keybind.KeybindFrame, TweenInfo.new(0.55, Enum.EasingStyle.Exponential, Enum.EasingDirection.Out), {Size = UDim2.new(0, Keybind.KeybindFrame.KeybindBox.TextBounds.X + 24, 0, 30)}):Play()
			end)

			function KeybindSettings:Set(NewKeybind)
				Keybind.KeybindFrame.KeybindBox.Text = tostring(NewKeybind)
				KeybindSettings.CurrentKeybind = tostring(NewKeybind)
				Keybind.KeybindFrame.KeybindBox:ReleaseFocus()
				SaveConfiguration()
			end

			if Settings.ConfigurationSaving then
				if Settings.ConfigurationSaving.Enabled and KeybindSettings.Flag then
					RayfieldLibrary.Flags[KeybindSettings.Flag] = KeybindSettings
				end
			end

			Rayfield.Main:GetPropertyChangedSignal('BackgroundColor3'):Connect(function()
				Keybind.KeybindFrame.BackgroundColor3 = SelectedTheme.InputBackground
				Keybind.KeybindFrame.UIStroke.Color = SelectedTheme.InputStroke
			end)

			return KeybindSettings
		end

		-- Toggle
		function Tab:CreateToggle(ToggleSettings)
			local ToggleValue = {}

			local Toggle = Elements.Template.Toggle:Clone()
			Toggle.Name = ToggleSettings.Name
			Toggle.Title.Text = ToggleSettings.Name
			Toggle.Visible = true
			Toggle.Parent = TabPage

			Toggle.BackgroundTransparency = 1
			Toggle.UIStroke.Transparency = 1
			Toggle.Title.TextTransparency = 1
			Toggle.Switch.BackgroundColor3 = SelectedTheme.ToggleBackground

			if SelectedTheme ~= RayfieldLibrary.Theme.Default then
				Toggle.Switch.Shadow.Visible = false
			end

			TweenService:Create(Toggle, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {BackgroundTransparency = 0}):Play()
			TweenService:Create(Toggle.UIStroke, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {Transparency = 0}):Play()
			TweenService:Create(Toggle.Title, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {TextTransparency = 0}):Play()	

			if ToggleSettings.CurrentValue == true then
				Toggle.Switch.Indicator.Position = UDim2.new(1, -20, 0.5, 0)
				Toggle.Switch.Indicator.UIStroke.Color = SelectedTheme.ToggleEnabledStroke
				Toggle.Switch.Indicator.BackgroundColor3 = SelectedTheme.ToggleEnabled
				Toggle.Switch.UIStroke.Color = SelectedTheme.ToggleEnabledOuterStroke
			else
				Toggle.Switch.Indicator.Position = UDim2.new(1, -40, 0.5, 0)
				Toggle.Switch.Indicator.UIStroke.Color = SelectedTheme.ToggleDisabledStroke
				Toggle.Switch.Indicator.BackgroundColor3 = SelectedTheme.ToggleDisabled
				Toggle.Switch.UIStroke.Color = SelectedTheme.ToggleDisabledOuterStroke
			end

			Toggle.MouseEnter:Connect(function()
				TweenService:Create(Toggle, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundColor3 = SelectedTheme.ElementBackgroundHover}):Play()
			end)

			Toggle.MouseLeave:Connect(function()
				TweenService:Create(Toggle, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundColor3 = SelectedTheme.ElementBackground}):Play()
			end)

			Toggle.Interact.MouseButton1Click:Connect(function()
				if ToggleSettings.CurrentValue == true then
					ToggleSettings.CurrentValue = false
					TweenService:Create(Toggle, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundColor3 = SelectedTheme.ElementBackgroundHover}):Play()
					TweenService:Create(Toggle.UIStroke, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {Transparency = 1}):Play()
					TweenService:Create(Toggle.Switch.Indicator, TweenInfo.new(0.45, Enum.EasingStyle.Quart, Enum.EasingDirection.Out), {Position = UDim2.new(1, -40, 0.5, 0)}):Play()
					TweenService:Create(Toggle.Switch.Indicator.UIStroke, TweenInfo.new(0.55, Enum.EasingStyle.Exponential, Enum.EasingDirection.Out), {Color = SelectedTheme.ToggleDisabledStroke}):Play()
					TweenService:Create(Toggle.Switch.Indicator, TweenInfo.new(0.8, Enum.EasingStyle.Exponential, Enum.EasingDirection.Out), {BackgroundColor3 = SelectedTheme.ToggleDisabled}):Play()
					TweenService:Create(Toggle.Switch.UIStroke, TweenInfo.new(0.55, Enum.EasingStyle.Exponential, Enum.EasingDirection.Out), {Color = SelectedTheme.ToggleDisabledOuterStroke}):Play()
					TweenService:Create(Toggle, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundColor3 = SelectedTheme.ElementBackground}):Play()
					TweenService:Create(Toggle.UIStroke, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {Transparency = 0}):Play()	
				else
					ToggleSettings.CurrentValue = true
					TweenService:Create(Toggle, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundColor3 = SelectedTheme.ElementBackgroundHover}):Play()
					TweenService:Create(Toggle.UIStroke, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {Transparency = 1}):Play()
					TweenService:Create(Toggle.Switch.Indicator, TweenInfo.new(0.5, Enum.EasingStyle.Quart, Enum.EasingDirection.Out), {Position = UDim2.new(1, -20, 0.5, 0)}):Play()
					TweenService:Create(Toggle.Switch.Indicator.UIStroke, TweenInfo.new(0.55, Enum.EasingStyle.Exponential, Enum.EasingDirection.Out), {Color = SelectedTheme.ToggleEnabledStroke}):Play()
					TweenService:Create(Toggle.Switch.Indicator, TweenInfo.new(0.8, Enum.EasingStyle.Exponential, Enum.EasingDirection.Out), {BackgroundColor3 = SelectedTheme.ToggleEnabled}):Play()
					TweenService:Create(Toggle.Switch.UIStroke, TweenInfo.new(0.55, Enum.EasingStyle.Exponential, Enum.EasingDirection.Out), {Color = SelectedTheme.ToggleEnabledOuterStroke}):Play()
					TweenService:Create(Toggle, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundColor3 = SelectedTheme.ElementBackground}):Play()
					TweenService:Create(Toggle.UIStroke, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {Transparency = 0}):Play()		
				end

				local Success, Response = pcall(function()
					ToggleSettings.Callback(ToggleSettings.CurrentValue)
				end)

				if not Success then
					TweenService:Create(Toggle, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundColor3 = Color3.fromRGB(85, 0, 0)}):Play()
					TweenService:Create(Toggle.UIStroke, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {Transparency = 1}):Play()
					Toggle.Title.Text = "Callback Error"
					print("Rayfield | "..ToggleSettings.Name.." Callback Error " ..tostring(Response))
					warn('Check docs.sirius.menu for help with Rayfield specific development.')
					task.wait(0.5)
					Toggle.Title.Text = ToggleSettings.Name
					TweenService:Create(Toggle, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundColor3 = SelectedTheme.ElementBackground}):Play()
					TweenService:Create(Toggle.UIStroke, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {Transparency = 0}):Play()
				end

				SaveConfiguration()
			end)

			function ToggleSettings:Set(NewToggleValue)
				if NewToggleValue == true then
					ToggleSettings.CurrentValue = true
					TweenService:Create(Toggle, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundColor3 = SelectedTheme.ElementBackgroundHover}):Play()
					TweenService:Create(Toggle.UIStroke, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {Transparency = 1}):Play()
					TweenService:Create(Toggle.Switch.Indicator, TweenInfo.new(0.5, Enum.EasingStyle.Quart, Enum.EasingDirection.Out), {Position = UDim2.new(1, -20, 0.5, 0)}):Play()
					TweenService:Create(Toggle.Switch.Indicator, TweenInfo.new(0.4, Enum.EasingStyle.Quart, Enum.EasingDirection.Out), {Size = UDim2.new(0,12,0,12)}):Play()
					TweenService:Create(Toggle.Switch.Indicator.UIStroke, TweenInfo.new(0.55, Enum.EasingStyle.Exponential, Enum.EasingDirection.Out), {Color = SelectedTheme.ToggleEnabledStroke}):Play()
					TweenService:Create(Toggle.Switch.Indicator, TweenInfo.new(0.8, Enum.EasingStyle.Exponential, Enum.EasingDirection.Out), {BackgroundColor3 = SelectedTheme.ToggleEnabled}):Play()
					TweenService:Create(Toggle.Switch.UIStroke, TweenInfo.new(0.55, Enum.EasingStyle.Exponential, Enum.EasingDirection.Out), {Color = SelectedTheme.ToggleEnabledOuterStroke}):Play()
					TweenService:Create(Toggle.Switch.Indicator, TweenInfo.new(0.45, Enum.EasingStyle.Quart, Enum.EasingDirection.Out), {Size = UDim2.new(0,17,0,17)}):Play()	
					TweenService:Create(Toggle, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundColor3 = SelectedTheme.ElementBackground}):Play()
					TweenService:Create(Toggle.UIStroke, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {Transparency = 0}):Play()	
				else
					ToggleSettings.CurrentValue = false
					TweenService:Create(Toggle, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundColor3 = SelectedTheme.ElementBackgroundHover}):Play()
					TweenService:Create(Toggle.UIStroke, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {Transparency = 1}):Play()
					TweenService:Create(Toggle.Switch.Indicator, TweenInfo.new(0.45, Enum.EasingStyle.Quart, Enum.EasingDirection.Out), {Position = UDim2.new(1, -40, 0.5, 0)}):Play()
					TweenService:Create(Toggle.Switch.Indicator, TweenInfo.new(0.4, Enum.EasingStyle.Quart, Enum.EasingDirection.Out), {Size = UDim2.new(0,12,0,12)}):Play()
					TweenService:Create(Toggle.Switch.Indicator.UIStroke, TweenInfo.new(0.55, Enum.EasingStyle.Exponential, Enum.EasingDirection.Out), {Color = SelectedTheme.ToggleDisabledStroke}):Play()
					TweenService:Create(Toggle.Switch.Indicator, TweenInfo.new(0.8, Enum.EasingStyle.Exponential, Enum.EasingDirection.Out), {BackgroundColor3 = SelectedTheme.ToggleDisabled}):Play()
					TweenService:Create(Toggle.Switch.UIStroke, TweenInfo.new(0.55, Enum.EasingStyle.Exponential, Enum.EasingDirection.Out), {Color = SelectedTheme.ToggleDisabledOuterStroke}):Play()
					TweenService:Create(Toggle.Switch.Indicator, TweenInfo.new(0.4, Enum.EasingStyle.Quart, Enum.EasingDirection.Out), {Size = UDim2.new(0,17,0,17)}):Play()
					TweenService:Create(Toggle, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundColor3 = SelectedTheme.ElementBackground}):Play()
					TweenService:Create(Toggle.UIStroke, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {Transparency = 0}):Play()	
				end

				local Success, Response = pcall(function()
					ToggleSettings.Callback(ToggleSettings.CurrentValue)
				end)

				if not Success then
					TweenService:Create(Toggle, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundColor3 = Color3.fromRGB(85, 0, 0)}):Play()
					TweenService:Create(Toggle.UIStroke, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {Transparency = 1}):Play()
					Toggle.Title.Text = "Callback Error"
					print("Rayfield | "..ToggleSettings.Name.." Callback Error " ..tostring(Response))
					warn('Check docs.sirius.menu for help with Rayfield specific development.')
					task.wait(0.5)
					Toggle.Title.Text = ToggleSettings.Name
					TweenService:Create(Toggle, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundColor3 = SelectedTheme.ElementBackground}):Play()
					TweenService:Create(Toggle.UIStroke, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {Transparency = 0}):Play()
				end

				SaveConfiguration()
			end

			if Settings.ConfigurationSaving then
				if Settings.ConfigurationSaving.Enabled and ToggleSettings.Flag then
					RayfieldLibrary.Flags[ToggleSettings.Flag] = ToggleSettings
				end
			end

			Rayfield.Main:GetPropertyChangedSignal('BackgroundColor3'):Connect(function()
				Toggle.Switch.BackgroundColor3 = SelectedTheme.ToggleBackground

				if SelectedTheme ~= RayfieldLibrary.Theme.Default then
					Toggle.Switch.Shadow.Visible = false
				end

				task.wait()

				if not ToggleSettings.CurrentValue then
					Toggle.Switch.Indicator.UIStroke.Color = SelectedTheme.ToggleDisabledStroke
					Toggle.Switch.Indicator.BackgroundColor3 = SelectedTheme.ToggleDisabled
					Toggle.Switch.UIStroke.Color = SelectedTheme.ToggleDisabledOuterStroke
				else
					Toggle.Switch.Indicator.UIStroke.Color = SelectedTheme.ToggleEnabledStroke
					Toggle.Switch.Indicator.BackgroundColor3 = SelectedTheme.ToggleEnabled
					Toggle.Switch.UIStroke.Color = SelectedTheme.ToggleEnabledOuterStroke
				end
			end)

			return ToggleSettings
		end

		-- Slider
		function Tab:CreateSlider(SliderSettings)
			local SLDragging = false
			local Slider = Elements.Template.Slider:Clone()
			Slider.Name = SliderSettings.Name
			Slider.Title.Text = SliderSettings.Name
			Slider.Visible = true
			Slider.Parent = TabPage

			Slider.BackgroundTransparency = 1
			Slider.UIStroke.Transparency = 1
			Slider.Title.TextTransparency = 1

			if SelectedTheme ~= RayfieldLibrary.Theme.Default then
				Slider.Main.Shadow.Visible = false
			end

			Slider.Main.BackgroundColor3 = SelectedTheme.SliderBackground
			Slider.Main.UIStroke.Color = SelectedTheme.SliderStroke
			Slider.Main.Progress.UIStroke.Color = SelectedTheme.SliderStroke
			Slider.Main.Progress.BackgroundColor3 = SelectedTheme.SliderProgress

			TweenService:Create(Slider, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {BackgroundTransparency = 0}):Play()
			TweenService:Create(Slider.UIStroke, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {Transparency = 0}):Play()
			TweenService:Create(Slider.Title, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {TextTransparency = 0}):Play()	

			Slider.Main.Progress.Size =	UDim2.new(0, Slider.Main.AbsoluteSize.X * ((SliderSettings.CurrentValue + SliderSettings.Range[1]) / (SliderSettings.Range[2] - SliderSettings.Range[1])) > 5 and Slider.Main.AbsoluteSize.X * (SliderSettings.CurrentValue / (SliderSettings.Range[2] - SliderSettings.Range[1])) or 5, 1, 0)

			if not SliderSettings.Suffix then
				Slider.Main.Information.Text = tostring(SliderSettings.CurrentValue)
			else
				Slider.Main.Information.Text = tostring(SliderSettings.CurrentValue) .. " " .. SliderSettings.Suffix
			end

			Slider.MouseEnter:Connect(function()
				TweenService:Create(Slider, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundColor3 = SelectedTheme.ElementBackgroundHover}):Play()
			end)

			Slider.MouseLeave:Connect(function()
				TweenService:Create(Slider, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundColor3 = SelectedTheme.ElementBackground}):Play()
			end)

			Slider.Main.Interact.InputBegan:Connect(function(Input)
				if Input.UserInputType == Enum.UserInputType.MouseButton1 or Input.UserInputType == Enum.UserInputType.Touch then 
					TweenService:Create(Slider.Main.UIStroke, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {Transparency = 1}):Play()
					TweenService:Create(Slider.Main.Progress.UIStroke, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {Transparency = 1}):Play()
					SLDragging = true 
				end 
			end)

			Slider.Main.Interact.InputEnded:Connect(function(Input) 
				if Input.UserInputType == Enum.UserInputType.MouseButton1 or Input.UserInputType == Enum.UserInputType.Touch then 
					TweenService:Create(Slider.Main.UIStroke, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {Transparency = 0.4}):Play()
					TweenService:Create(Slider.Main.Progress.UIStroke, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {Transparency = 0.3}):Play()
					SLDragging = false 
				end 
			end)

			Slider.Main.Interact.MouseButton1Down:Connect(function(X)
				local Current = Slider.Main.Progress.AbsolutePosition.X + Slider.Main.Progress.AbsoluteSize.X
				local Start = Current
				local Location = X
				local Loop; Loop = RunService.Stepped:Connect(function()
					if SLDragging then
						Location = UserInputService:GetMouseLocation().X
						Current = Current + 0.025 * (Location - Start)

						if Location < Slider.Main.AbsolutePosition.X then
							Location = Slider.Main.AbsolutePosition.X
						elseif Location > Slider.Main.AbsolutePosition.X + Slider.Main.AbsoluteSize.X then
							Location = Slider.Main.AbsolutePosition.X + Slider.Main.AbsoluteSize.X
						end

						if Current < Slider.Main.AbsolutePosition.X + 5 then
							Current = Slider.Main.AbsolutePosition.X + 5
						elseif Current > Slider.Main.AbsolutePosition.X + Slider.Main.AbsoluteSize.X then
							Current = Slider.Main.AbsolutePosition.X + Slider.Main.AbsoluteSize.X
						end

						if Current <= Location and (Location - Start) < 0 then
							Start = Location
						elseif Current >= Location and (Location - Start) > 0 then
							Start = Location
						end
						TweenService:Create(Slider.Main.Progress, TweenInfo.new(0.45, Enum.EasingStyle.Exponential, Enum.EasingDirection.Out), {Size = UDim2.new(0, Current - Slider.Main.AbsolutePosition.X, 1, 0)}):Play()
						local NewValue = SliderSettings.Range[1] + (Location - Slider.Main.AbsolutePosition.X) / Slider.Main.AbsoluteSize.X * (SliderSettings.Range[2] - SliderSettings.Range[1])

						NewValue = math.floor(NewValue / SliderSettings.Increment + 0.5) * (SliderSettings.Increment * 10000000) / 10000000
						NewValue = math.clamp(NewValue, SliderSettings.Range[1], SliderSettings.Range[2])

						if not SliderSettings.Suffix then
							Slider.Main.Information.Text = tostring(NewValue)
						else
							Slider.Main.Information.Text = tostring(NewValue) .. " " .. SliderSettings.Suffix
						end

						if SliderSettings.CurrentValue ~= NewValue then
							local Success, Response = pcall(function()
								SliderSettings.Callback(NewValue)
							end)
							if not Success then
								TweenService:Create(Slider, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundColor3 = Color3.fromRGB(85, 0, 0)}):Play()
								TweenService:Create(Slider.UIStroke, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {Transparency = 1}):Play()
								Slider.Title.Text = "Callback Error"
								print("Rayfield | "..SliderSettings.Name.." Callback Error " ..tostring(Response))
								warn('Check docs.sirius.menu for help with Rayfield specific development.')
								task.wait(0.5)
								Slider.Title.Text = SliderSettings.Name
								TweenService:Create(Slider, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundColor3 = SelectedTheme.ElementBackground}):Play()
								TweenService:Create(Slider.UIStroke, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {Transparency = 0}):Play()
							end

							SliderSettings.CurrentValue = NewValue
							SaveConfiguration()
						end
					else
						TweenService:Create(Slider.Main.Progress, TweenInfo.new(0.3, Enum.EasingStyle.Exponential, Enum.EasingDirection.Out), {Size = UDim2.new(0, Location - Slider.Main.AbsolutePosition.X > 5 and Location - Slider.Main.AbsolutePosition.X or 5, 1, 0)}):Play()
						Loop:Disconnect()
					end
				end)
			end)

			function SliderSettings:Set(NewVal)
				local NewVal = math.clamp(NewVal, SliderSettings.Range[1], SliderSettings.Range[2])

				TweenService:Create(Slider.Main.Progress, TweenInfo.new(0.45, Enum.EasingStyle.Exponential, Enum.EasingDirection.Out), {Size = UDim2.new(0, Slider.Main.AbsoluteSize.X * ((NewVal + SliderSettings.Range[1]) / (SliderSettings.Range[2] - SliderSettings.Range[1])) > 5 and Slider.Main.AbsoluteSize.X * (NewVal / (SliderSettings.Range[2] - SliderSettings.Range[1])) or 5, 1, 0)}):Play()
				Slider.Main.Information.Text = tostring(NewVal) .. " " .. (SliderSettings.Suffix or "")

				local Success, Response = pcall(function()
					SliderSettings.Callback(NewVal)
				end)

				if not Success then
					TweenService:Create(Slider, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundColor3 = Color3.fromRGB(85, 0, 0)}):Play()
					TweenService:Create(Slider.UIStroke, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {Transparency = 1}):Play()
					Slider.Title.Text = "Callback Error"
					print("Rayfield | "..SliderSettings.Name.." Callback Error " ..tostring(Response))
					warn('Check docs.sirius.menu for help with Rayfield specific development.')
					task.wait(0.5)
					Slider.Title.Text = SliderSettings.Name
					TweenService:Create(Slider, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundColor3 = SelectedTheme.ElementBackground}):Play()
					TweenService:Create(Slider.UIStroke, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {Transparency = 0}):Play()
				end

				SliderSettings.CurrentValue = NewVal
				SaveConfiguration()
			end

			if Settings.ConfigurationSaving then
				if Settings.ConfigurationSaving.Enabled and SliderSettings.Flag then
					RayfieldLibrary.Flags[SliderSettings.Flag] = SliderSettings
				end
			end

			Rayfield.Main:GetPropertyChangedSignal('BackgroundColor3'):Connect(function()
				if SelectedTheme ~= RayfieldLibrary.Theme.Default then
					Slider.Main.Shadow.Visible = false
				end

				Slider.Main.BackgroundColor3 = SelectedTheme.SliderBackground
				Slider.Main.UIStroke.Color = SelectedTheme.SliderStroke
				Slider.Main.Progress.UIStroke.Color = SelectedTheme.SliderStroke
				Slider.Main.Progress.BackgroundColor3 = SelectedTheme.SliderProgress
			end)

			return SliderSettings
		end

		Rayfield.Main:GetPropertyChangedSignal('BackgroundColor3'):Connect(function()
			TabButton.UIStroke.Color = SelectedTheme.TabStroke

			if Elements.UIPageLayout.CurrentPage == TabPage then
				TabButton.BackgroundColor3 = SelectedTheme.TabBackgroundSelected
				TabButton.Image.ImageColor3 = SelectedTheme.SelectedTabTextColor
				TabButton.Title.TextColor3 = SelectedTheme.SelectedTabTextColor
			else
				TabButton.BackgroundColor3 = SelectedTheme.TabBackground
				TabButton.Image.ImageColor3 = SelectedTheme.TabTextColor
				TabButton.Title.TextColor3 = SelectedTheme.TabTextColor
			end
		end)

		return Tab
	end

	Elements.Visible = true


	task.wait(1.1)
	TweenService:Create(Main, TweenInfo.new(0.7, Enum.EasingStyle.Exponential, Enum.EasingDirection.InOut), {Size = UDim2.new(0, 390, 0, 90)}):Play()
	task.wait(0.3)
	TweenService:Create(LoadingFrame.Title, TweenInfo.new(0.2, Enum.EasingStyle.Exponential), {TextTransparency = 1}):Play()
	TweenService:Create(LoadingFrame.Subtitle, TweenInfo.new(0.2, Enum.EasingStyle.Exponential), {TextTransparency = 1}):Play()
	TweenService:Create(LoadingFrame.Version, TweenInfo.new(0.2, Enum.EasingStyle.Exponential), {TextTransparency = 1}):Play()
	task.wait(0.1)
	TweenService:Create(Main, TweenInfo.new(0.6, Enum.EasingStyle.Exponential, Enum.EasingDirection.Out), {Size = useMobileSizing and UDim2.new(0, 500, 0, 275) or UDim2.new(0, 500, 0, 475)}):Play()
	TweenService:Create(Main.Shadow.Image, TweenInfo.new(0.5, Enum.EasingStyle.Exponential), {ImageTransparency = 0.6}):Play()

	Topbar.BackgroundTransparency = 1
	Topbar.Divider.Size = UDim2.new(0, 0, 0, 1)
	Topbar.Divider.BackgroundColor3 = SelectedTheme.ElementStroke
	Topbar.CornerRepair.BackgroundTransparency = 1
	Topbar.Title.TextTransparency = 1
	Topbar.Search.ImageTransparency = 1
	Topbar.ChangeSize.ImageTransparency = 1
	Topbar.Hide.ImageTransparency = 1


	task.wait(0.5)
	Topbar.Visible = true
	TweenService:Create(Topbar, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {BackgroundTransparency = 0}):Play()
	TweenService:Create(Topbar.CornerRepair, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {BackgroundTransparency = 0}):Play()
	task.wait(0.1)
	TweenService:Create(Topbar.Divider, TweenInfo.new(1, Enum.EasingStyle.Exponential), {Size = UDim2.new(1, 0, 0, 1)}):Play()
	TweenService:Create(Topbar.Title, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {TextTransparency = 0}):Play()
	task.wait(0.05)
	TweenService:Create(Topbar.Search, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {ImageTransparency = 0.8}):Play()
	task.wait(0.05)
	TweenService:Create(Topbar.ChangeSize, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {ImageTransparency = 0.8}):Play()
	task.wait(0.05)
	TweenService:Create(Topbar.Hide, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {ImageTransparency = 0.8}):Play()
	task.wait(0.3)

	if dragBar then
		TweenService:Create(dragBarCosmetic, TweenInfo.new(0.6, Enum.EasingStyle.Exponential), {BackgroundTransparency = 0.7}):Play()
	end

	function Window.ModifyTheme(NewTheme)
		local success = pcall(ChangeTheme, NewTheme)
		if not success then
			RayfieldLibrary:Notify({Title = 'Unable to Change Theme', Content = 'We are unable find a theme on file.', Image = 4400704299})
		else
			RayfieldLibrary:Notify({Title = 'Theme Changed', Content = 'Successfully changed theme to '..(typeof(NewTheme) == 'string' and NewTheme or 'Custom Theme')..'.', Image = 4483362748})
		end
	end

	return Window
end

local function setVisibility(visibility: boolean, notify: boolean?)
	if Debounce then return end
	if visibility then
		Hidden = false
		Unhide()
	else
		Hidden = true
		Hide(notify)
	end
end

workspace:SetAttribute("Radiant",true)
workspace:GetAttributeChangedSignal("Radiant"):Connect(function()
    local shown = workspace:GetAttribute("Radiant")
    if shown then
        setVisibility(true,false)
        else
        setVisibility(false,false)
    end
end)

function RayfieldLibrary:SetVisibility(visibility: boolean)
	setVisibility(visibility, false)
end

function RayfieldLibrary:IsVisible(): boolean
	return not Hidden
end

function RayfieldLibrary:Destroy()
	hideHotkeyConnection:Disconnect()
	Rayfield:Destroy()
end

Topbar.ChangeSize.MouseButton1Click:Connect(function()
	if Debounce then return end
	if Minimised then
		Minimised = false
		Maximise()
	else
		Minimised = true
		Minimise()
	end
end)

Main.Search.Input:GetPropertyChangedSignal('Text'):Connect(function()
	if #Main.Search.Input.Text > 0 then
		if not Elements.UIPageLayout.CurrentPage:FindFirstChild('SearchTitle-fsefsefesfsefesfesfThanks') then 
			local searchTitle = Elements.Template.SectionTitle:Clone()
			searchTitle.Parent = Elements.UIPageLayout.CurrentPage
			searchTitle.Name = 'SearchTitle-fsefsefesfsefesfesfThanks'
			searchTitle.LayoutOrder = -100
			searchTitle.Title.Text = "Results from '"..Elements.UIPageLayout.CurrentPage.Name.."'"
			searchTitle.Visible = true
		end
	else
		local searchTitle = Elements.UIPageLayout.CurrentPage:FindFirstChild('SearchTitle-fsefsefesfsefesfesfThanks')

		if searchTitle then
			searchTitle:Destroy()
		end
	end

	for _, element in ipairs(Elements.UIPageLayout.CurrentPage:GetChildren()) do
		if element.ClassName ~= 'UIListLayout' and element.Name ~= 'Placeholder' and element.Name ~= 'SearchTitle-fsefsefesfsefesfesfThanks' then
			if element.Name == 'SectionTitle' then
				if #Main.Search.Input.Text == 0 then
					element.Visible = true
				else
					element.Visible = false
				end
			else
				if string.lower(element.Name):find(string.lower(Main.Search.Input.Text), 1, true) then
					element.Visible = true
				else
					element.Visible = false
				end
			end
		end
	end
end)

Main.Search.Input.FocusLost:Connect(function(enterPressed)
	if #Main.Search.Input.Text == 0 and searchOpen then
		task.wait(0.12)
		closeSearch()
	end
end)

Topbar.Search.MouseButton1Click:Connect(function()
	task.spawn(function()
		if searchOpen then
			closeSearch()
		else
			openSearch()
		end
	end)
end)


Topbar.Hide.MouseButton1Click:Connect(function()
	setVisibility(Hidden, not useMobileSizing)
end)

if MPrompt then
	MPrompt.Interact.MouseButton1Click:Connect(function()
		if Debounce then return end
		if Hidden then
			Hidden = false
			Unhide()
		end
	end)
end

for _, TopbarButton in ipairs(Topbar:GetChildren()) do
	if TopbarButton.ClassName == "ImageButton" and TopbarButton.Name ~= 'Icon' then
		TopbarButton.MouseEnter:Connect(function()
			TweenService:Create(TopbarButton, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {ImageTransparency = 0}):Play()
		end)

		TopbarButton.MouseLeave:Connect(function()
			TweenService:Create(TopbarButton, TweenInfo.new(0.7, Enum.EasingStyle.Exponential), {ImageTransparency = 0.8}):Play()
		end)
	end
end

function RayfieldLibrary:LoadConfiguration()
	local config

	if useStudio then
		config = [[{"Toggle1adwawd":"false","Keybind1":"Q","InputExample":"","Slider1dawd":120,"ColorPicfsefker1":{"B":255,"G":255,"R":255},"Slidefefsr1":80,"dawdawd":"","ColorPicker1awd":{"B":255,"G":255,"R":255},"Dropdown1":["Ocean"]}]]
	end

	if CEnabled then
		local notified
		local loaded

		local success, result = pcall(function()
			if useStudio and config then
				loaded = LoadConfiguration(config)
				return
			end

			if isfile then 
				if isfile(ConfigurationFolder .. "/" .. CFileName .. ConfigurationExtension) then
					loaded = LoadConfiguration(readfile(ConfigurationFolder .. "/" .. CFileName .. ConfigurationExtension))
				end
			else
				notified = true
				RayfieldLibrary:Notify({Title = "Rayfield Configurations", Content = "We couldn't enable Configuration Saving as you are not using file supported software.", Image = 4384402990})
			end
		end)

		if success and loaded and not notified then
			RayfieldLibrary:Notify({Title = "Rayfield Configurations", Content = "The configuration file for this script has been loaded from a previous session.", Image = 4384403532})
		elseif not success and not notified then
			warn('Rayfield Configurations Error | '..tostring(result))
			RayfieldLibrary:Notify({Title = "Rayfield Configurations", Content = "We've encountered an issue loading your configuration correctly.\n\nCheck the Developer Console for more information.", Image = 4384402990})
		end
	end
end

if useStudio then
	-- run w/ studio
	-- Feel free to place your own script here to see how it'd work in Roblox Studio before running it on your execution software.


	local Window = RayfieldLibrary:CreateWindow({
		Name = "Rayfield Example Window",
		LoadingTitle = "Rayfield Interface Suite",
		Theme = 'Default',
		Icon = 0,
		LoadingSubtitle = "by Sirius",
		ConfigurationSaving = {
			Enabled = true,
			FolderName = nil, -- Create a custom folder for your hub/game
			FileName = "Big Hub52"
		},
		Discord = {
			Enabled = false,
			Invite = "noinvitelink", -- The Discord invite code, do not include discord.gg/. E.g. discord.gg/ABCD would be ABCD
			RememberJoins = true -- Set this to false to make them join the discord every time they load it up
		},
		KeySystem = false, -- Set this to true to use our key system
		KeySettings = {
			Title = "Untitled",
			Subtitle = "Key System",
			Note = "No method of obtaining the key is provided",
			FileName = "Key", -- It is recommended to use something unique as other scripts using Rayfield may overwrite your key file
			SaveKey = true, -- The user's key will be saved, but if you change the key, they will be unable to use your script
			GrabKeyFromSite = false, -- If this is true, set Key below to the RAW site you would like Rayfield to get the key from
			Key = {"Hello"} -- List of keys that will be accepted by the system, can be RAW file links (pastebin, github etc) or simple strings ("hello","key22")
		}
	})

	local Tab = Window:CreateTab("Tab Example", 'key-round') -- Title, Image
	local Tab2 = Window:CreateTab("Tab Example 2", 4483362458) -- Title, Image

	local Section = Tab2:CreateSection("Section")


	local ColorPicker = Tab2:CreateColorPicker({
		Name = "Color Picker",
		Color = Color3.fromRGB(255,255,255),
		Flag = "ColorPicfsefker1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
		Callback = function(Value)
			-- The function that takes place every time the color picker is moved/changed
			-- The variable (Value) is a Color3fromRGB value based on which color is selected
		end
	})

	local Slider = Tab2:CreateSlider({
		Name = "Slider Example",
		Range = {0, 100},
		Increment = 10,
		Suffix = "Bananas",
		CurrentValue = 40,
		Flag = "Slidefefsr1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
		Callback = function(Value)
			-- The function that takes place when the slider changes
			-- The variable (Value) is a number which correlates to the value the slider is currently at
		end,
	})

	local Input = Tab2:CreateInput({
		Name = "Input Example",
		CurrentValue = '',
		PlaceholderText = "Input Placeholder",
		Flag = 'dawdawd',
		RemoveTextAfterFocusLost = false,
		Callback = function(Text)
			-- The function that takes place when the input is changed
			-- The variable (Text) is a string for the value in the text box
		end,
	})


	--RayfieldLibrary:Notify({Title = "Rayfield Interface", Content = "Welcome to Rayfield. These - are the brand new notification design for Rayfield, with custom sizing and Rayfield calculated wait times.", Image = 4483362458})

	local Section = Tab:CreateSection("Section Example")

	local Button = Tab:CreateButton({
		Name = "Change Theme",
		Callback = function()
			-- The function that takes place when the button is pressed
			Window.ModifyTheme('DarkBlue')
		end,
	})

	local Toggle = Tab:CreateToggle({
		Name = "Toggle Example",
		CurrentValue = false,
		Flag = "Toggle1adwawd", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
		Callback = function(Value)
			-- The function that takes place when the toggle is pressed
			-- The variable (Value) is a boolean on whether the toggle is true or false
		end,
	})

	local ColorPicker = Tab:CreateColorPicker({
		Name = "Color Picker",
		Color = Color3.fromRGB(255,255,255),
		Flag = "ColorPicker1awd", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
		Callback = function(Value)
			-- The function that takes place every time the color picker is moved/changed
			-- The variable (Value) is a Color3fromRGB value based on which color is selected
		end
	})

	local Slider = Tab:CreateSlider({
		Name = "Slider Example",
		Range = {0, 100},
		Increment = 10,
		Suffix = "Bananas",
		CurrentValue = 40,
		Flag = "Slider1dawd", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
		Callback = function(Value)
			-- The function that takes place when the slider changes
			-- The variable (Value) is a number which correlates to the value the slider is currently at
		end,
	})

	local Input = Tab:CreateInput({
		Name = "Input Example",
		CurrentValue = "",
		PlaceholderText = "Adaptive Input",
		RemoveTextAfterFocusLost = false,
		Flag = 'InputExample',
		Callback = function(Text)
			-- The function that takes place when the input is changed
			-- The variable (Text) is a string for the value in the text box
		end,
	})

	local thoptions = {}
	for themename, theme in pairs(RayfieldLibrary.Theme) do
		table.insert(thoptions, themename)
	end

	local Dropdown = Tab:CreateDropdown({
		Name = "Theme",
		Options = thoptions,
		CurrentOption = {"Default"},
		MultipleOptions = false,
		Flag = "Dropdown1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
		Callback = function(Options)
			--Window.ModifyTheme(Options[1])
			-- The function that takes place when the selected option is changed
			-- The variable (Options) is a table of strings for the current selected options
		end,
	})


	--Window.ModifyTheme({
	--	TextColor = Color3.fromRGB(50, 55, 60),
	--	Background = Color3.fromRGB(240, 245, 250),
	--	Topbar = Color3.fromRGB(215, 225, 235),
	--	Shadow = Color3.fromRGB(200, 210, 220),

	--	NotificationBackground = Color3.fromRGB(210, 220, 230),
	--	NotificationActionsBackground = Color3.fromRGB(225, 230, 240),

	--	TabBackground = Color3.fromRGB(200, 210, 220),
	--	TabStroke = Color3.fromRGB(180, 190, 200),
	--	TabBackgroundSelected = Color3.fromRGB(175, 185, 200),
	--	TabTextColor = Color3.fromRGB(50, 55, 60),
	--	SelectedTabTextColor = Color3.fromRGB(30, 35, 40),

	--	ElementBackground = Color3.fromRGB(210, 220, 230),
	--	ElementBackgroundHover = Color3.fromRGB(220, 230, 240),
	--	SecondaryElementBackground = Color3.fromRGB(200, 210, 220),
	--	ElementStroke = Color3.fromRGB(190, 200, 210),
	--	SecondaryElementStroke = Color3.fromRGB(180, 190, 200),

	--	SliderBackground = Color3.fromRGB(200, 220, 235),  -- Lighter shade
	--	SliderProgress = Color3.fromRGB(70, 130, 180),
	--	SliderStroke = Color3.fromRGB(150, 180, 220),

	--	ToggleBackground = Color3.fromRGB(210, 220, 230),
	--	ToggleEnabled = Color3.fromRGB(70, 160, 210),
	--	ToggleDisabled = Color3.fromRGB(180, 180, 180),
	--	ToggleEnabledStroke = Color3.fromRGB(60, 150, 200),
	--	ToggleDisabledStroke = Color3.fromRGB(140, 140, 140),
	--	ToggleEnabledOuterStroke = Color3.fromRGB(100, 120, 140),
	--	ToggleDisabledOuterStroke = Color3.fromRGB(120, 120, 130),

	--	DropdownSelected = Color3.fromRGB(220, 230, 240),
	--	DropdownUnselected = Color3.fromRGB(200, 210, 220),

	--	InputBackground = Color3.fromRGB(220, 230, 240),
	--	InputStroke = Color3.fromRGB(180, 190, 200),
	--	PlaceholderColor = Color3.fromRGB(150, 150, 150)
	--})

	local Keybind = Tab:CreateKeybind({
		Name = "Keybind Example",
		CurrentKeybind = "Q",
		HoldToInteract = false,
		Flag = "Keybind1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
		Callback = function(Keybind)
			-- The function that takes place when the keybind is pressed
			-- The variable (Keybind) is a boolean for whether the keybind is being held or not (HoldToInteract needs to be true)
		end,
	})

	local Label = Tab:CreateLabel("Label Example")

	local Label2 = Tab:CreateLabel("Warning", 4483362458, Color3.fromRGB(255, 159, 49),  true)

	local Paragraph = Tab:CreateParagraph({Title = "Paragraph Example", Content = "Paragraph ExampleParagraph ExampleParagraph ExampleParagraph ExampleParagraph ExampleParagraph ExampleParagraph ExampleParagraph ExampleParagraph ExampleParagraph ExampleParagraph ExampleParagraph ExampleParagraph ExampleParagraph Example"})
end

if CEnabled and Main:FindFirstChild('Notice') then
	Main.Notice.BackgroundTransparency = 1
	Main.Notice.Title.TextTransparency = 1
	Main.Notice.Size = UDim2.new(0, 0, 0, 0)
	Main.Notice.Position = UDim2.new(0.5, 0, 0, -100)
	Main.Notice.Visible = true


	TweenService:Create(Main.Notice, TweenInfo.new(0.5, Enum.EasingStyle.Exponential, Enum.EasingDirection.InOut), {Size = UDim2.new(0, 280, 0, 35), Position = UDim2.new(0.5, 0, 0, -50), BackgroundTransparency = 0.5}):Play()
	TweenService:Create(Main.Notice.Title, TweenInfo.new(0.5, Enum.EasingStyle.Exponential), {TextTransparency = 0.1}):Play()
end

if not useStudio then
	local success, result = pcall(function()
		loadstring(game:HttpGet('https://raw.githubusercontent.com/SiriusSoftwareLtd/Sirius/refs/heads/request/boost.lua'))()
	end)

	if not success then
		print('Error with boost file.')
		print(result)
	end
end

task.delay(4, function() 
	RayfieldLibrary.LoadConfiguration()
	if Main:FindFirstChild('Notice') and Main.Notice.Visible then 
		TweenService:Create(Main.Notice, TweenInfo.new(0.5, Enum.EasingStyle.Exponential, Enum.EasingDirection.InOut), {Size = UDim2.new(0, 100, 0, 25), Position = UDim2.new(0.5, 0, 0, -100), BackgroundTransparency = 1}):Play()
		TweenService:Create(Main.Notice.Title, TweenInfo.new(0.3, Enum.EasingStyle.Exponential), {TextTransparency = 1}):Play()

		task.wait(0.5)
		Main.Notice.Visible = false 
	end
end)

return RayfieldLibrary