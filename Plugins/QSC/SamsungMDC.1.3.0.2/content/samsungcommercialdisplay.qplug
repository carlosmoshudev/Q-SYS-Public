--[[ BEGIN DIGITAL SIGNATURE
T6FgpRmFpSiFn4uzcxgdxdxmPXz3RWQC5G/Uh3D+BNFc2yocBOQBotwQ0n8GizCAomq7KkEn6JBE2MnoBVTsu1q0scS+JCuJ2EYB7eq2EWhEnexhRHmOCHV3t9RZ/GTMqtC/gDcwdNg7QY5xAdxu4JKubXM+dHdp+dQYepQzTqnu6Nmq/OFzu6+UnAsHybGF77ZvsSy1pfM80yh2dIruvl6JhW5XZcU/c9WHTloCkjTwQAQXR4dd5TOjwwh2pgmZENEwJasIN6c7g8UE73Bh68tyYkUFrUTuRop71mAmchH/di8729CfijQvqFyBIlpRhmC+iX6rESLUQqU1EPN/qg==
END DIGITAL SIGNATURE ]]
-- Samsung Commercial Dispalys 
-- For devices supporting MDC Protocol
-- by QSC
-- August 2020

PluginInfo = {
    Name = "Enterprise Manager~Samsung~Commercial Display (MDC) v1.3",
    Version = "1.3",
    BuildVersion = "1.3.0.1",
    Id = "bd0a5e74-c1bf-48ee-8574-e42e1e7b2bb9",
    Author = "QSC",
    Description = "Control and Status for Samsung Commercial Displays that support the MDC protocol.",
    Manufacturer = "Samsung",
    Model = "Commercial Display",
    IsManaged = true,
    Type = Reflect and Reflect.Types.Display or 0,
}
-- Constant Values to use with the Samsung Commercial Display MDC protocol

-- MDC Defined input names: { InputName, Decimal Value of code } 
local InputCount = 27
local InputTypes = { 
  {Name="HDMI 1", Value=33},
  {Name="HDMI 2", Value=35},
  {Name="HDMI 3", Value=49},
  {Name="HDMI 4", Value=51},
  {Name="Display Port 1", Value=37},
  {Name="Display Port 2", Value=38},
  {Name="Display Port 3", Value=39},
  {Name="DTV", Value=64},
  {Name="S-Video", Value=4},
  {Name="Component", Value=8},
  {Name="AV1", Value=12},
  {Name="AV2", Value=13},
  {Name="EXT", Value=14},
  {Name="DVI", Value=24},
  {Name="PC", Value=20},
  {Name="BNC", Value=30},
  {Name="Magic Info", Value=32},
  {Name="Plugin Module", Value=80},
  {Name="HD Base T", Value=85},
  {Name="OCM", Value=86},
  {Name="Media", Value=96},
  {Name="WIDI", Value=97},
  {Name="Internal USB", Value=98},
  {Name="UL Launcher", Value=99},
  {Name="IWB", Value=100},
  {Name="Web Browser", Value=101},
  {Name="Remote Workspace", Value=102}
}
local AlternativeInputNames = {
  -- PC Input Types, Overridden to use the named buttons above
  {Name="HDMI 1_PC", Value=34, ButtonIndex=1},
  {Name="HDMI 2_PC", Value=36, ButtonIndex=2},
  {Name="HDMI 3_PC", Value=50, ButtonIndex=3},
  {Name="HDMI 4_PC", Value=52, ButtonIndex=4},
  {Name="DVI_Video", Value=31, ButtonIndex=14},
}
function GetInputIndex(val)
  for i,input in ipairs(InputTypes) do
    if(input.Value == val)then
      return i
    end
  end
  for i,input in ipairs(AlternativeInputNames) do
    if(input.Value == val)then
      return input.ButtonIndex
    end
  end
end

-- These are in order, based on their hex value converted to decimal
local PanelType = { 
  "PDP",
  "LCD",
  "DLP",
  "LED",
  "CRT",
  "OLED"
}

-- These are in order, based on their hex value converted to decimal
local ModelList = { 
  "PPM50H2",
  "PPM42S2",
  "PS-42P2ST",
  "PS-50P2HT",
  "SyncMaster 400T",
  "SyncMaster 403T",
  "PPM42S3, SPD-42P3SM",
  "PPM50H3, SPD-50P3HM",
  "PPM63H3, SPD-63P3HM",
  "PS-42P3ST",
  "SyncMaster 323T",
  "SyncMaster 403T – CT40CS(N)",
  "PPMxxM5x",
  "SyncMaster 320P(n), SyncMaster 400P(n), SyncMaster 460P(n)",
  "-",
  "SyncMaster 320PX, SyncMaster 400PX(n), SyncMaster 460PX(n)",
  "-",
  "-",
  "SyncMaster 400TX(n)",
  "SyncMaster 570DX",
  "SyncMaster 320DX(n), SyncMaster 400DX(n), SyncMaster 460DX(n), SyncMaster 700DX(n), SyncMaster 820DX(n)",
  "SyncMaster 460TX(n)",
  "SyncMaster 400UX(n), SyncMaster 460UX(n), SyncMaster 460DR(n)",
  "SyncMaster 42TS, SyncMaster 42PS, SyncMaster P42HP",
  "SyncMaster P50Hn",
  "SyncMaster P50F(n), SyncMaster P50FP",
  "SyncMaster P63F(n), SyncMaster P63FP",
  "SyncMaster 320MX(n)",
  "SyncMaster 400CX(n), SyncMaster 400MX(n), SyncMaster 400MP(n)",
  "-",
  "-",
  "SyncMaster 460CX(n), SyncMaster 460MP(n)",
  "SyncMaster 520DX(n)",
  "SyncMaster 400Uxn-UD, SyncMaster 460Uxn-UD",
  "SyncMaster 400FX(n)",
  "SyncMaster 460DRn-A",
  "SyncMaster 460Utn-UD",
  "SyncMaster 460UT(n)",
  "SyncMaster 320MX(n)-2, SyncMaster 320MP-2",
  "SyncMaster 400MX(n)-2, SyncMaster 400FP(n)-2",
  "SyncMaster 460MX(n)-2, SyncMaster 460FP(n)-2",
  "SyncMaster P42H-2",
  "SyncMaster P50HP",
  "SyncMaster P50FP",
  "SyncMaster P63FP",
  "SyncMaster 460Rn-S",
  "SyncMaster 400DXn-S",
  "SyncMaster 460DXn-S",
  "SyncMaster 400CX(n)-2, SyncMaster 460CX(n)-2 ",
  "SyncMaster 400DX(n)-2, SyncMaster 460DX(n)-2, SyncMaster 700DX(n)-2, SyncMaster 820DX(n)-2, SyncMaster 650MP(n)",
  "SyncMaster 400UX(n)-2, SyncMaster 460UX(n)-2",
  "SyncMaster 700DRn",
  "SyncMaster 230TSn, SyncMaster 230MXn",
  "SyncMaster 460DMn",
  "SyncMaster 400Uxn-UD2, SyncMaster 460Uxn-UD2",
  "SyncMaster P50HP-2",
  "SyncMaster P63FP-2",
  "SyncMaster 400Exn",
  "SyncMaster 460Exn",
  "SyncMaster 550Exn",
  "SyncMaster 460UT(n)-2",
  "SyncMaster 550DX(n)",
  "SyncMaster 460CX(n)-3, SyncMaster 400CX(n)-3, SyncMaster 320CX(n)-3",
  "SyncMaster 520LD",
  "SyncMaster 460UX(n)-3 SyncMaster 400UX(n)-3 SyncMaster 400BX",
  "SyncMaster 460TS(n)-3 SyncMaster 400TS(n)-3",
  "SyncMaster 460UT(n)-UD2",
  "UE46A/UE55A ME40A/ME46A/ME55A DE40A/DE46A/DE55A MD32B/MD40B/MD46B/MD55B ME32B/ME40B/ME46B ME55B/ME65B/ME75B, SL46B",
  "SyncMaster UD55A",
  "DE40C/DE46C/DE55C/UD46C/UD55C/UE46C/UE55C",
  "SyncMaster UD22A",
  "SyncMaster NL22B",
  "MD32C, MD40C, MD46C, MD55C, ME95C",
  "ED32C/ED40C/ED46C/ED55C/ED65C/ED75C/ED32D/ED40D/ED46D/ED55D/ED65D/ED75D",
  "SyncMaster LE32C, SyncMaster LE46C, SyncMaster LE55C",
  "SyncMaster UD46C-B",
  "ME32C/ME40C/ME46C/ME55C",
  "SyncMaster UD55C-B",
  "DB22D/DB32D/DB40D/DB48D/DB55D/DM32D/OH46D/OH55D",
  "DM40D/DM48D/DM55DDM65D/DM75D, UE46D/UE55D, DH40D/DH48D/DH55D, OM46D/OM55D/OM75D",
  "EB40D/EB48D",
  "SyncMasterQM55D, SyncMasterQM85D, SyncMasterQM50D, SyncMasterQM40D, SyncMasterQM105D",
  "EM65E/EM75E, ED65E/ED75E",
  "DH40E,DH48E,DH55E, DM32E,DM40E,DM48E, DM55E,DM65E,DM75E, DB32E,DB40E,DB48E,DB55E, DM65E-BR, DM75E-BR, DM82E-BR, PE40E,PE46E,PE55E, DM10E, OHE, OME, MLE, SHF, UD46E, UD46E-P, UD55EP, UD55E-P, UD55E, UD55E-SS",
  "RH48E, RH55E",
  "SyncMaster UD46E-B, SyncMaster UD55E-B, SyncMaster UD46E-C, SyncMaster UD46E-A, SyncMaster UD55E-A, SyncMaster UH55F-E, SyncMaster UM55H-E, SyncMaster UH46N-E, SyncMaster UM46N-E",
  "IL015E/ IL025E/IL20E/ILF/ISF",
  "SBB-ES",
  "DC32E / DC40E / DC48E / DC55E",
  "OM24E, OH24E/OH75E",
  "SBB-MT",
  "DC32E, DC32E-M / DC40EM / DC40E-M / DC48EM / DC48E-M / DC55EM / DC55E-MM, DC32E, DC32E-H / DC40EH / DC40E-H / DC48EH / DC48E-H / DC55EH / DC55E-H",
  "QM49F / QM55F / QM65F / QM75F / QM98F",
  "PM32F / PM43F / PM49F / PM55F / PH43F / PH49F / PM32F / PM43F / PM49F / PM55F / PH43F / PH49F / PF55F/ PF55F / ML55F/ ML55F-R / PH43FR / PH43F-P / PH49FP / PH49F-P/ PH55FP / PH55F-P / PM43H / PM49H / PM55HP / PM43H / PM49H / PM55H",
  "OM46F / OM55F / OH46F / OH55F / OM46F / OM55F / OH46F / OH55F",
  "DC90F",
  "UH46F5",
  "OH85F",
  "DC43H / DC49H / DC55H",
  "QMH / QHH / PMJ / PHJ / PBJ",
  "IFH",
  "OHH",
  "RM49H",
  "DC43J / DC49JDC49J",
  "QMN / QBN / QEN / QHR/ QMR / QMR-N / QBR / QBR-N / QBR-T / SHR / QET",
  "OHN / OHN-K / OHN-D / OHN-DK / OMN-D / OHF-S",
  "VMRNU",
  "QER / QPR-8K",
  "BE43R, BE49R",
  "VH55R-R",
  "OMR",
  "QPT-8K"
}

