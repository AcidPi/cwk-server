# Card Wars Kingdom Reversed-Engineered Server

This is a reversed-engineered server for Card Wars Kingdom, designed for version 1.0.17 works with v1.0.17 - v1.19.0 ( v1.19.1 requires fixes ).

**Disclaimer**: This server is intended for use only by individuals you trust, as it lacks essential security measures in this version.

Blueprints are sourced from the original CWK and may require changes.

## Setup

1. **Server Configuration**: Navigate to `CardWarsKindom/Card Wars Kingdom_data/StreamingAssets/server_settings.json` and replace the `server_url` with the web address of the server you want to connect to. You should also replace `photon_chat_app_id` and `photon_pun_app_id` if you intend to use PVP and Chat.

2. **VPN Usage**: It is recommended to use a VPN when connecting to someone else's server.

## Running the Server

To run the server, use one of the following methods:

- Using Python: `python app.py`
- Using Gunicorn: `gunicorn app:app app.py`

## Additional Setup

It is recommended to set up Chat and PUN servers with [Photon](https://www.photonengine.com/) if you want to play PVP and use chat exclusively with users of your server.

## Notes

### v1.0.17 - v1.19.0
- Works.

### v1.19.1
- Works, however requires fixes.

### v1.19.1 Fixes

#### PersistGame(username) 
- Get username/playerid from request.headers Player-Id.

#### UserAction2()
- Add **handle** in the data dictionary or game will freeze in treasure cave.
- Add sha256 Hash to handle or gems wont deduct from your total.
- Key to generate hash has been changed and no longer matches the original game source.
- `OldKey = "5424493204pemhi3148ifmanseu4iksdf4_4" + clientData["player_id"] + clientData["misc"]`
- `NewKey = "5424498w34tiowhtgoae0tu4iksdf4_4" + clientData["player_id"] + "650"`
- *All versions:* add **level1** to the data dictionary if you have PaidHardCurrency in your save game.

#### Other

- Rename **discord_game_sdk.dll** `<your_install_location>\CardWarsKingdom\Card Wars Kingdom_Data\Plugins\x86_64\` if you dont want data sent to discord.
- Add folder **recordings** to `%USERPROFILE%\LocalLow\shishkabob\Card Wars Kingdom\` to stop error *folder not found* in logs.
- Edit file **config** `%USERPROFILE%\LocalLow\shishkabob\Card Wars Kingdom\Unity\local.*\Analytics\` if you dont want to generate files in ArchivedEvents or possibly send?
```
{
	"analytics": {
		"enabled": false
	},
	"connect": {
		"limit_user_tracking": true,
		"player_opted_out": true,
		"enabled": false
	},
	"performance": {
		"enabled": false
	},
	"dynamic": {
		"coreBusinessMetrics": {
			"enabled": false,
			"timeToWaitForUserInfoS": 86400
		},
		"analytics": {
			"shouldCollectAutomation": false,
			"timeToWaitForUserInfoS": 86400
		}
	}
}
```
