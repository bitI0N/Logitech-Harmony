# IPSymconHarmony
[![Version](https://img.shields.io/badge/Symcon-PHPModul-red.svg)](https://www.symcon.de/service/dokumentation/entwicklerbereich/sdk-tools/sdk-php/)
[![Version](https://img.shields.io/badge/Symcon%20Version-5.0%20%3E-green.svg)](https://www.symcon.de/forum/threads/37412-IP-Symcon-5-0-%28Testing%29)

Module for IP Symcon Version 5 and higher. Enables communication with a Logitech Harmony Hub and sending commands through the Logitech Harmony Hub.

## Documentation

**Table of Contents**

1. [Features](#1-features)
2. [Requirements](#2-requirements)
3. [Installation](#3-installation)
4. [Function reference](#4-functionreference)
5. [Configuration](#5-configuration)
6. [Annex](#6-annex)

## 1. Features

With the help of the Logitech Harmony Hub devices can be operated, which are otherwise controllable via IR remote controls or even newer devices such as FireTV and AppleTV which are controlled via Bluetooth.
For more information about controllable devices through the Logitech Harmony Hub, see [Logitech Harmony Elite](https://www.logitech.com/de-de/product/harmony-elite "Logitech Harmony Elite")

Using the module, the devices stored in the Logitech Harmony Hub can be imported into IP-Symcon and then switched from IP-Symcon via the Logitech Harmony Hub.
Harmony activities can be started from IP-Symcon. When the Harmony Hub performs an activity, the current running activity is submitted to IP-Symcon.

### send IR Code :  

 - Send an IR signal through the Logitech Harmony Hub to the hub known devices 

### FireTV:  (Bluetooth)

 - Sending commands to a FireTV   

### Show current activity:  

 - Shows the current active Harmony Hub activity 
 
### Start an activity:  

 - Starts an activity of the Harmony Hub  
	  
## 2. Requirements

- IPS 5.x.
- Logitech Harmony Hub on the same network as IP Symcon

## 3. Installation

### a. Loading the module

Open the IP Console's web console with _http: // <IP-Symcon IP>: 3777 / console / _.

Then the object tree _Open_.

![Objektbaum](img/objektbaum.png?raw=true "Objektbaum")	

Open the instance _'Modules'_ below core instances in the object tree of IP-Symcon (>= Ver 5.x) with a double-click and press the _Plus_ button.

![Modules](img/Modules.png?raw=true "Modules")	

![Plus](img/plus.png?raw=true "Plus")	

![ModulURL](img/add_module.png?raw=true "Add Module")
 
Enter the following URL in the field and confirm with _OK_:


```	
https://github.com/Wolbolar/IPSymconNEEO  
```
    
and confirm with _OK_.    
    
Then an entry for the module appears in the list of the instance _Modules_

### b. Configuration in IPS

If scripts are to be created, they will be placed below a category. First, we create a category in the object tree _right mouse button -> add object -> category_, which we give an arbitrary name such as. _**Harmony devices**_.
Later, all scripts for devices of the Logitech Harmony Hub will be created under this category.

Then add an instance in IP-Symcon 5.x under splitter.

![Add_Splitter](img/add_splitter.png?raw=true "Add Splitter")

Here as manufacturer enter _Logitech_ and select _Logitech Harmony Hub_.

![Add Logitech Hub](img/add_splitter_1.png?raw=true "Add Logitech Hub")


In the window that opens, first select the following items during initial installation:

![Logitech Hub 1](img/logitech_hub_1.png?raw=true "Logitech Hub 1")


**1.** put slider on active. This is necessary for the I / O instance to be active later.

**2.** Enter the IP address of the Logitech Harmony Hub

**3.** Email address (corresponds to login name) for MyHarmony

**5.** MyHarmony password

**6.** Then press _ÄNDERUNGEN ÜBERNEHMEN_ .

![Accept Changes](img/Accept_Changes.png?raw=true "Accept Changes")

**7.** Select _Konfiguration auslesen_ and wait a few seconds.

![Logitech Hub 2](img/logitech_hub_2.png?raw=true "Logitech Hub 2")

**8.** After the _Harmony Config_ variable has been updated, press _Setup Harmony_, then the instance can be closed.

Then a configurator is created.

![Konfigurator 1](img/konfigurator_1.png?raw=true "Konfigurator 1")

![Konfigurator 2](img/konfigurator_2.png?raw=true "Konfigurator 2")

The configurator now offers the following options:

![Konfigurator 3](img/konfigurator_3.png?raw=true "Konfigurator 3")


- _Kategorie Harmony Skripte_ is the category under which scripts are created
- _Harmony Variablen_ if not active only the instance is created, but scripts can still be used. Activate to switch over variables in the web front. _Attention! Many devices can consume many variables_.
  _Optional_ If this option is selected, a variable for switching from the web front will be created for each command group of a Logitech Harmony device. **CAUTION:** This option should **only be selected if there are still enough variables available in IP-Symcon** or the number of variables is unlimited, as a large number of variables can be consumed depending on the devices learned in the Harmony Hub. Every Harmony Hub device creates a variable for switching in the web front for each Controllgroup stored in the Harmony Hub. Depending on the number of devices configured in the Harmony Hub, a large number of variables may be generated here.
  The option is intended for IP Symcon users who still have enough variables available and want to drop commands from the web front.	
- _Harmony Skript_ If this is activated, the associated scripts will be created for each already created instance with _Setup Harmony_.
  _Optional_ This option can be chosen as an alternative or addition to variables. A subcategory with scripts is created for each Controllgroup stored in the Harmony Hub.
  The single script then sends the respective command (script name) to the Logitech Harmony Hub.

If something has been changed in the configuration in the Harmony Hub, press _Konfiguration auslesen_ and press _Liste aktualisieren_.
Individual devices can now be selected in the configurator and _Create_ creates the device in IP-Symcon.


![Konfigurator 4](img/konfigurator_4.png?raw=true "Konfigurator 4")

Mit _Setup Harmony_ , scripts are created for each device created in IP Symcon, depending on the settings (see above), and scripts are generated for the activities.

### Webfront Screen

![Webfront](img/Webfront.png?raw=true "Webfront")

You can then send commands via the web front or the scripts. The activity is displayed on the web front.
Once a device or Harmony Remote triggers a Harmony Activity, it will also be updated in IP Symcon.
The current activity is displayed in the variable Harmony Activity, which is located under the Logitech Harmony Splitter. A link under the category selected above is automatically created for this variable.

The variable names and the name of the commands are created as they are stored by the name in the Harmony Hub. For each created variable also the description field is used, here stands the actual command inside which is sent to the Harmony Hub. Therefore, the description field of the variable must not be changed. The name of the variable as well as the command names that are stored in the variable profile of the variable can be customized by the user. However, the order in the variable profile should not change


## 4. Function reference

### Logitech Harmony Hub:

### Harmony Devices
The Harmony Devices are to be created via the configurator
A command can be sent to each device
 
Reads out the available functions of the device and outputs them as an array
```php 
LHD_GetCommands(integer $InstanceID) 
```  
Parameter _$InstanceID_ ObjectID of the Harmony Hub device

  
 Sends a command to the Logitech Harmony Hub 
```php
LHD_Send(integer $InstanceID, string $Command)
``` 
 Parameter _$InstanceID_ ObjectID of the Harmony Hub device
 Parameter _$Command_ Command to be sent, available commands are read out via LHD_GetCommands.
 
### Harmony Hub
Activities of the Logitech Harmony Hub can be performed.
The current activity of the Logitech Harmony Hub is displayed in the variable Harmony Activity and can be switched on the web front.
 
If the activity is to be updated via functions or switched via a script, the following functions are to be used:
Requests the current activity of the Logitech Harmony Hub. The value is set in the variable Harmony Activity.
```php
HarmonyHub_getCurrentActivity(integer $InstanceID) 
```   
Parameter _$InstanceID_ ObjektID of the Harmony Hub Splitter

 
Reads all available activities of the Logitech Harmony Hub and returns an array.
```php
HarmonyHub_GetAvailableAcitivities(integer $InstanceID) 
```   
Parameter _$InstanceID_ ObjektID of the Harmony Hub Splitter
  
Reads all available Device IDs of the Logitech Harmony Hub and returns an array.
```php
HarmonyHub_GetHarmonyDeviceIDs(integer $InstanceID) 
```   
   
Parameter _$InstanceID_ of the Harmony Hub Splitter
 
Switches to the desired Logitech Harmony Hub activity
```php
HarmonyHub_startActivity(integer $InstanceID, integer $activityID)
``` 
Parameter _$InstanceID_ ObjektID of the Harmony Hub Splitter
Parameter _$activityID_ ID of the Harmony Activity, available IDs can be read out via HarmonyHub_GetAvailableAcitivities

## 5. Configuration:

### Logitech Harmony Hub:

| Property         | Type    | Standard Value | Function                                            |
| :--------------: | :-----: | :------------: | :-------------------------------------------------: |
| Open             | boolean | true           | Connect to Logitech Harmony Hub Active / Disable    |
| Host             | string  |                | IP address of the Logitech Harmony Hub              |
| Email            | string  |                | Email address to login MyHarmony                    |
| Passwort         | string  |                | Password to log in MyHarmony                        |
| ImportCategoryID | integer |                | ObjectID of the import category                     |
| HarmonyVars      | boolean |                | Active creates variables per control group          |
| HarmonyScript    | boolean |                | Active creates a script for each command            |


### Logitech Harmony Device:  

| Property        | Type    | Standard Value | Function                                                              |
| :-------------: | :-----: | :------------: | :-------------------------------------------------------------------: |
| Name            | string  |                | Name of the device                                                    |
| DeviceID        | integer |                | DeviceID of the device                                                |
| BluetoothDevice | boolean |     false      | Bluetooth Device                                                      |


## 6. Annnex

###  b. GUIDs und Data Flow:

#### Logitech Harmony Hub Splitter:

GUID: `{7E03C651-E5BF-4EC6-B1E8-397234992DB4}` 


#### Logitech Harmony Device:

GUID: `{C45FF6B3-92E9-4930-B722-0A6193C7FFB5}` 

Credits:
[Logitech Harmony Ultimate Smart Control Hub Library](https://www.symcon.de/forum/threads/22682-Logitech-Harmony-Ultimate-Smart-Control-Hub-library "Logitech-Harmony-Ultimate-Smart-Control-Hub-library") _Zapp_ 
