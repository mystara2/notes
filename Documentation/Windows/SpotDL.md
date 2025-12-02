
So you've gone down the path of ditching spotify for local music, or are just reinstalling it and forgot how to get it working properly, well lets do it step by step to make sure it works


* **STEP 1**: Install python 3.13 (if you have python already do `python --version` to check which version you have, if u have newer than 3.13, downgrade if you are older than 3.11, upgrade to 3.13)
* **STEP 2**: Upgrade pip `python.exe -m pip install --upgrade pip`
* **STEP 3**: Install spotDL `pip install yt-dlp` then `pip install --upgrade spotdl yt-dlp`
* **STEP 4**: Configs, restart your shell (either `pwsh.exe` or close & reopen) then `spotdl --generate-config` (AND `spotdl --download-ffmpeg` else it wont work)
* **STEP 5**: now you edit your configs, ill provide what ive edited below

```json
{
  "_comment_audio_providers": "Add SoundCloud as a fallback provider.",
  "audio_providers": [
    "youtube",
    "youtube-music",
    "soundcloud"
  ]

  "_comment_output": "Custom output path formatting.",
  "output": "F:/Music/Download/{artist}/[{year}] {album}/{artists} - {title}.{output-ext}",
  "_comment_ffmpeg_args": "Encode to MP3 320k using libmp3lame.",
  "ffmpeg_args": "-acodec libmp3lame -b:a 320k -compression_level 0 -threads 8 -nostats -hide_banner",

  "_comment_yt_dlp_args": "Force m4a when available (itag 140), otherwise fall back to bestaudio. sleep-interval helps avoid rate limiting.",
  "yt_dlp_args": "--sleep-interval 3 --ignore-no-formats-error --format 140/bestaudio",
}
```

if you get rate-limited by spotify you can make a [developer app](https://developer.spotify.com) and set these values:
* links you do:
* `http://127.0.0.1:8800/`
* `http://127.0.0.1:8800/callback`
and select Web API

then replace client_id and client_secret from your `config.json` to the values on the dev app.

should be good to go now! simply do `spotdl [url]` to begin! if it ever errors out, run `spotdl [url] --log-level DEBUG` to find out why.