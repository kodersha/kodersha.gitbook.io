---
icon: dove
layout:
  width: default
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: false
  metadata:
    visible: true
---

# Windhawk

<figure><img src="../.gitbook/assets/Desktop.png" alt=""><figcaption></figcaption></figure>



### Windows 11 Taskbar Styler

```json
{
  "controlStyles[0].target": "Taskbar.TaskbarFrame#TaskbarFrame",
  "controlStyles[0].styles[1]": "HorizontalAlignment=Center",
  "controlStyles[0].styles[2]": "Width=Auto",

  "controlStyles[1].target": "Taskbar.TaskbarFrame#TaskbarFrame > Grid#RootGrid",
  "controlStyles[1].styles[0]": "Padding=6,0,6,0",
  "controlStyles[1].styles[1]": "Margin=10,2,10,3",
  "controlStyles[1].styles[2]": "BorderThickness=1",
  "controlStyles[1].styles[3]": "BorderBrush:=<SolidColorBrush Color=\"{ThemeResource SurfaceStrokeColorDefault}\" Opacity=\".55\" />",
  "controlStyles[1].styles[4]": "CornerRadius=15",
  "controlStyles[1].styles[5]": "Background:=<AcrylicBrush TintColor=\"{ThemeResource CardStrokeColorDefaultSolid}\" FallbackColor=\"{ThemeResource CardStrokeColorDefaultSolid}\" TintOpacity=\"0\" TintLuminosityOpacity=\".45\" Opacity=\"1\"/>",

  "controlStyles[2].target": "Rectangle#BackgroundFill",
  "controlStyles[2].styles[0]": "Visibility=Collapsed",

  "controlStyles[3].target": "Rectangle#BackgroundStroke",
  "controlStyles[3].styles[0]": "Visibility=Collapsed",

  "controlStyles[4].target": "Taskbar.AugmentedEntryPointButton#AugmentedEntryPointButton > Taskbar.TaskListButtonPanel#ExperienceToggleButtonRootPanel",
  "controlStyles[4].styles[0]": "Margin=0",

  "controlStyles[5].target": "Grid#SystemTrayFrameGrid",
  "controlStyles[5].styles[0]": "Background:=#00000000",
  "controlStyles[5].styles[1]": "CornerRadius=5",
  "controlStyles[5].styles[2]": "BackgroundSizing=InnerBorderEdge",
  "controlStyles[5].styles[3]": "Margin=0,2,0,3",
  "controlStyles[5].styles[4]": "BorderThickness=5",

  "controlStyles[6].target": "SystemTray.ChevronIconView",
  "controlStyles[6].styles[0]": "Padding=0",

  "controlStyles[7].target": "SystemTray.NotifyIconView#NotifyItemIcon",
  "controlStyles[7].styles[0]": "Padding=0",

  "controlStyles[8].target": "SystemTray.OmniButton",
  "controlStyles[8].styles[0]": "Padding=0",

  "controlStyles[9].target": "SystemTray.CopilotIcon",
  "controlStyles[9].styles[0]": "Padding=0",

  "controlStyles[10].target": "SystemTray.OmniButton#NotificationCenterButton > Grid > ContentPresenter > ItemsPresenter > StackPanel > ContentPresenter > systemtray:IconView#SystemTrayIcon > Grid",
  "controlStyles[10].styles[0]": "Padding=0,0,0,0",

  "controlStyles[11].target": "SystemTray.IconView#SystemTrayIcon > Grid#ContainerGrid > ContentPresenter#ContentPresenter > Grid#ContentGrid > SystemTray.TextIconContent > Grid#ContainerGrid",
  "controlStyles[11].styles[0]": "Padding=0",

  "controlStyles[12].target": "SystemTray.StackListView#IconStack > ItemsPresenter > StackPanel > ContentPresenter > SystemTray.IconView#SystemTrayIcon",
  "controlStyles[12].styles[0]": "Padding=0",

  "controlStyles[13].target": "SystemTray.Stack#ShowDesktopStack",
  "controlStyles[13].styles[0]": "Margin=20,0,0,0",

  "controlStyles[14].target": "Taskbar.Gripper#GripperControl",
  "controlStyles[14].styles[0]": "Width=Auto",
  "controlStyles[14].styles[1]": "MinWidth=24"
}
```



### Windows 11 Start Menu Styler <a href="#windows-11-start-menu-styler" id="windows-11-start-menu-styler"></a>

