# Installation of the new asgard based qbr-core, with modern functions and calls and a lot of exploit protection.
1) Download and add the new qbr-core to your resources
2) Replace all of the current functions in your server resources with the ones provided below.
3) Add the GetCoreObject declaration to all of your client and server files as shown below.

# Replace all of the following lines in ALL of your files and resources - the easiest way to do this is to use a project explorer or development environment. Visual studio would be the easiest, simply open visual studio, open local folder, choose your server files folder to open the project > click edit in the top bar, find and replace, replace in files and then enter the first part of each of the following in the top bar and what it is being replaced with in the bar below.

# IMPORTANT - make sure you tick match case before pressing replace all.

exports['qbr-core']:TriggerCallback 	>With> 			QBCore.Functions.TriggerCallback
exports['qbr-core']:GetPlayerData 		>With>	 		QBCore.Functions.GetPlayerData
exports['qbr-core']:CreateCallback 		>With> 			QBCore.Functions.CreateCallback
exports['qbr-core']:GetPlayer 			>With> 			QBCore.Functions.GetPlayer
exports['qbr-core']:AddCommand 			>With> 			QBCore.Commands.Add
exports['qbr-core']:Notify 				>With> 			QBCore.Functions.Notify
exports['qbr-core']:Progressbar 		>With> 			QBCore.Functions.Progressbar
exports['qbr-core']:SplitStr 			>With> 			QBCore.Shared.SplitStr
exports['qbr-core']:GetClosestPlayer 	>With> 			QBCore.Functions.GetClosestPlayer
exports['qbr-core']:CreateUseableItem 	>With> 			QBCore.Functions.CreateUseableItem
exports['qbr-core']:GetPermissions 		>With> 			QBCore.Functions.GetPermission
exports['qbr-core']:GetQBPlayers 		>With> 			QBCore.Functions.GetQBPlayers
exports['qbr-core']:DeleteCharacter 	>With> 			QBCore.Player.DeleteCharacter
exports['qbr-core']:Logout 				>With> 			QBCore.Player.Logout
exports['qbr-core']:Login 				>With> 			QBCore.Player.Login
exports['qbr-core']:RefreshCommands 	>With> 			QBCore.Commands.Refresh
exports['qbr-core']:ShowSuccess 		>With> 			QBCore.ShowSuccess
exports['qbr-core']:GetIdentifier 		>With> 			QBCore.Functions.GetIdentifier

# Delete the following lines from all files they are in
local sharedItems = exports['qbr-core']:GetItems()
local sharedWeapons = exports['qbr-core']:GetWeapons()
local sharedJobs = exports['qbr-core']:GetJobs()
local sharedGangs = exports['qbr-core']:GetGangs()

# Next replace the following
sharedItems		> 	QBCore.Shared.Items
sharedWeapons 	> 	QBCore.Shared.Weapons
sharedJobs 		> 	QBCore.Shared.Jobs
sharedGangs 	> 	QBCore.Shared.Gangs

# To finish up, you will need to add the following line to the TOP of any client and server files that use any qbr-core functions (which is the vast majority, I would advise simply opening every client and server file at once and then pasting this line at the top, so you don't have to go through each individual one when you get an error.
local QBCore = exports['qbr-core']:GetCoreObject()

# Potential Errors:

attempt to index a nil value (global 'QBCore') - This simply means you forgot to add the GetCoreObject call to the resource you're getting the error for. Add the line directly above to the file.

no such export in QBCore / qbr-core - This means you simply left in one of the old exports, go to the file giving the error and replace the export giving the error with what it tells you to at the top of this document

Unexpected symbol near 'EXAMPLE' - This also means you have probably forgot the GetCoreObject, add it to this file and see if that fixes it. If not, you may have pasted the wrong thing. Feel free to contact us on discord at ANY time.