## SpoonMaskv1 how to
+ This file is contain the needed changes for the mask work perfect.
+ We will use v3.16.0 of PocketMine-MP as an example.
+ SpoonMask v1 is use in production in UNW's official server.
+ [IMPORTANT!!!] READ THE CODE VERY CAREFULLY IF YOU DON'T WANT TO BREAK THE VERSION/API SYSTEM.

### Add SpoonMask.php into /src/pocketmine/ (IMPORTANT!)
+ To get the SpoonMaskv1 work, you need to add SpoonMask.php into /src/pocketmine folder and add this code in /src/pocketmine/PocketMine.php
```php
	require_once __DIR__ . '/SpoonMask.php';
```

### Changes in /src/pocketmine/Server.php

#### Add new functions
+ We need to add some function to work with our SpoonMask, such as (getDistroName, getDistroVersion and getCodename.)
+ You need add it like this:

```php
	public function getDistroName() : string{
		return \pocketmine\DISTRO_NAME;
    }
```
... do the same, exactly with last 2 function.

### Replace arrays, function fallback (return) with contain old name:
+ [IMPORTANT!] DO NOT RENAME ANY DEFAULTS POCKETMINE PUBLIC FUNCTIONS.
+ [IMPORTANT!] DO NOT USE REPLACE ALL FUNCTION!!!!
+ The original name, defined as PocketMine-MP still display on the console, game or some place you don't know.
+ You just need to find and replace this:
```
"\pocketmine\NAME" into "\pocketmine\DISTRO_NAME"
"\pocketmine\VERSION" into "\pocketmine\DISTRO_VERSION"
"getName()" into "getDistroName"
```
+ Example:
```php
			critical_error("Another " . \pocketmine\NAME . " instance (PID $pid) is already using this folder (" . realpath(\pocketmine\DATA) . ").");
```

into

```php
			critical_error("Another " . \pocketmine\NAME . " instance (PID $pid) is already using this folder (" . realpath(\pocketmine\DATA) . ").");
```
+ It will appear at some files, I just found these files and use it on UNWDS (stable):
```
\src\pocketmine\Server.php

\src\pocketmine\PocketMine.php

\src\pocketmine\wizard\SetupWizard.php

\src\pocketmine\commands\default\VersionCommand.php
```
+ Read carefully or you will replace wrong some function like get player, plugin name ( the function same getName() but it get player's or plugins name not the server software name. )  
+ Now, run the source code and try it!

#### Tobe continued