```json
{
  "theme": "Windows11_Metro10Minimal",
  "disableNewStartMenuLayout": 0,

  "controlStyles[0].target": "",
  "controlStyles[0].styles[0]": "",

  "webContentStyles[0].target": "",
  "webContentStyles[0].styles[0]": "",

  "webContentCustomJs": "",

  "styleConstants[0]": "",

  "resourceVariables[0].variableKey": "",
  "resourceVariables[0].value": ""
}
```



### Windows 11 File Explorer Styler <a href="#windows-11-file-explorer-styler" id="windows-11-file-explorer-styler"></a>

```json
{
  "theme": "MicaBar",

  "controlStyles[0].target": "",
  "controlStyles[0].styles[0]": "",

  "styleConstants[0]": "",

  "resourceVariables[0].variableKey": "",
  "resourceVariables[0].value": "",

  "explorerFrameContainerHeight": 0
}
```



### Taskbar height and icon size

```json
{
  "IconSize": 22,
  "TaskbarHeight": 56,
  "TaskbarButtonWidth": 46
}
```



### Taskbar tray system icon tweaks

```json
{
  "hideVolumeIcon": 0,
  "hideNetworkIcon": 0,
  "hideBatteryIcon": 0,
  "hideMicrophoneIcon": 0,
  "hideGeolocationIcon": 0,
  "hideStudioEffectsIcon": 0,
  "hideLanguageBar": 0,
  "hideLanguageSupplementaryIcons": 0,
  "hideBellIcon": "always",
  "showDesktopButtonWidth": 0
}
```



### Taskbar Clock Customization

```json
{
  "ShowSeconds": 1,
  "TimeFormat": "HH':'mm",
  "DateFormat": "ddd','  dd MMMM",
  "WeekdayFormat": "dddd",
  "WeekdayFormatCustom": "Sun, Mon, Tue, Wed, Thu, Fri, Sat",
  "TopLine": "%time%",
  "BottomLine": "%date%",
  "MiddleLine": "",
  "TooltipLine": "",

  "Width": 180,
  "Height": 60,
  "MaxWidth": 0,
  "TextSpacing": 0,

  "DataCollection.NetworkMetricsFormat": "mbs",
  "DataCollection.NetworkMetricsFixedDecimals": -1,
  "DataCollection.PercentageFormat": "spacePaddingAndSymbol",
  "DataCollection.UpdateInterval": 1,

  "WebContentWeatherLocation": "",
  "WebContentWeatherFormat": "",
  "WebContentWeatherUnits": "autoDetect",

  "WebContentsItems[0].Url": "https://rss.nytimes.com/services/xml/rss/nyt/World.xml",
  "WebContentsItems[0].BlockStart": "<item>",
  "WebContentsItems[0].Start": "<title>",
  "WebContentsItems[0].End": "</title>",
  "WebContentsItems[0].ContentMode": "xmlHtml",
  "WebContentsItems[0].SearchReplace[0].Search": "",
  "WebContentsItems[0].SearchReplace[0].Replace": "",
  "WebContentsItems[0].MaxLength": 28,
  "WebContentsUpdateInterval": 10,

  "TimeZones[0]": "Eastern Standard Time",

  "TimeStyle.Hidden": 0,
  "TimeStyle.TextColor": "",
  "TimeStyle.TextAlignment": "",
  "TimeStyle.FontSize": 0,
  "TimeStyle.FontFamily": "",
  "TimeStyle.FontWeight": "",
  "TimeStyle.FontStyle": "",
  "TimeStyle.FontStretch": "",
  "TimeStyle.CharacterSpacing": 0,

  "DateStyle.Hidden": 0,
  "DateStyle.TextColor": "",
  "DateStyle.TextAlignment": "",
  "DateStyle.FontSize": 0,
  "DateStyle.FontFamily": "",
  "DateStyle.FontWeight": "",
  "DateStyle.FontStyle": "",
  "DateStyle.FontStretch": "",
  "DateStyle.CharacterSpacing": 0,

  "oldTaskbarOnWin11": 0
}
```



### Slick Window Arrangement

```json
{
  "SnapWindowsWhenDragging": 1,
  "SnapWindowsDistance": 10,

  "KeysToDisableSnapping.Ctrl": 0,
  "KeysToDisableSnapping.Alt": 1,
  "KeysToDisableSnapping.Shift": 0,

  "SlidingAnimation": 0,
  "SnapWindowsWhenSliding": 1,
  "SlidingAnimationSlowdown": 15
}
```
