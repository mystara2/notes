
So you've gone down the path of ditching spotify for local music, or are just reinstalling it and forgot how to get it working properly, well lets do it step by step to make sure it works


* **STEP 1**: Install python 3.13 (if you have python already do `python --version` to check which version you have, if u have newer than 3.13, downgrade if you are older than 3.11, upgrade to 3.13)
* **STEP 2**: Upgrade pip `python.exe -m pip install --upgrade pip`
* **STEP 3**: Install spotDL `pip install yt-dlp` then `pip install --upgrade spotdl yt-dlp`
* **STEP 4**: Configs, restart your shell (either `pwsh.exe` or close & reopen) then `spotdl --generate-config` (AND `spotdl --download-ffmpeg` else it wont work)
* **STEP 5**: now you edit your configs, ill provide what ive edited below

```json
    "ffmpeg_args": "-acodec libmp3lame -b:a 320k -compression_level 0 -threads 8 -nostats -hide_banner",
    
    // this will be null by default, change it to that this will encode whatever the audio format is to that specific one
   
    "yt_dlp_args": "--sleep-interval 3 --ignore-no-formats-error --format 140/bestaudio",
    // sleep-interval is required by yt, so its set, we ignore format errors, and 140 is m4a, and if m4a isnt available, we do whatever the best audio track is. 
    // you can do custom formatting in output, for me i do
        "output": "F:/Music/Download/{artist}/[{year}] {album}/{artists} - {title}.{output-ext}",
        
    // i personally also add "soundcloud" as a option for audio providers aswell incase yt is dead
        "audio_providers": [
        "youtube",
        "youtube-music",
        "soundcloud"

    ],
```

if you get rate-limited by spotify you can make a [developer app](https://developer.spotify.com) and set these values:
* links you do:
* `http://127.0.0.1:8800/`
* `http://127.0.0.1:8800/callback`
and select Web API

then replace client_id and client_secret from your `config.json` to the values on the dev app.