function GetColor(props)
  return { 102, 102, 102 }
end

function GetPrettyName(props)
  return "Samsung Commercial Display " .. PluginInfo.Version
end

local pagenames = {"Setup","Control"}
function GetPages(props)
  local pages = {}
  for ix,name in ipairs(pagenames) do
    table.insert(pages, {name = pagenames[ix]})
  end
  return pages
end

function GetProperties()
  local props = {}
  table.insert(props,{
    Name    = "Connection Type",
    Type    = "enum", 
    Choices = {"Ethernet", "Serial"},
    Value   = "Ethernet"
  })
  table.insert(props,{
    Name    = "Debug Print",
    Type    = "enum",
    Choices = {"None", "Tx/Rx", "Tx", "Rx", "Function Calls", "All"},
    Value   = "None"
  })
  table.insert(props,{
    Name  = "Poll Interval",
    Type  = "integer",
    Min   = 1,
    Max   = 60, 
    Value = 3
  })
  table.insert(props,{
    Name  = "Get Device Info",
    Type  = "boolean",
    Value = true
  })
  return props
end

function RectifyProperties(props)
  if props.plugin_show_debug.Value==false then props["Debug Print"].IsHidden=true end
  return props
end

function GetControls(props)
  local ctrls = {}
  -- Configuration Controls --
  table.insert(ctrls, {
    Name         = "IPAddress",
    ControlType  = "Text",
    Count        = 1,
    DefaultValue = "Enter an IP Address",
    UserPin      = true,
    PinStyle     = "Both"
  })
  table.insert(ctrls, {
    Name         = "Port",
    ControlType  = "Text",
    ControlUnit  = "Integer",
    DefaultValue = "1515",
    Min          = 1,
    Max          = 65535,
    Count        = 1,
    UserPin      = true,
    PinStyle     = "Both"
  })
  table.insert(ctrls, {
    Name         = "DisplayID",
    ControlType  = "Knob",
    ControlUnit  = "Integer",
    Count        = 1,
    UserPin      = true,
    PinStyle     = "Both",
    DefaultValue = 0,
    Min          = 0,
    Max          = 253
  })
  table.insert(ctrls, {
    Name         = "Broadcast",
    ControlType  = "Button",
    ButtonType   = "Toggle",
    Count        = 1,
    UserPin      = true,
    PinStyle     = "Both"
  })
  table.insert(ctrls, {
    Name         = "Reset",
    ControlType  = "Button",
    ButtonType   = "Trigger",
    Count        = 1,
    UserPin      = true,
    PinStyle     = "Input"
  })
  
  -- Status Controls --
  table.insert(ctrls, {
    Name          = "Status",
    ControlType   = "Indicator",
    IndicatorType = Reflect and "StatusGP" or "Status",
    PinStyle      = "Output",
    UserPin       = true,
    Count         = 1
  })
  table.insert(ctrls, {
    Name         = "ModelNumber",
    ControlType  = "Text",
    PinStyle     = "Output",
    UserPin      = true,
    Count        = 1
  })
  table.insert(ctrls, {
    Name         = "PanelType",
    ControlType  = "Text",
    PinStyle     = "Output",
    UserPin      = true,
    Count        = 1
  })
  table.insert(ctrls, {
    Name         = "ModelName",
    ControlType  = "Text",
    PinStyle     = "Output",
    UserPin      = true,
    Count        = 1
  })
  table.insert(ctrls, {
    Name         = "DeviceName",
    ControlType  = "Text",
    PinStyle     = "Output",
    UserPin      = true,
    Count        = 1
  })
  table.insert(ctrls, {
    Name         = "SerialNumber",
    ControlType  = "Text",
    PinStyle     = "Output",
    UserPin      = true,
    Count        = 1
  })
  table.insert(ctrls, {
    Name         = "DeviceFirmware",
    ControlType  = "Text",
    PinStyle     = "Output",
    UserPin      = true,
    Count        = 1
  })
  table.insert(ctrls, {
    Name         = "MACAddress",
    ControlType  = "Text",
    PinStyle     = "Output",
    UserPin      = true,
    Count        = 1,
    DefaultValue = ""
  })
  
  -- Power Controls --
  table.insert(ctrls, {
    Name          = "PowerStatus",
    ControlType   = "Indicator",
    IndicatorType = "Led",
    Count         = 1,
    UserPin       = true,
    PinStyle      = "Output"
  })
  table.insert(ctrls, {
    Name          = "StandbyStatus",
    ControlType   = "Indicator",
    IndicatorType = "Led",
    Count         = 1,
    UserPin       = true,
    PinStyle      = "Output"
  })
  table.insert(ctrls, {
    Name         = "Power",
    ControlType  = "Button",
    ButtonType   = "Trigger",
    Count        = 1,
    UserPin      = true,
    PinStyle     = "Input",
    Icon         = "Power"
  })
  table.insert(ctrls, {
    Name         = "PowerOn",
    ControlType  = "Button",
    ButtonType   = "Trigger",
    Count        = 1,
    UserPin      = true,
    PinStyle     = "Input"
  })
  table.insert(ctrls, {
    Name         = "PowerOff",
    ControlType  = "Button",
    ButtonType   = "Trigger",
    Count        = 1,
    UserPin      = true,
    PinStyle     = "Input"
  })
  table.insert(ctrls, {
    Name         = "Reboot",
    ControlType  = "Button",
    ButtonType   = "Trigger",
    Count        = 1,
    UserPin      = true,
    PinStyle     = "Input"
  })
  
  -- Input Controls --
  table.insert(ctrls, {
    Name         = "Input",
    ControlType  = "Text",
    PinStyle     = "Output",
    UserPin      = true,
    Count        = 1
  })
  table.insert(ctrls, {
    Name         = "InputButtons",
    ControlType  = "Button",
    ButtonType   = "Momentary",
    Count        = InputCount,
    UserPin      = true,
    PinStyle     = "Both"
  })
  table.insert(ctrls, {
    Name          = "InputStatus",
    ControlType   = "Indicator",
    IndicatorType = "Led",
    Count         = InputCount
  })
  table.insert(ctrls, {
    Name         = "InputNext",
    ControlType  = "Button",
    ButtonType   = "Trigger",
    Count        = 1,
    UserPin      = true,
    PinStyle     = "Input"
  })
  
  -- Sound Controls --
  table.insert(ctrls, {
    Name         = "Volume",
    ControlType  = "Knob",
    ControlUnit  = "Integer",
    DefaultValue = 0,
    Min          = 0,
    Max          = 100,
    Count        = 1,
    UserPin      = true,
    PinStyle     = "Both"
  })
  table.insert(ctrls, {
    Name         = "VolumeUp",
    ControlType  = "Button",
    ButtonType   = "Trigger",
    Count        = 1,
    UserPin      = true,
    PinStyle     = "Input",
    Icon         = "Plus"
  })
  table.insert(ctrls, {
    Name         = "VolumeDown",
    ControlType  = "Button",
    ButtonType   = "Trigger",
    Count        = 1,
    UserPin      = true,
    PinStyle     = "Input",
    Icon         = "Minus"
  })
  table.insert(ctrls, {
    Name         = "Mute",
    ControlType  = "Button",
    ButtonType   = "Toggle",
    Count        = 1,
    UserPin      = true,
    PinStyle     = "Both"
  })
  return ctrls
