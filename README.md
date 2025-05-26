# BetterTeams Placeholder API Documentation

## Requirements
- BetterTeams v2
- Placeholder API (https://modrinth.com/mod/placeholder-api)
- Any mod that supports Placeholder API (StyledChat, TAB, etc.)

## Available Placeholders

### Team Information
```
%betterteams:team_name%           - Team name without color
%betterteams:team_name_colored%   - Team name with color formatting
%betterteams:team_display%        - [TeamName] in team color
%betterteams:team_prefix%         - [TeamName] with trailing space
%betterteams:team_suffix%         - Space with [TeamName]
%betterteams:team_color%          - Color name (e.g., GOLD, RED)
%betterteams:team_color_code%     - Minecraft color code
```

### Member Information
```
%betterteams:team_owner%          - Team owner's name
%betterteams:team_members%        - Total member count
%betterteams:team_members_online% - Online member count
%betterteams:team_members_list%   - Comma-separated member list
```

### Player Status
```
%betterteams:has_team%            - true/false
%betterteams:is_owner%            - true/false
%betterteams:role%                - Owner/Member
%betterteams:role_symbol%         - ★ for owner, • for member
```

### Global Statistics
```
%betterteams:total_teams%         - Total teams on server
%betterteams:largest_team%        - Name of largest team
%betterteams:player_team:NAME%    - Get team of specific player
```

### Conditional Placeholders
```
%betterteams:if_has_team:TEXT%    - Shows TEXT only if player has team
%betterteams:if_no_team:TEXT%     - Shows TEXT only if player has no team
```

## Usage Examples

### StyledChat Configuration
```json
{
  "default": {
    "chat": "%betterteams:team_prefix%<${player}> ${message}",
    "join": "%betterteams:team_display% ${player} joined the game",
    "quit": "%betterteams:team_display% ${player} left the game"
  }
}
```

### Advanced Chat Formats
```
Basic prefix:
%betterteams:team_prefix%%player:name%: %message%

With role symbol:
%betterteams:role_symbol% %player:name%%betterteams:team_suffix%: %message%

Conditional display:
%player:name%%betterteams:if_has_team: [%betterteams:team_name_colored%]%: %message%

Team info format:
%betterteams:team_name% (%betterteams:team_members_online%/%betterteams:team_members% online)
```

### TAB List Examples
```
Simple:
%betterteams:team_prefix%%player:name%

With role:
%betterteams:role_symbol% %player:name% [%betterteams:team_name_colored%]

Conditional:
%player:name%%betterteams:if_has_team: - %betterteams:team_name%%

Server format:
%luckperms:prefix%%betterteams:team_prefix%%player:name%%luckperms:suffix%
```

### Scoreboard Examples
```
Team: %betterteams:team_name_colored%
Role: %betterteams:role%
Members: %betterteams:team_members_online%/%betterteams:team_members%
Leader: %betterteams:team_owner%
```

## Testing Placeholders

BetterTeams includes built-in test commands:

```
/bteam placeholder test
Shows all placeholder values for your current state

/bteam placeholder parse <text>
Parses custom text with placeholders
```

### Test Examples:
```
/bteam placeholder parse Hello %betterteams:team_prefix%world!
/bteam placeholder parse Team: %betterteams:team_name_colored% Members: %betterteams:team_members%
/bteam placeholder parse %betterteams:if_has_team:In team: %betterteams:team_name%%
```

## Compatible Mods
- StyledChat - Chat formatting
- Styled Nicknames - Player name customization
- TAB-Reborn - TAB list management
- Styled Player List - Enhanced player list
- Any mod supporting Placeholder API

## Notes
- Placeholders return empty strings for players without teams
- Color codes use standard Minecraft formatting
- All placeholders are case-sensitive
- The API is optional - BetterTeams works without it

## Support
Discord: @.t4bzzz 
