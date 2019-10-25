# Transcode audio in video files to Dolby Digital 5.1
This step-by-step guide explains how to transcode (convert) to Dolby Digital 5.1 sound from other codecs such as DTS and Dolby Digital Plus.

**This step-by-step guide isn't finished yet. Want me to hurry? Let me know by dropping a GitHub issue.**

## Requirements
* [FFmpeg](https://ffmpeg.zeranoe.com/builds/)

## Useful tool
To inspect audio streams in video files I tend to use [MediaInfo](https://mediaarea.net/en/MediaInfo). It's a great tool to display all codec and metadata information from a file.

## Commands
These commands can be placed in a batch script (e.g. `audioTranscode.bat` or `audioTranscode.cmd`). Then drag 'n drop a video file (MKV, MP4, etc.) onto the batch script.
* Convert all audio tracks in MKV file: `ffmpeg -i %1 -map 0 -vcodec copy -scodec copy -acodec ac3 -b:a 640k "%~d1%~p1%~n1"-AC3.mkv`
* Convert first audio track and drop all other audio tracks: `ffmpeg -i %1 -map 0:v -vcodec copy -map 0:a:0 -acodec ac3 -b:a 640k -map 0:s? -scodec copy "%~d1%~p1%~n1"-AC3.mkv`
* Convert second audio track and drop all other audio tracks: `ffmpeg -i %1 -map 0:v -vcodec copy -map 0:a:1 -acodec ac3 -b:a 640k -map 0:s? -scodec copy "%~d1%~p1%~n1"-AC3.mkv`
