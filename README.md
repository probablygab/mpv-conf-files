# mpv conf files

My conf files for [mpv](https://mpv.io/). Tailored to Plex and [mpv.net](https://github.com/mpvnet-player/mpv.net)

TL;DR mpv is an amazing player, Plex uses it, you can use it standalone or with mpv.net (has a GUI).

It offers wide support for most media, supports scripts, shaders and has great support for HDR and Dolby Vision (BL and RPU layers only, FEL and MEL are ignored).

AFAIK only madVR surpasses it when it comes to HDR tonemapping, but madVR requires and external player and is gimmicky sometimes.

Some more stuff:

## Plex libmpv-2.dll replace

Why? Better support for everything and detailed infos.

DLL Source: <https://sourceforge.net/projects/mpv-player-windows/files/libmpv/>

Working versions, newer is better:

- [20250824](https://sourceforge.net/projects/mpv-player-windows/files/libmpv/mpv-dev-x86_64-v3-20250824-git-5faec4e.7z/download)
- [20250525](https://sourceforge.net/projects/mpv-player-windows/files/libmpv/mpv-dev-x86_64-v3-20250525-git-1d1535f.7z/download)

Extract and replace the original `libmpv-2.dll` in `C:\Program Files\Plex\Plex`.

## mpv.net with AnimeJanai

mpv.net used for real-time Anime/Cartoon Upscaling with [AnimeJanaiV3](https://github.com/the-database/mpv-upscale-2x_animejanai).

## AnimeJanai Plex injection

There's no need to use animejanai with mpv.net standalone, we can use it with Plex like so:

### STEP 1

Copy over every file in the animejanai install directory to `C:\Program Files\Plex\Plex` as-is, except libmpv-2.dll, use the first one indicated in the previous section.

For reference, the `animejanai` folder should be on the same level as `Plex.exe`.

### STEP 2

Grant the folder `C:\Program Files\Plex\Plex` permission to write as user (Right-Click > Security > Users > Edit > Write).

This allows VapourSynth and the Python interpreter to write cache and logs, otherwise this whole setup only works if Plex is run as admin.

### STEP 3

Copy everything inside `Plex-desktop` to `C:\Users\YOU\AppData\Local\Plex`. Check if the paths in `mpv.conf` and `animejanaistats.lua` match your config. Edit `mpv.conf` to your liking.

Alternatively, if you already have your conf set up, copy only the D3D11 settings and the end `mpv.conf` to your `mpv.conf`, also copy the scripts folder and the animejanai inputs in `input.conf`.

### NOTE

When Plex updates it erases all these modifications, repeat the process if this happens.

## Plex Tips and Tricks

- [QoL Scripts for mpv](https://forums.plex.tv/t/use-mpv-features-which-are-not-exposed-in-plex-for-windows-mac-linux-and-plex-htpc/830025)
- [Plex and the rules of 4K](https://forums.plex.tv/t/info-plex-4k-transcoding-and-you-aka-the-rules-of-4k/378203)
