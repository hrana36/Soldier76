Download script
Choose a version and download , domestic players recommend using mirror download
If you use a mirror to download, please pay attention to whether the version number is the same as that on github. The mirror project is not necessarily the latest version because it needs to be updated manually.
Installation tutorial
Start Logitech Drive as an administrator
Please make sure that the driver you download matches your operating system
Currently it does not support GHUBthe new drive, relevant information go to forums to understand.
Opened automatic game detection
The advantage of this is that it can prevent the script from accidentally interfering with normal operations
Try not to lock the configuration, because your scripts are running all the time after locking, which may interfere with the normal use of your mouse
Scan game
If the game cannot be found by automatic detection, you need to add it manually
The trick to add manually is to open the task manager, find the game process, right-click and select the location of the file to open, and you can find the file you need to add
Right-click the PUBG icon on the right side of the configuration file -> write script
After the previous step, will be more out of a pubg icon, this icon will be able to find the right scripting the
The Soldier76.lua all code contained completely covered in, save (Ctrl + S)
Cover, opens scripting , the generated code does not retain the original
Be careful not to use translation software to translate scripts, translation software will destroy the code format and cause errors
Right PUBG configuration and the default configuration of the G6 , G7 , G8 , G9 , G10 , G11 and other button -> unassigned
The current configuration and onboard macros have a default key bindings configuration may interfere with the normal use of the script, so it should be unassigned
Game settings
The script default settings AimingSettings = "recommend", that is, the script recommended settings, need to make corresponding changes to the in-game settings
Open the mirror: long press the right button
Aim: When autoPressAimKey = ""the time, press ctrl the key
If the habit game default setting, the setting AimingSettings = "default", then you may not need to change any game settings
With this setting, any of your clicks will be recognized as shooting, and an automatic gun will be triggered
If you just want to perform click operations, you need to close the script, or temporarily hold down the left shift or left alt.
If you compare different operating habits, you can also customize settingsAimingSettings = "custom"
This setting is needed customAimingSettingsto make the determination in the corresponding
It is recommended to use the script after you have some knowledge of the script, or you can join the exchange group for help
The latest version of the script to increase automatically waist shot feature, set autoPressAimKey = "tilde"to open
It needs to be set as a key on the keyboard. For the key name, please refer to the G-series Lua API reference document.docx
To close, please set autoPressAimKey = ""
This feature is not compatible AimingSettings = "default"
Compatible AimingSettings = "recommend"by default , but it will affect normal click operations, please close the script when you need to click, or temporarily hold down the left shift or left alt key
Compatible AimingSettings = "custom", you need to make compatible settings yourself
parameter	description
default	Use the initial default settings of the game, that is, right-click to open the mirror, and long-click to aim. (You need to hold down the left shift when you simply click.)
recommend	The recommended setting for using this script is to press and hold the right button to open the mirror and press and hold the left ctrl to aim. (The script uses this setting by default)
ctrlmode	In this mode, you need to modify the game settings to quickly open the mirror, and squat down when you hold down ctrl. (There is no waist shot in this mode)
custom	Custom settings, using customAimingSettingsthe determination condition set.
Start control
Modification startControl = "capslock"may be used in different ways control macros open (off)

