# Custom-Cover-Script
This is the script integration of this mod: [Asaayu's Custom Cover Mod](https://steamcommunity.com/sharedfiles/filedetails/?id=1618663060)
If you would like to support me and my endevors feel free to [donate](https://www.paypal.me/asaayu) any support is appreacted. 

# Installation
Make sure to add the CfgCustomCover to your description.ext or else the script won't work. This is the bit that you can edit to your liking.
```c++
class CfgCustomCover
{
 startCredits = 15;
 //== Number of credits per player when they join the mission

 items[] = {{"Land_BagFence_End_F",1},{"Land_BagFence_Corner_F",2},{"Land_BagFence_Long_F",4},{"Land_BagFence_Round_F",4},{"Land_BagFence_Short_F",2},{"Land_BagFence_01_end_green_F",1},{"Land_BagFence_01_corner_green_F",2},{"Land_BagFence_01_long_green_F",4},{"Land_BagFence_01_round_green_F",4},{"Land_BagFence_01_short_green_F",2},{"Land_SandbagBarricade_01_half_F",5},{"Land_SandbagBarricade_01_F",10},{"Land_SandbagBarricade_01_hole_F",9},{"Land_Plank_01_4m_F",1}};
 //== Use an array with the item & the credit cost eg. {"item_className",3}

 allowPlacedItemPickup = 1;
 //== 1- Any object placed in the mission and is in the list can be collected for credits
 //== 0 - Only player placed items can be collected for credits
};
```

Then add the following to your description.ext to add the dialogs
```c++
#include "Custom-Cover-Script\dialog\defines.hpp"
#include "Custom-Cover-Script\dialog\menu.hpp"
``` 

Then if your description.ext already contains CfgFunctions then just add the following to your CfgFunctions
```c++
class customCover
	{
		class Dialog
		{
			file = "Custom-Cover-Script\Dialog\Functions";
			class dialogFadeIn {};
			class menuInit {};
			class transferInit {};
		};
		class Interaction
		{
			file = "Custom-Cover-Script\Functions\Interaction";
			class transferCredits {};
		};
		class Place
		{
			file = "Custom-Cover-Script\Functions\Place";
			class placeItem {};
		};
	};
```

If you don't already have a CfgFunctions then add this
```c++
class CfgFunctions
{
	class customCover
	{
		class Dialog
		{
			file = "Custom-Cover-Script\Dialog\Functions";
			class dialogFadeIn {};
			class menuInit {};
			class transferInit {};
		};
		class Interaction
		{
			file = "Custom-Cover-Script\Functions\Interaction";
			class transferCredits {};
		};
		class Place
		{
			file = "Custom-Cover-Script\Functions\Place";
			class placeItem {};
		};
	};
};
```

Then copy over the Custom-Cover-Script folder and make sure it includes the init.sqf file.

IF YOU WHITELIST REMOTEXECS MAKE SURE TO WHITELIST "customCover_fnc_transferCredits" TO ALLOW PLAYERS TO TRANSFER CREDITS!

Then your good to go!