end

function GetPins(props)
  local pins = {}
  if props["Connection Type"].Value=="Serial" then 
    table.insert(pins,{Name="input", Direction="input", Domain="serial"})
  end
  return pins
end

function GetControlLayout(props)
  local layout   = {}
  local graphics = {}
  local CurrentPage = pagenames[props["page_index"].Value]
  local colors = {  
    Background  = {232,232,232},
    Transparent = {255,255,255,0},
    Text        = {24,24,24},
    Header      = {0,0,0},
    Button      = {48,32,40},
    Red         = {217,32,32},
    DarkRed     = {80,16,16},
    Green       = {32,217,32},
    OKGreen     = {48,144,48},
    Blue        = {32,32,233},
    Black       = {0,0,0},
    White       = {255,255,255},
    Gray        = {96,96,96}
  }
  
  if CurrentPage == "Setup" then
    -- User defines connection properties
    table.insert(graphics,{Type="GroupBox",Text="Connect",Fill=colors.Background,StrokeWidth=1,CornerRadius=4,HTextAlign="Left",Position={5,5},Size={400,120}})
    if props["Connection Type"].Value=="Ethernet" then 
      table.insert(graphics,{Type="Text",Text="IP Address",Position={15,35},Size={100,16},FontSize=14,HTextAlign="Right"})
      layout["IPAddress"] = {PrettyName="Settings~IP Address",Style="Text",Color=colors.White,Position={120,35},Size={99,16},FontSize=12}
      table.insert(graphics,{Type="Text",Text="Port",Position={15,60},Size={100,16},FontSize=14,HTextAlign="Right"})
      layout["Port"] = {PrettyName="Settings~Port",Style="Text",Color=colors.White,Position={120,60},Size={99,16},FontSize=12}
      table.insert(graphics,{Type="Text",Text="(1515 default)",Position={221,60},Size={100,18},FontSize=10,HTextAlign="Left"})
      table.insert(graphics,{Type="Text",Text="Reboot",Position={315,35},Size={70,14},FontSize=12,HTextAlign="Center",Color=colors.Text})
      layout["Reboot"] = {PrettyName="Power~Reboot", Style="Button", Color=colors.Button, FontColor=colors.Red, FontSize=14, CornerRadius=2, Position={325,48}, Size={50,20} }
    else
      table.insert(graphics,{Type="Text",Text="Reset Serial",Position={5,32},Size={110,16},FontSize=14,HTextAlign="Right"})
      layout["Reset"] = {PrettyName="Settings~Reset Serial", Style="Button", Color=colors.Button, FontColor=colors.Red, FontSize=14, CornerRadius=2, Position={120,30}, Size={50,20} }
      table.insert(graphics,{Type="Text",Text="Reboot",Position={15,57},Size={100,16},FontSize=14,HTextAlign="Right"})
      layout["Reboot"] = {PrettyName="Power~Reboot", Style="Button", Color=colors.Button, FontColor=colors.Red, FontSize=14, CornerRadius=2, Position={120,55}, Size={50,20} }
    end
    table.insert(graphics,{Type="Text",Text="Display ID",Position={15,85},Size={100,16},FontSize=14,HTextAlign="Right"})
    layout["DisplayID"] = {Type="Text",PrettyName="Settings~Display ID Number", Style="Text", FontColor=colors.Text, Position={120,85}, Size={99,16}, FontSize=12}
    
  
    -- Status fields updated upon connect show model/name/serial/sw rev
    table.insert(graphics,{Type="GroupBox",Text="Status",Fill=colors.Background,StrokeWidth=1,CornerRadius=4,HTextAlign="Left",Position={5,135},Size={400,220}})
    layout["Status"] = {PrettyName="Status~Connection Status", Position={40,165}, Size={330,32}, Padding=4 }
    table.insert(graphics,{Type="Text",Text="Device Name",Position={15,212},Size={100,16},FontSize=12,HTextAlign="Right"})
    layout["DeviceName"] = {PrettyName="Status~Device Name", Style="Text", HTextAlign="Left", IsReadOnly=true, Color=colors.Transparent, StrokeWidth=0, FontSize=14, IsBold=true, FontColor=colors.Text, Position={120,211}, Size={255,16} }
    table.insert(graphics,{Type="Text",Text="Model Name",Position={15,235},Size={100,16},FontSize=12,HTextAlign="Right"})
    layout["ModelName"] = {PrettyName="Status~Model Name", Style="Text", HTextAlign="Left", IsReadOnly=true, Color=colors.Transparent, StrokeWidth=0, FontSize=14, IsBold=true, FontColor=colors.Text, Position={120,234}, Size={255,16} }
    table.insert(graphics,{Type="Text",Text="Serial Number",Position={15,258},Size={100,16},FontSize=12,HTextAlign="Right"})
    layout["SerialNumber"] = {PrettyName="Status~Serial Number", Style="Text", HTextAlign="Left", IsReadOnly=true, Color=colors.Transparent, StrokeWidth=0, FontSize=14, IsBold=true, FontColor=colors.Text, Position={120,257}, Size={255,16} }
    table.insert(graphics,{Type="Text",Text="Software Version",Position={15,281},Size={100,16},FontSize=12,HTextAlign="Right"})
    layout["DeviceFirmware"] = {PrettyName="Status~SW Version", Style="Text", HTextAlign="Left", IsReadOnly=true, Color=colors.Transparent, StrokeWidth=0, FontSize=14, IsBold=true, FontColor=colors.Text, Position={120,280}, Size={255,16} }
    table.insert(graphics,{Type="Text",Text="MAC Address",Position={15,304},Size={100,16},FontSize=12,HTextAlign="Right"})
    layout["MACAddress"] = {PrettyName="Status~MAC Address", Style="Text", HTextAlign="Left", IsReadOnly=true, Color=colors.Transparent, StrokeWidth=0, FontSize=14, IsBold=true, FontColor=colors.Text, Position={120,303}, Size={255,16} }
  
    table.insert(graphics,{Type="Text",Text="Samsung Commercial Display Plugin version "..PluginInfo.Version,Position={15,340},Size={380,14},FontSize=10,HTextAlign="Right", Color=colors.Gray})
  
    --Invisible Controls for pin access to data
    layout["ModelNumber"] = {PrettyName="Status~Model Family", Style="Text", HTextAlign="Left", IsReadOnly=true, Color=colors.Transparent, StrokeWidth=0, FontSize=14, IsBold=true, FontColor=colors.Text, Position={1,1}, Size={1,1}, IsInvisible=true }
    layout["PanelType"] = {PrettyName="Status~Panel Type", Style="Text", HTextAlign="Left", IsReadOnly=true, Color=colors.Transparent, StrokeWidth=0, FontSize=14, IsBold=true, FontColor=colors.Text, Position={1,1}, Size={1,1}, IsInvisible=true }
  
  elseif CurrentPage == "Control" then
    -- Control interface for the monitor
    table.insert(graphics,{Type="GroupBox",Text="Control",Fill=colors.Background,StrokeWidth=1,CornerRadius=4,HTextAlign="Left",Position={5,5},Size={305,600}})
    table.insert(graphics,{Type="Text",Text="Broadcast Mode",Position={108,20},Size={125,25},FontSize=12,HTextAlign="Right", VTextAlign="Middle", Color=colors.Text})
    layout["Broadcast"] = {PrettyName="Settings~Broadcast", Style="Button", UnlinkOffColor=true, Color=colors.Blue, OffColor=colors.Gray, FontSize=14, CornerRadius=2, Position={234,20}, Size={65,25} }
  
    table.insert(graphics,{Type="Header",Text="Power",Position={15,55},Size={285,14},FontSize=12,HTextAlign="Center",Color=colors.Header})
    table.insert(graphics,{Type="Text",Text="On",Position={12,70},Size={71,14},FontSize=12,HTextAlign="Center",Color=colors.Text})
    layout["PowerOn"] = {PrettyName="Power~On", Style="Button", Color=colors.Button, FontColor=colors.Hreen, FontSize=14, CornerRadius=2, Position={15,83}, Size={65,25} }
    table.insert(graphics,{Type="Text",Text="Off",Position={231,70},Size={71,14},FontSize=12,HTextAlign="Center",Color=colors.Text})
    layout["PowerOff"] = {PrettyName="Power~Off", Style="Button", Color=colors.Button, FontColor=colors.Red, FontSize=14, CornerRadius=2, Position={234,83}, Size={65,25} }
    --table.insert(graphics,{Type="Text",Text="Status",Position={12,70},Size={71,14},FontSize=12,HTextAlign="Center",Color=colors.Text})
    layout["PowerStatus"] = {PrettyName="Power~Status", Style="LED", Color=colors.Blue, OffColor=colors.DarkRed, UnlinkOffColor=true, CornerRadius=6, Position={147,85}, Size={20,20} }
  
    table.insert(graphics,{Type="Header",Text="Input",Position={15,120},Size={285,14},FontSize=12,HTextAlign="Center",Color=colors.Header})
    table.insert(graphics,{Type="Text",Text="Current Input",Position={12,139},Size={75,20},FontSize=12,HTextAlign="Right", VTextAlign="Middle", Color=colors.Text})
    layout["Input"] = {PrettyName="Input~Current Input", Style="Text", FontColor=colors.Black, FontSize=14, Position={88,139} , Size={211,20} }
    local i,j=0,0
    for val,input in pairs(InputTypes) do
      if (i+(j*4)) < InputCount then
        table.insert(graphics,{Type="Text",Text=input.Name,Position={12+(73*i),160+j*45},Size={71,22},FontSize=10,Color=colors.Text,HTextAlign="Center", VTextAlign="Bottom"})
        layout["InputButtons "..(j*4+1+i)] = {PrettyName="Input~"..input.Name, Style="Button", UnlinkOffColor=true, Color=colors.Blue, OffColor=colors.Button, FontColor=colors.White, FontSize=14, Position={15+(73*i), 180+j*45}, Size={65,25} }
        layout["InputStatus "..(j*4+1+i)] = {PrettyName="Input~Status "..input.Name, Style="LED", Color=colors.White, OffColor=colors.Transparent, UnlinkOffColor=true, StrokeWidth=0, Position={68+(73*i), 182+j*45}, Size={10,10}, ZOrder=-1000}
        i=i+1
        if(i>3)then 
          j=j+1
          i=0
        end
      end
    end
    --[[ Next Source Functionality removed due to instability with different models not having all inputs available
    table.insert(graphics,{Type="Text",Text="Next Source",Position={12+(73*i),160+j*45},Size={71,22},FontSize=10,Color=colors.Text,HTextAlign="Center", VTextAlign="Bottom"})
    layout["InputNext"] = { PrettyName="Input~Next Source", Style="Button", Color=colors.Button, FontColor=colors.Black, FontSize=14, Position={15+(73*i),180+j*45}, Size={65,25} }
    ]]
  
    table.insert(graphics,{Type="Header",Text="Volume",Position={15,490},Size={285,14},FontSize=12,HTextAlign="Center",Color=colors.Header})
    layout["VolumeDown"] = { PrettyName="Volume~Down", Style="Button", Color=colors.Button, IconColor=colors.White, Position={15,512}, Size={30,30} }
    layout["Volume"] = { PrettyName="Volume~Level", Style="Fader", Color=colors.Button, Position={50,510}, Size={140,35} }
    layout["VolumeUp"] = { PrettyName="Volume~Up", Style="Button", Color=colors.Button, IconColor=colors.White, Position={195,512}, Size={30,30} }
    table.insert(graphics,{Type="Text",Text="Mute",Position={224,501},Size={85,15},FontSize=10,Color=colors.Text,HTextAlign="Center", VTextAlign="Bottom"})
    layout["Mute"] = { PrettyName="Volume~Mute", Style="Button", Color=colors.Red, Position={234,515}, Size={65,25} }
  
    table.insert(graphics,{Type="Text",Text="Samsung Commercial Display Plugin version "..PluginInfo.Version,Position={15,590},Size={285,14},FontSize=10,HTextAlign="Right", Color=colors.Gray})
  end
  return layout, graphics