parameter	description
capslock	Use caps lock key control. (Default, recommended)
numlock	Keypad lock key control.
G_bind	Use offinstructions to turn off the macro, any switching operations can be opened macro firearms.
Mode control
button	Features
CapsLock	Open capital letters key to start the macro, close the lock macro will not respond to pressing the left button to perform the operation when the gun is closed, but the G_bindcommand is still valid (Note: can be changed to other control methods, see # launch control )
ScrollLock	Developers debug mode is turned on, the sight automatically pull to the right (after opening attempts to modify the ADSvalue of the trajectory becomes word)
First use
Follow the #installation tutorial installation script
Then change the in-game settings, refer to #游戏SET
Modify the script canUsein firearms, set the UMP45mode to 1 , all other firearms mode is set to 0 . (During automatic game detection, switching windows will cause the script to restart. Therefore, the location information of the last configuration table will not be recorded. Limiting the available firearms to 1 is good for debugging. You can also choose to keep other guns, any gun Yes. )
Enter the training ground and follow the notes to install the specified accessories for the gun.
Turn on the gun function (reference for startup method startControl) and debugging mode ScrollLock, face the wall, press and hold the right button to open the mirror, press and hold the left button to fire, you will find that the front sight automatically shifts to the right , please do not move the mouse until the bullets are lit.
If a horizontal line is not printed projectile, modify the ADSvalue, down to fine-tune.
Go back to the game and feel the ballistic changes, repeat the above modification operations, and keep trying until the ballistic becomes a horizontal line.
If the value cannot be turned into a horizontal line no matter how you modify it, please try to slightly adjust the mouse sensitivity in the game.
When the trajectory is successfully drawn into a horizontal line, turn off the debugging mode ScrollLock, and then shoot at the wall again. If there are no accidents, congratulations, your macro has been able to automatically press the gun accurately!
Trimming Aim, scopeX2, scopeX3, scopeX4, scopeX6the value of the waist shot, twice, three times, four times, six times when the pressure gun shells printed in one place. You can skip this step if you don't need the multiplying gun function.
Modify the script canUseof firearms, you will need to firearms is set to mode 1
ctrl+s After saving the script, you can try to switch the configuration in the editor. When the configuration is switched, the corresponding text information will be output. You can confirm here whether it is the same as the configuration information you expect.
The last step is to find teammates, and then play hard~
* Pay attention to the comments in the code. The player custom area and the script core area have been clearly marked. Please do not modify the code in the script core area.

Other settings (not necessary)
Even point function Please canUseset
Please independent factor in canUsesetting
Please squat independent factor in canUsesetting
Extended development tutorial: add a new firearm/modify the data of a firearm
Extended development tutorial: Set custom targeting judgment conditions
What is a switch configuration?
Many people don't figure out what switching means. This is what makes our script unique.

There is a firearms library in this script, which is divided into different series according to the bullet type, including: .45 series, 9mm series, 5.56 series and 7.62 series. Each series stores firearms with matching ammunition types. For example, the first gun in the 5.56 series is the M416 . There are 4 keys in G6-G9 , and each key represents a series. After clicking, it will switch to the firearm list of the corresponding series, and automatically select the first gun in the list. Press the G11 key several times to select the gun downwards. If you need the last gun in the series, just press G10 once.

For example: if you have picked up an AKM , you only need to click the G8 button to do it, because AKM is the first gun in the 7.62 series. If you find another QBZ and you don’t need your AKM , you need to click on G6 first . When switching to the 5.56 series, the first gun is selected by default, and QBZ is the third one, so you have to Press G11 twice so that you can use the QBZ data.

Please check the order of firearms in the source code. The userInfo.canUsearrangement order is the order of firearms.

The above G-key functions can be customized, the default is g502 settings, other logitech series programmable mice are also supported. If you don’t know how to set and adjust, please join the group and ask us.

G key function (default setting)
G key	Features
G6	Switch to the 5.56 firearms configuration file table and use the first configuration
G7	Switch to the 9mm gun configuration file table and use the first configuration
G8	Switch to the 7.62 firearms configuration file table and use the first configuration
G9	Switch to the .45 firearm profile table and use the first profile
G10	Switch to the last configuration (wheel to the right)
G11	Switch to the next configuration (wheel left)
Above can be provided in G_binda custom modification keys in

Instruction list
instruction	Features
.45	Switch to the .45 series firearms list and use the first gun in the list
9mm	Switch to the list of 9mm series guns and use the first gun in the list
5.56	Switch to the 5.56 series firearms list and use the first gun in the list
7.62	Switch to the 7.62 series of firearms list and use the first gun in the list
first	Switch to the first gun in the current list
next	Switch to the next gun in the current list
last	Switch to the last gun in the current list
first_in_canUse	The canUseall considered as a whole list of available arms, and switching to the first list of the gun
next_in_canUse	The canUseall available firearms deemed a whole list, and switch to a gun under the list
last_in_canUse	The canUseall available firearms deemed a whole list, a gun and switch to the last of the list
off	As startControl = "G_bind"when using the command control script is closed, the switching operation of firearms will re-start the macro
scopeX1	Switch to basic sight mode (red dot, holographic, side sight or without any sights)
scopeX2	Switch to double lens mode
scopeX3	Switch to triple lens mode
scopeX4	Switch to quadruple lens mode
scopeX6	Switch to 6x lens mode
UMP45	Switch directly to the UMP45configuration
Tommy Gun	Switch directly to the Tommy Gunconfiguration
Vector	Switch directly to the Vectorconfiguration
Micro UZI	Switch directly to the Micro UZIconfiguration
M416	Switch directly to the M416configuration
SCAR-L	Switch directly to the SCAR-Lconfiguration
QBZ	Switch directly to the QBZconfiguration
G36C	Switch directly to the G36Cconfiguration
M16A4	Switch directly to the M16A4configuration
AKM	Switch directly to the AKMconfiguration
Beryl M762	Switch directly to the Beryl M762configuration
DP-28	Switch directly to the DP-28configuration
fast_pickup	One-click pickup (use after closing the backpack)
fast_discard	One-click discard (use after closing the backpack)
fast_lick_box	One-click bag licking (use after closing the backpack, only pick up items that can be loaded into the backpack)
Can be bound to G_bind, use the preset key combination to trigger instructions. Note: The instruction is bound to the combination key, not the combination key to the instruction. Please do not modify [""]the content before the equal sign !

G_bind Instruction binding demo
- G 
[ " G3 " ] =  " " ,
[ " G4 " ] =  " " ,
[ " G5 " ] =  " " ,
[ " G6 " ] =  " 5.56 " ,
[ " G7 " ] =  " 9mm " ,
[ " G8 " ] =  " 7.62 " ,
[ " G9 " ] =  " .45 " ,
[ " G10 " ] =  " last " ,
[ " G11 " ] =  " next " ,

- ✖, wrong modification method 
[ " G3 " ] =  " " ,
[ " G4 " ] =  " " , - the following will be covered by the G4 G4, lost G6, G6 press to be wrong. 
[ " G5 " ] =  " " ,
[ " G4 " ] =  " 5.56 " , - Never directly modify the key combination in front of the equal sign! 
[ " G7 " ] =  " 9mm " ,
[ " G8 " ] =  " 7.62 " ,
[ " G9 " ] =  " .45 " ,
[ " G10 " ] =  " last " ,
[ " G11 " ] =  " next " ,

- ✔, the correct way to modify 
[ " G3 " ] =  " " ,
[ " G4 " ] =  " 5.56 " , - bind the command here 
[ " G5 " ] =  " " ,
[ " G6 " ] =  " " , - This command is cleared 
[ " G7 " ] =  " 9mm " ,
[ " G8 " ] =  " 7.62 " ,
[ " G9 " ] =  " .45 " ,
[ " G10 " ] =  " last " ,
[ " G11 " ] =  " next " ,

- The v4.4 version adds support for binding a set of commands, separated by | 
[ " rctrl + G5 " ] =  " M416|scopeX1 " ,
[ " rctrl + G6 " ] =  " AKM|scopeX4 " ,
Hardware condition
A programmable Logitech mouse (the wireless mouse is very unstable when running macros)
The game screen does not freeze, does not frequently drop frames, if necessary, you can lock the number of frames to ensure stability
Disclaimer
The script program is for learning and communication only, and it is strictly prohibited to use it for any commercial purposes. If there is a dispute of interest, it will not be held responsible.
Please respect the author's labor achievements, if you need to reprint, please indicate the source, thank you!
Do not use this script for commercial purposes after the second creation!
Exchange group
Welcome to join the technical exchange QQ group: Logitech mouse macro technology exchange( 768483124 )
Very welcome friends who are willing to fine-tune the trajectory of this project
We also welcome friends from other projects to settle in and exchange technical topics together
common problem
Q: No response?
A1: Please exclude wireless mouse and GHUB first
A2: Please confirm whether you have activated the macro (capitalization is enabled by default)
Q: There is a reaction on the desktop, but no reaction in the game?
A: Close the driver, restart the driver as an administrator
Q: The comments in the code are all garbled?
A1: Your driver may be GHUB, it is currently not supported
A2: You may use the 导入function, luathe file is copied and pasted directly into the editor can not be used导入
Q: The tip of the gun hits the ground directly, even if you can't pull it up?
A: Adjust ADS (If you have this question, you must have not read the above tutorial)
feedback
Have any questions about using scripts, or there is a script deficiencies can Issuesgive me feedback
About Macro
Macro is like a blind man with ingenuity. It can help you do more complicated and delicate operations, but it cannot be modified according to the real-time situation, so the dishes are still authentic...

Regarding game fairness
I agree with @liantian-cn 's point of view.

Is it unfair to use a 4,000 yuan monitor to win a 400 yuan opponent? Winning a graphics card with 10,000 yuan is a 1,000 yuan opponent. Does anyone say that it is unfair? Why is it that using a mouse with a few hundred dollars to beat the mouse is an opponent of dozens of dollars, and some people say it is unfair and cheating?

Obviously a good monitor and a good graphics card have a greater impact on the level of the game than a mouse macro. Why is it that the mouse macro is unfair?

Kong Jing will say that you can use a few hundred dollars of the mouse, the mouse provides you with macro functions, but you have the right not to use it. So I can also say that 4000 monitors give you a display resolution of 144Hz and 2K or even 4K, and you have the right not to use it. You can change it back to 60Hz and 1080p, and the graphics card is the same.

Out of some people's prejudice, I have to make this clear. The mouse macro is not guilty, and the dish is the original sin. Those who think that others use the mouse macro to ruin your gaming experience, please answer after you have tried the mouse macro. It is not as divine as you imagine.

The mouse macro is just an auxiliary wheel when you learn to bike . After you learn it, you only want to remove it. It's that simple.
