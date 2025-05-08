**DISCLAIMER**

This script is provided as-is without any warranties or guarantees. By using this code, you acknowledge and agree that:
1. I am not responsible for any consequences resulting from the use of this script.
2. Using third-party scripts may violate Roblox's Terms of Service and could result in account restrictions or bans.
3.This project is for educational purposes only - demonstrating Roblox development techniques.
4.You assume all risks associated with using this code in any capacity.
5.Modifying game behavior with scripts may be considered cheating by some communities.

Use at your own discretion. The creator does not endorse or encourage using this in ways that break platform rules.


**Universal ESP for Roblox Games**

This is a Universal ESP script designed to work with most Roblox games that utilize the built-in Teams system. The script provides visual tracking of players through walls by displaying their names and team affiliations.

*Key Features:*

Automatically detects and displays all players in the game

Shows player names through walls and obstacles

Color-codes players based on their team affiliation

Highlights enemy players for better visibility

Works in real-time, updating player positions continuously

Configurable settings for text size, colors and display options

Technical Requirements:
The script requires:

A Roblox game that uses the official Teams service

The Teams service must be properly configured with TeamColor

Players must be assigned to teams through the standard system

How It Works:
The script accesses the game's Teams service to identify all available teams. It then tracks each player's character and assigns the appropriate team color. Enemy players are highlighted differently from teammates. The ESP elements are displayed using BillboardGui objects attached to each player's head.

Usage Warning:
This script is provided for educational purposes only. Using third-party scripts in Roblox games may violate the Terms of Service and could result in account restrictions. The functionality is limited to games using Roblox's native team system and will not work with custom team implementations or free-for-all game modes.

Implementation Note:
The script requires a compatible executor that can handle HTTP requests and loadstring functionality. Performance may vary depending on the game's complexity and player count.

For developers:
The code demonstrates advanced Roblox Lua techniques including:

Team system interaction

Character tracking

3D billboard rendering

Real-time player position updates

This project is open for contributions and improvements through pull requests.