end

--Start event based logic
if Controls then
  --[[
    Samsung Commercial Display Runtime
  
    2 Connectivity types;  Direct Serial Connection and Ethernet
    Both use the same commands
    Based on user set Property "Connection Type"  the communication engine and send and receive functions will be defined to use one or the other.
  
    The command parsing, processsing, and input handlers will call the same functions so Send needs to have the same inputs in both builds.
  ]]
  
  -- Control aliases
  Status = Controls.Status
  
  -- Variables and flags
  DebugTx=false
  DebugRx=false
  DebugFunction=false
  DebugPrint=Properties["Debug Print"].Value
  
  -- Timers, tables, and constants
  StatusState = { OK = 0, COMPROMISED = 1, FAULT = 2, NOTPRESENT = 3, MISSING = 4, INITIALIZING = 5 }
  Heartbeat = Timer.New()
  PowerupTimer = Timer.New()
  VolumeDebounce = Timer.New()
  PowerupCount = 0
  PollRate = Properties["Poll Interval"].Value
  Timeout = PollRate + 10
  BufferLength = 1024
  ConnectionType = Properties["Connection Type"].Value
  DataBuffer = ""
  CommandQueue = {}
  CommandProcessing = false
  --Internal command timeout
  CommandTimeout = 5
  CommunicationTimer = Timer.New()
  PowerOnDebounceTime = 20
  PowerOnDebounce = false
  TimeoutCount = 0
  ActiveInput = 1
  for i=1,InputCount do
    if Controls['InputButtons'][i].Boolean then
      ActiveInput = i
    end
  end
  
  --Hide controls that are just for pins
  Controls["ModelNumber"].IsInvisible=true
  Controls["PanelType"].IsInvisible=true
  
  --[[
    Request Command Set
    Named reference to each of the command objects used here in
    Note commands are in decimal here, translation to hex is done in Send()
  ]]
  local Request = {
    Status={Command=0,Data={}},
    SerialNumber={Command=11,Data={}},
    SWVersion={Command=14,Data={}},
    ModelNumber={Command=16,Data={}},
    ModelName={Command=138,Data={}},
    DeviceName={Command=103,Data={}},
    MACAddress={Command=27,Data={129}},
  
    PowerStatus={Command=17,Data={}},
    PowerOn={Command=17,Data={1}},
    PowerOff={Command=17,Data={0}},
    Reboot={Command=17,Data={2}},
  
    DisplayStatus={Command=13,Data={}},
    InputStatus={Command=20,Data={}},
    InputSet={Command=20,Data={}},  
  
    SoundStatus={Command=9,Data={}},
    VolumeStatus={Command=18,Data={}},
    VolumeSet={Command=18,Data={0}},
    VolumeUp={Command=98,Data={0}},
    VolumeDown={Command=98,Data={1}},
    MuteStatus={Command=19,Data={}},
    MuteOn={Command=19,Data={1}},
    MuteOff={Command=19,Data={0}}
  }
  
  -- Helper functions
  -- A function to determine common print statement scenarios for troubleshooting
  function SetupDebugPrint()
    if DebugPrint=="Tx/Rx" then
      DebugTx,DebugRx=true,true
    elseif DebugPrint=="Tx" then
      DebugTx=true
    elseif DebugPrint=="Rx" then
      DebugRx=true
    elseif DebugPrint=="Function Calls" then
      DebugFunction=true
    elseif DebugPrint=="All" then
      DebugTx,DebugRx,DebugFunction=true,true,true
    end
  end
  
  -- A function to clear controls/flags/variables and clears tables
  function ClearVariables()
    if DebugFunction then print("ClearVariables() Called") end
    Request["InputSet"]["Data"][1]=1
    Controls["SerialNumber"].String = ""
    Controls["DeviceFirmware"].String = ""
    Controls["ModelNumber"].String = ""
    Controls["ModelName"].String = ""
    Controls["DeviceName"].String = ""
    Controls["MACAddress"].String = ""
    DataBuffer = ""
    CommandQueue = {}
  end
  
  --Reset any of the "Unavailable" data;  Will cause a momentary colision that will resolve itself the customer names the device "Unavailable"
  function ClearUnavailableData()
    if DebugFunction then print("ClearUnavailableData() Called") end
    -- If data was unavailable reset it; the next poll loop will test for it again
    for i,ctrl in ipairs({ "SerialNumber", "DeviceFirmware", "ModelNumber", "ModelName", "DeviceName", "MACAddress" }) do
      if(Controls[ctrl].String == "Unavailable")then
        Controls[ctrl].String = ""
      end
    end
  end
  
  -- Update the Status control
  function ReportStatus(state,msg)
    if DebugFunction then print("ReportStatus() Called: "..state.." - "..msg) end
    --Dont report status changes immediately after power on
    if PowerOnDebounce == false then
      local msg=msg or ""
      Status.Value=StatusState[state]
      Status.String=msg
      --Show the power off state if we can't communicate
      if(state ~= "OK")then
        Controls["PowerStatus"].Value = 0
      end
    end
  end
  
  -- Interface will receive a lot of strings of hex bytes; Printing decimal values for easier debug
  function PrintByteString(ByteString, header)
    if DebugFunction then print("PrintByteString() Called") end
    local result=header or ""
    if(ByteString:len()>0)then
      for i=1,ByteString:len() do
        result = result .. ByteString:byte(i) .. " "
      end
    end
    print( result )
  end
  
  -- Arrays of bytes may get used often; Printing decimal values for easier debug
  function PrintByteArray(ByteArray, header)
    if DebugFunction then print("PrintByteArray() Called") end
    local result=header or ""
    if(#ByteArray>0)then
      for i=1,#ByteArray do
        result = result .. ByteArray[i] .. " "
      end
    end
    print( result )
  end
  
  -- Set the current input indicators
  function SetActiveInput(index)
    if DebugFunction then print("SetActiveInputIndicator() Called") end
    if(index)then
      Controls["Input"].String = InputTypes[index].Name
      Controls["InputButtons"][ActiveInput].Value = false
      Controls["InputStatus"][ActiveInput].Value = false
      Controls["InputButtons"][index].Value = true
      Controls["InputStatus"][index].Value = true
      ActiveInput = index
    else
      Controls["Input"].String = "Unknown"
      Controls["InputButtons"][ActiveInput].Value = false
      Controls["InputStatus"][ActiveInput].Value = false
    end
  end
  
  --Parse a string from byte array
  function ParseString(data)
    if DebugFunction then print("ParseString() Called") end
    local name = ""
    for i,byte in ipairs(data) do
      name = name .. string.char(byte)
    end
    return name
  end
  
  --A debounce timer on power up avoids reporting the TCP reset that occurs as ane error
  function ClearDebounce()
    PowerOnDebounce = false
  end
  
  
  ------ Communication Interfaces --------
  
  -- Shared interface functions
  function Init()
    if DebugFunction then print("Init() Called") end
    Disconnected()
    Connect()
  end
  
  function Connected()
    if DebugFunction then print("Connected() Called") end
    CommunicationTimer:Stop()
    Heartbeat:Start(PollRate)
    CommandProcessing = false
    SendNextCommand()
  end
  
  --Wrapper for setting the pwer level
  function SetPowerLevel(val)
    --
    if val==1 and Controls["PowerStatus"].Value~=val then
      ClearUnavailableData()
      PowerupTimer:Stop()
  
    --If the display is being shut off, clear the buffer of commands
    --This prevents a hanging off command from immediately turn the display off on next power-on command
    elseif(val == 0)then
      CommandQueue = {}
    end
    Controls["PowerStatus"].Value = val
  end
  
  --[[  Communication format
    All commands are hex bytes of the format:
       Header   Command   DeviceID   DataLength   Val 1.......   CheckSum
        0xAA     0x??       0x??      0x??(int)    0x??0x??...     0x??
    Extended commands will have Val 1 be a SubCommand when sending
    Responses will contain an ACK/NACK as the first Val in the data section
    Checksum ignores Header byte
    Switching Device ID for 0xFE will cause the display to broadcast the command to all daisy chained serial connected displays, but won't respond.
  
    Both Serial and TCP mode must contain functions:
      Connect()
      Controls["PowerOn"].EventHandler() 
      And a receive handler that passes data to ParseData()
  ]]
  
  -- Take a request object and queue it for sending.  Object format is of:
  --  { Command=int, Data={int} }
  --  ints must be between 0 and 255 for hex translation
  --  Broadcast is a Boolean to determine if using Broadcast ID for this send
  function Send(cmd, broadcast, sendImmediately)
    if DebugFunction then print("Send() Called") end
    local ID = Controls["DisplayID"].Value
    if(broadcast)then
      ID = 254
    end
    local value = "\xAA".. string.char( cmd.Command ) .. string.char( ID ) .. string.char( #cmd.Data )
    local checksum = cmd.Command + ID + #cmd.Data
    local i = 1
  
    while cmd.Data[i]~=nil do
      value = value .. string.char( cmd.Data[i] ) 
      checksum = checksum + cmd.Data[i]
      i=i+1
    end
    value = value .. string.char( checksum % 256 ) 
  
    --Check for if a command is already queued
    for i, val in ipairs(CommandQueue) do
      if(val == value)then
        --Some Commands should be sent immediately
        if sendImmediately then
          --remove other copies of a command and move to head of the queue
          table.remove(CommandQueue,i)
          if DebugTx then PrintByteString(value, "Sending: ") end
          table.insert(CommandQueue,1,value)
        end
        return
      end
    end
    --Queue the command if it wasn't found
    table.insert(CommandQueue,value)
    SendNextCommand()
  end
  
  
  --Timeout functionality
  -- Close the current and start a new connection with the next command
  -- This was included due to behaviour within the Samsung Serial; may be redundant check on TCP mode
  CommunicationTimer.EventHandler = function()
    if DebugFunction then print("CommunicationTimer Event (timeout) Called") end
    ReportStatus("MISSING","Communication Timeout")
    CommunicationTimer:Stop()
    CommandProcessing = false
    SendNextCommand()
  end 
  
  --  Serial mode Command function  --
  if ConnectionType == "Serial" then
    print("Serial Mode Initializing...")
    -- Create Serial Connection
    Samsung = SerialPorts[1]
    Baudrate, DataBits, Parity = 9600, 8, "N"
  
    --Send the display the next command off the top of the queue
    function SendNextCommand()
      if DebugFunction then print("SendNextCommand() Called") end
      if CommandProcessing then
        -- Do Nothing
      elseif #CommandQueue > 0 then
        CommandProcessing = true
        if DebugTx then PrintByteString(CommandQueue[1], "Sending: ") end
        Samsung:Write( table.remove(CommandQueue,1) )
        CommunicationTimer:Start(CommandTimeout)
      else
        CommunicationTimer:Stop()
      end
    end
  
    function Disconnected()
      if DebugFunction then print("Disconnected() Called") end
      CommunicationTimer:Stop() 
      CommandQueue = {}
      Heartbeat:Stop()
    end
  
    -- Clear old and open the socket, sending the next queued command
    function Connect()
      if DebugFunction then print("Connect() Called") end
      Samsung:Close()
      Samsung:Open(Baudrate, DataBits, Parity)
    end
  
    -- Handle events from the serial port
    Samsung.Connected = function(serialTable)
      if DebugFunction then print("Connected handler called Called") end
      ReportStatus("OK","")
      Connected()
    end
  
    Samsung.Reconnect = function(serialTable)
      if DebugFunction then print("Reconnect handler called Called") end
      Connected()
    end
  
    Samsung.Data = function(serialTable, data)
      ReportStatus("OK","")
      CommunicationTimer:Stop() 
      CommandProcessing = false
      local msg = DataBuffer .. Samsung:Read(1024)
      DataBuffer = "" 
      if DebugRx then PrintByteString(msg, "Received: ") end
      ParseResponse(msg)
      SendNextCommand()
    end
  
    Samsung.Closed = function(serialTable)
      if DebugFunction then print("Closed handler called Called") end
      Disconnected()
      ReportStatus("MISSING","Connection closed")
    end
  
    Samsung.Error = function(serialTable, error)
      if DebugFunction then print("Socket Error handler called Called") end
      Disconnected()
      ReportStatus("MISSING",error)
    end
  
    Samsung.Timeout = function(serialTable, error)
      if DebugFunction then print("Socket Timeout handler called Called") end
      Disconnected()
      ReportStatus("MISSING","Serial Timeout")
    end
  
    --Serial mode PowerOn handler uses the main api (see network power on below for more fun)
    Controls["PowerOn"].EventHandler = function()
      if DebugFunction then print("PowerOn Serial Handler Called") end
      PowerupTimer:Stop()
      --Documentation calls for 3 commands to be sent, every 2 seconds, for 3 repetitions
      Send( Request["PowerOn"], Controls["Broadcast"].Boolean, true )
      PowerupCount=0
      PowerupTimer:Start(2)
      PowerOnDebounce = true
      Timer.CallAfter( ClearDebounce, PowerOnDebounceTime)
    end
  
    Controls["Reset"].EventHandler = function()
      if DebugFunction then print("Reset handler called Called") end
      PowerupTimer:Stop()
      ClearVariables()
      Disconnected()
      Connect()
    end
    
  
  --  Ethernet Command Function  --
  else
    print("TCP Mode Initializing...")
    IPAddress = Controls.IPAddress
    Port = Controls.Port
    -- Create Sockets
    Samsung = TcpSocket.New()
    Samsung.ReconnectTimeout = 5
    Samsung.ReadTimeout = 10  --Tested to verify 6 seconds necessary for input switches;  Appears some TV behave mroe slowly
    Samsung.WriteTimeout = 10
    udp = UdpSocket.New()
    
    --Send the display the next command off the top of the queue
    function SendNextCommand()
      if DebugFunction then print("SendNextCommand() Called") end
      if CommandProcessing then
        -- Do Nothing
      elseif #CommandQueue > 0 then
        if not Samsung.IsConnected then
          Connect()
        else
          CommandProcessing = true
          if DebugTx then PrintByteString(CommandQueue[1], "Sending: ") end
          Samsung:Write( table.remove(CommandQueue,1) )
        end
      end
    end
  
    function Disconnected()
      if DebugFunction then print("Disconnected() Called") end
      if Samsung.IsConnected then
        Samsung:Disconnect()
      end
      CommandQueue = {}
      Heartbeat:Stop()
    end
  
    -- Clear old and open the socket
    function Connect()
      if DebugFunction then print("Connect() Called") end
      if IPAddress.String ~= "Enter an IP Address" and IPAddress.String ~= "" and Port.String ~= "" then
        if Samsung.IsConnected then
          Samsung:Disconnect()
        end
        Samsung:Connect(IPAddress.String, tonumber(Port.String))
      else
        ReportStatus("MISSING","No IP Address or Port")
      end
    end
  
    -- Handle events from the socket;  Nearly identical to Serial
    Samsung.EventHandler = function(sock, evt, err)
      if DebugFunction then print("Ethernet Socket Handler Called") end
      if evt == TcpSocket.Events.Connected then
        ReportStatus("OK","")
        Connected()
      elseif evt == TcpSocket.Events.Reconnect then
        --Disconnected()
  
      elseif evt == TcpSocket.Events.Data then
        ReportStatus("OK","")
        CommandProcessing = false
        TimeoutCount = 0
        local line = sock:Read(BufferLength)
        local msg = DataBuffer
        DataBuffer = "" 
        while (line ~= nil) do
          msg = msg..line
          line = sock:Read(BufferLength)
        end
        if DebugRx then PrintByteString(msg, "Received: ") end
        ParseResponse(msg)  
        SendNextCommand()
        
      elseif evt == TcpSocket.Events.Closed then
        Disconnected()
        ReportStatus("MISSING","Socket closed")
  
      elseif evt == TcpSocket.Events.Error then
        Disconnected()
        ReportStatus("MISSING","Socket error")
  
      elseif evt == TcpSocket.Events.Timeout then
        TimeoutCount = TimeoutCount + 1
        if TimeoutCount > 3 then
          Disconnected()
          ReportStatus("MISSING","Socket Timeout")
        end
  
      else
        Disconnected()
        ReportStatus("MISSING",err)
  
      end
    end
  
    --Ethernet specific event handlers
    Controls["IPAddress"].EventHandler = function()
      if DebugFunction then print("IP Address Event Handler Called") end
      if Controls["IPAddress"].String == "" then
        Controls["IPAddress"].String = "Enter an IP Address"
      end
      ClearVariables()
      Init()
    end
    Controls["Port"].EventHandler = function()
      if DebugFunction then print("Port Event Handler Called") end
      ClearVariables()
      Init()
    end
  
    -- Get the binary numerical value from a string IP address of the format "%d.%d.%d.%d"
    -- Consider hardening inputs for this function
    function IPV4ToValue(ipString)
      local bitShift = 24
      local ipValue = 0
      for octet in ipString:gmatch("%d+") do
        ipValue = ipValue + (tonumber(octet) << bitShift)
        bitShift = bitShift - 8
      end
      return ipValue or nil
    end
  
    -- Convert a 32bit number into an IPV4 string format
    function ValueToIPV4(value)
      return string.format("%d.%d.%d.%d", value >> 24, (value >> 16) & 0xFF, (value >> 8) & 0xFF, value & 0xFF)
    end
  
    -- Compare IPAddresses as values (32bit integers)
    function IPMaskCheck(ip1, ip2, mask)
      return ip1 & mask == ip2 & mask
    end
  
    -- Accept IPAddresses as strings
    function IsIPInSubnet(ip1, ip2, mask)
      return IPMaskCheck(IPV4ToValue(ip1), IPV4ToValue(ip2), IPV4ToValue(mask))
    end
  
    -- PowerOn command on Ethernet requires a UDP broadcast wake-on-lan packet
    -- The packet needs the MAC of the display to be formed - GetDisplayInfo must be run once to get the MAC first.
    -- If Display is connected WiFi the poweron will not work
    Controls["PowerOn"].EventHandler = function()
      if DebugFunction then print("PowerOn Ethernet Handler Called") end
      --MAC from device is sent as string text, needs translation
      if Controls["MACAddress"].String:len()==12 then
        local mac = ""
        local macstr = Controls["MACAddress"].String
        local localIPAddress = nil
        local broadcastRange = "255.255.255.255"
        local deviceIpValue = IPV4ToValue(IPAddress.String)
        local nics = Network.Interfaces()
  
        --WOL Packet is 6 full scale bytes then 16 repetitions of Device MAC
        for i=1,6 do
          mac = mac..string.char( tonumber( "0x"..macstr:sub((i*2)-1, i*2) ) );  
        end
        local WOLPacket = "\xff\xff\xff\xff\xff\xff"
        for i=1,16 do
          WOLPacket = WOLPacket..mac
        end
  
        -- Check Gateways and generate a broadcast range if it is found to be 0.0.0.0.  This might be better as a property (if user wanted local range for some reason)
        for name,interface in pairs(nics) do
          if interface.Gateway == "0.0.0.0" then
            for _,nic in pairs(nics) do
              local ipValue = IPV4ToValue(nic.Address)
              local maskValue = IPV4ToValue(nic.Netmask or "255.255.255.0")  -- Mask may not be available in emulation mode
              if ipValue & maskValue == deviceIpValue & maskValue then
                localIPAddress = nic.Address
                if nic.BroadcastAddress then
                  broadcastRange = nic.BroadcastAddress
                else
                  broadcastRange = ValueToIPV4((deviceIpValue & maskValue) | (0xFFFFFFFF - maskValue))
                end
                break
              end
            end
            break
          end
        end
  
        --UDP broadcast of the wake on lan packet
        if DebugTx then print("Sending WoL packet UDP:", 9, broadcastRange) end
        udp:Open( localIPAddress )
        udp:Send( broadcastRange, 9, WOLPacket )
        udp:Close()
      end
  
      PowerupTimer:Stop()
      Send( Request["PowerOn"], Controls["Broadcast"].Boolean, true )
      --Also send the MDC command in case of broadcast awake signal
      PowerupCount = 0
      PowerupTimer:Start(2)
      PowerOnDebounce = true
      Timer.CallAfter( ClearDebounce, PowerOnDebounceTime)
    end
  end
  
  
  --  Device Request and Data handlers
  
  --[[ Test the device once for
    0x10: Model Number
    0x67: Device Name
    0x8A: Model Name
    0x0B: Serial Number
    0x0E: SW Revision
  
    TODO: Find a way to test available inputs?
  ]]
  -- Initial data grab from device
  function GetDeviceInfo()
    if DebugFunction then print("GetDeviceInfo() Called") end
    if Properties["Get Device Info"].Value then
      if(Controls["SerialNumber"].String == "") then Send( Request["SerialNumber"] )  end
      if(Controls["DeviceFirmware"].String == "") then Send( Request["SWVersion"] )  end
      if(Controls["ModelNumber"].String == "") then Send( Request["ModelNumber"] )  end
      if(Controls["ModelName"].String == "") then Send( Request["ModelName"] )  end
      if(Controls["DeviceName"].String == "") then Send( Request["DeviceName"] )  end
      if(Controls["MACAddress"].String == "") then Send( Request["MACAddress"] )  end
    end
  end
  
  
  --[[  Response Data parser
    
    All response commands are hex bytes of the format
       Header   Command   DeviceID   DataLength   Ack/Nack   r-Command   Val 1.......   CheckSum
        0xAA     0xFF       0x??      0x??(int)  'A' or 'N'     0x??      0x??0x??...     0x??
  
    Command on a response is always 0xFF
    The Command it is in response to is r-Command
    Val 1 can be a sub command for extended commands
  
    Read until a header is found, then:
      1. Define a data object
      2. Parse the command, deviceID, length, and ack into the structure
      3. Parse the data bytes into an array
      4. Calculate the checksum
  
    Then check for:
      1. correct length
      2. Ack or Nack
      3. Checksum is valid
      4. Push the data object into a handler based on the command
  
    Recursively call if there is more data after the checksum. Stuff incomplete messages in the buffer
  ]]
  function ParseResponse(msg)
    if DebugFunction then print("ParseResponse() Called") end
  
    --Message is too short, buffer the chunk and wait for more
    if msg:len()==0 then 
      --do nothing
    elseif msg:len() < 7 then
      DataBuffer = DataBuffer .. msg
  
    --Message doesn't start at begining.  Find the correct start then parse from there
    elseif msg:byte(1) ~= 170 or msg:byte(2) ~= 255 then
      local i=msg:find( (string.char(170)..string.char(255))  ) 
      if i ~= nil then
        ParseResponse( msg:sub(i,-1) )
      else
        DataBuffer = DataBuffer .. msg
      end
    
    --If the message length field is longer than the buffer, stuff back into the buffer and wait for a complete message
    elseif msg:len() < msg:byte(4)+5 then
      DataBuffer = DataBuffer .. msg
  
    --Handle a good message
    else
      local ResponseObj = {}
      --Pack the data for the handler
      ResponseObj['Command']=msg:byte(6)
      ResponseObj['DeviceId']=msg:byte(3)
      ResponseObj['DataLength']=msg:byte(4)
      ResponseObj['Data']={}
      ResponseObj['CheckSum']=msg:byte( 5+ResponseObj['DataLength'] )
      ResponseObj['CheckSumTotal']=msg:byte(2)+msg:byte(3)+msg:byte(4)+msg:byte(5)+msg:byte(6)
      --Read the data bytes into the data array (Ack/Nack and Cmd are part of the data length)
      if ResponseObj['DataLength']>2 then
        for i=7,(4+ResponseObj['DataLength']) do
          table.insert( ResponseObj['Data'], msg:byte(i) )
          ResponseObj['CheckSumTotal']=ResponseObj['CheckSumTotal']+msg:byte(i)
        end
      end
      -- Message char 5 is an 'A' for ACK;  Otherwise it's a failure response
      if msg:byte(5) ~= 65 then
        --NAK handler
        if DebugRx then print("NAK RESPONSE RECEIVED!") end
        ResponseObj['Ack']=false
      else
        ResponseObj['Ack']=true
      end
  
      --Checksum failures;  Don't handle
      if ResponseObj['CheckSum'] ~= ResponseObj['CheckSumTotal']%256 then
        if DebugRx then print( "Checksum failure: " .. ResponseObj['CheckSum'] .. ' does not match ' .. (ResponseObj['CheckSumTotal']%256) ) end
      else
        HandleResponse(ResponseObj)
      end
  
      --Re-process any remaining data
      ParseResponse( msg:sub(6+ResponseObj['DataLength'],-1) )
    end
  end
  
  -- Handler for good data from interface
  function HandleResponse(msg)
    if DebugFunction then print("HandleResponse() Called") end
    
    --Serial Number
    if msg["Command"]==11 then
      if msg['Ack'] then
        Controls["SerialNumber"].String = ParseString(msg["Data"])
      else
        Controls["SerialNumber"].String = "Unavailable"
      end
  
    --SW Version
    elseif msg["Command"]==14 then
      if msg['Ack'] then
        Controls["DeviceFirmware"].String = ParseString(msg["Data"])
      else
        Controls["DeviceFirmware"].String = "Unavailable"
      end
  
    --Model Number
    elseif msg["Command"]==16 then
      if msg['Ack'] then
        Controls["PanelType"].String = PanelType[ msg["Data"][1] ] or ""
        Controls["ModelNumber"].String = ModelList[ msg["Data"][2] ] or ""
      else
        Controls["PanelType"].String = "Unavailable"
        Controls["ModelNumber"].String = "Unavailable"
      end
  
    --Input source Control response
    elseif msg["Command"]==20 then
      if DebugRx then print("Input Request change received: ",GetInputIndex(msg["Data"][1])) end
      --Don't need to do anything here as status resposne will show when input has changed.
  
    --System configuration
    elseif msg["Command"]==27 then
      --This command has sub commands
      --MAC Address
      if msg['Ack'] then
        if msg["Data"][1]==129 then
          local mac = ""
          for i=1,6 do
            mac = mac .. string.char(msg["Data"][i*2]) .. string.char(msg["Data"][1+i*2]) 
          end
          Controls["MACAddress"].String = mac
        else
          if DebugRx then PrintByteArray(msg["Data"], "Unrecognized System Configuration (0x1B) received: ") end
        end
      else
        Controls["MACAddress"].String = "Unavailable"
      end
  
    --Device Name
    elseif msg["Command"]==103 then
      if msg['Ack'] then
        Controls["DeviceName"].String = ParseString(msg["Data"])
      else 
        Controls["DeviceName"].String = "Unavailable"
      end
    
    --Model Name
    elseif msg["Command"]==138 then
      if msg['Ack'] then
        Controls["ModelName"].String = ParseString(msg["Data"])
        PluginInfo.Model = Controls["ModelName"].String
      else
        Controls["ModelName"].String = "Unavailable"
      end
    
    -- Catch NACK responses that aren't handled
    elseif not msg["Ack"] then
      print("Nack response received for command "..msg["Command"])
  
    --Handle Status command
    elseif msg["Command"]==0 then
      SetPowerLevel( msg["Data"][1] )
      Controls["Volume"].Value = msg["Data"][2]
      Controls["Mute"].Value = msg["Data"][3]
      SetActiveInput( GetInputIndex(msg["Data"][4]) )
  
    --Power Status
    elseif msg["Command"]==17 then
      SetPowerLevel( msg["Data"][1] )
      
    --Mute Status
    elseif msg["Command"]==19 then
      Controls["Mute"].Value = msg["Data"][1]
  
    --Handle Anything else by printing the unexpected command (debug?)
    else
      if DebugRx then 
        print("Unexpected Data received.  Command: "..msg["Command"])
        PrintByteArray( msg["Data"] ) 
      end
    end
  end
  
  --[[    Input Handler functions      ]]
  
  -- Re-Initiate communication when the user changes the IP address or Port or ID being queried
  Controls["DisplayID"].EventHandler = function()
    if DebugFunction then print("Port Event Handler Called") end
    ClearVariables()
    Init()
  end
  
  --Controls Handlers
  -- Power controls
  Controls["PowerOff"].EventHandler = function()
    if DebugFunction then print("PowerOff Handler Called") end
    -- Stop the power on sequence if the user presses power off
    PowerupTimer:Stop()
    CommandQueue = {}
    Controls["PowerStatus"].Value = 0
    Send( Request["PowerOff"], Controls["Broadcast"].Boolean, true )
  end
  Controls["Reboot"].EventHandler = function()
    if DebugFunction then print("Reboot Handler Called") end
    Send( Request["Reboot"], Controls["Broadcast"].Boolean  )
  end
  
  -- Input controls
  for i=1,InputCount do
    Controls['InputButtons'][i].EventHandler = function(ctrl)
      if DebugFunction then print("Input Handler Called") end
      if ctrl.Boolean then
        Request["InputSet"]["Data"][1] = InputTypes[i].Value
        Send( Request["InputSet"], Controls["Broadcast"].Boolean  )
      end
    end
  end
  Controls['InputNext'].EventHandler = function()
    if DebugFunction then print("Input Handler Called") end
    i = GetInputIndex( Request["InputSet"]["Data"][1] )
    if InputTypes[i+1] ~= nil then
      Request["InputSet"]["Data"][1] = InputTypes[i+1].Value
    else
      Request["InputSet"]["Data"][1] = InputTypes[1].Value
    end
    Send( Request["InputSet"], Controls["Broadcast"].Boolean  )
  end
  
  -- Sound Controls
  Controls["Mute"].EventHandler = function(ctrl)
    if DebugFunction then print("Mute Handler Called") end
    if ctrl.Value == 1 then
      Send( Request["MuteOn"], Controls["Broadcast"].Boolean  )
    else
      Send( Request["MuteOff"], Controls["Broadcast"].Boolean  )
    end
  end
  Controls["VolumeUp"].EventHandler = function()
    if DebugFunction then print("VolumeUp Handler Called") end
    Send( Request["VolumeUp"], Controls["Broadcast"].Boolean  )
  end
  Controls["VolumeDown"].EventHandler = function()
    if DebugFunction then print("VolumeDown Handler Called") end
    Send( Request["VolumeDown"], Controls["Broadcast"].Boolean  )
  end
  VolumeDebounce.EventHandler = function()
    if DebugFunction then print("VolumeDebounce Handler Called") end
    Request["VolumeSet"]["Data"][1] = math.floor(Controls["Volume"].Value)
    Send( Request["VolumeSet"], Controls["Broadcast"].Boolean  )
    VolumeDebounce:Stop()
  end
  Controls["Volume"].EventHandler = function(ctrl)
    if DebugFunction then print("Volume Handler Called") end
    VolumeDebounce:Start(.500)
  end
  
  -- Timer EventHandlers  --
  Heartbeat.EventHandler = function()
    if DebugFunction then print("Heartbeat Event Handler Called") end
    Send( Request["PowerStatus"] )
    if Controls["PowerStatus"].Value==1 then
      Send( Request["Status"] )
      GetDeviceInfo()
    end
  end 
  
  
  -- PowerOn command requires spamming the interface 3 times at 2 second intervals
  PowerupTimer.EventHandler = function()
    if Controls["PowerStatus"].Value == 1 then
      PowerupTimer:Stop()
    else
      Send( Request["PowerOn"], Controls["Broadcast"].Boolean, true )
      PowerupCount= PowerupCount + 1
      if PowerupCount>2 then
        PowerupTimer:Stop()
      end
    end
  end
  
  -- Kick it off
  SetupDebugPrint()
  Init()
  
  
  
  --[[ Additional Notes:
    Commands of interest but not used here
        0x01: Clock
        0x02: On time
        0x03: Off time
        0xA4 - 0xAE:  Timer controls
        0x09: Sound
        0x0D: Display Status
        0x4A: Standby state
        0xF9: Panel On/Off?  May be an integral part of multi-LCD panel dispays
        0x07: PiP Control
        0x04: Video Control for analog sources    (HSV etc)
        0x06: Video Control for digital sources   (RGB etc)
        0x16: Tuner control (analog TV)
        0x17: Tuner control (digital TV)
        0x61: Channel Up/Down
        0x85: Temperature
        0x1c: MagicInfo controls  (Samsung content feed)
        0xB4: Screen Mute
  ]]
end