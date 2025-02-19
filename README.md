# Comet

Open Source implementation of GOG Galaxy's Communication Service

This project aims to implement calls made by game through SDK.  
Note: that means it can't and won't replace Communication Service in official client

This will provide minimal and platform agnostic SDK. For use in game launchers like Heroic or Lutris

Project is continuation of Yepoleb's work [https://gitlab.com/Yepoleb/comet/](https://gitlab.com/Yepoleb/comet/) but in
Python

## Supported Requests

Excluding Overlay, and Cloud Sync related.

- [x] AUTH_INFO_REQUEST
- [x] GET_USER_STATS_REQUEST
- [x] SUBSCRIBE_TOPIC_REQUEST
- [x] UPDATE_USER_STAT_REQUEST
- [x] DELETE_USER_STATS_REQUEST
- [ ] GET_GLOBAL_STATS_REQUEST
- [x] GET_USER_ACHIEVEMENTS_REQUEST
- [x] UNLOCK_USER_ACHIEVEMENT_REQUEST
- [x] CLEAR_USER_ACHIEVEMENT_REQUEST
- [x] DELETE_USER_ACHIEVEMENTS_REQUEST
- [x] GET_LEADERBOARDS_REQUEST
- [x] GET_LEADERBOARD_ENTRIES_GLOBAL_REQUEST
- [x] GET_LEADERBOARD_ENTRIES_AROUND_USER_REQUEST
- [ ] GET_LEADERBOARD_ENTRIES_FOR_USERS_REQUEST
- [ ] SET_LEADERBOARD_SCORE_REQUEST
- [ ] AUTH_STATE_CHANGE_NOTIFICATION
- [ ] GET_LEADERBOARDS_BY_KEY_REQUEST
- [ ] CREATE_LEADERBOARD_REQUEST
- [ ] GET_USER_TIME_PLAYED_REQUEST
- [ ] SHARE_FILE_REQUEST
- [ ] START_GAME_SESSION_REQUEST
- [ ] OVERLAY_STATE_CHANGE_NOTIFICATION
- [ ] CONFIGURE_ENVIRONMENT_REQUEST

## Experimental support

Following requests are supported experimentally (they haven't been tested well)

- UPDATE_USER_STAT_REQUEST - no testing
- UNLOCK_USER_ACHIEVEMENT_REQUEST - able to avoid unlocking the achievement again (unsure about response status code)

## How to use

Currently service supports small amount of calls, but these are enough to play Gwent for example.

First, you neeed to obtain data about account `access_token`, `refresh_token` and `user_id`

(for Heroic these can be found in `.config/heroic/gog_store/config.json`)

### Dependencies

Currently the only dependency is python protocolbuffers and aiohttp

```sh
pip install -r requirements.txt
```

Alternatively you can install it using your Linux distro's package manager

### Running

```
./bin/comet --token "<access_token>" --refresh_token "<refresh_token>" --user-id <user_id>
```

Or if you are using heroic

```
./bin/comet --from-heroic
```

## Contributing

Join [Heroic Discord](https://discord.gg/rHJ2uqdquK) and reach out to us on
special [thread](https://discord.com/channels/812703221789097985/1074048840958742648)

[Here](https://imlinguin.vercel.app/blog/galaxy-comm-serv-re-setup) you can find a blog post about setting up
environment for tracing the Communication Service calls (involving Proxifier and custom mitmproxy)

Reverse engineered protobuf definitions are available here: https://github.com/Yepoleb/gog_protocols
