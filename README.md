# FFmpeg
FFmpeg

[Изтегли](https://www.ffmpeg.org/download.html#build-windows)

## Конвериране на видео от mp4 към mkv

ffmpeg -i bg.mp4 -c copy -map_metadata 0 bg.mkv

## Вграждане на български субтитри

ffmpeg -i bg.mkv -i bg.srt -map 0 -map 1:s:0 -c copy -metadata:s:s:1 language=bul -metadata:s:s:1 title="Bulgarian Subtitles (SRT)" bg_subs.mkv

## Разделяне на видео на 15 минутни сегменти

ffmpeg -i bg.mkv -c copy -map 0 -segment_time 00:15:00 -f segment -reset_timestamps 1 bg%03d.mkv

## Извличане на аудио без повторно кодиране (по-бързо)

ffmpeg -i video.mp4 -vn -acodec copy audio.aac

## Извличане с конвертиране в MP3

ffmpeg -i video.mp4 -q:a 0 -map a audio.mp3

## Извличане на част от аудиото (по време)

ffmpeg -i video.mp4 -ss 00:01:00 -t 00:00:30 -q:a 0 -map a clip.mp3

## Изпозлване на видеокарта Nvidia

ffmpeg -i input.mp4 -c:v h264_nvenc -preset p5 -b:v 5M -c:a copy output_h264_nvenc.mp4

ffmpeg -i input.mp4 -c:v hevc_nvenc -preset p5 -b:v 3M -c:a copy output_hevc_nvenc.mp4

ffmpeg -hwaccel cuvid -c:v h264_cuvid -i input.mp4 -c:v h264_nvenc -preset p5 -b:v 5M -c:a copy output_gpu_decode_encode.mp4

## Извличане на всички кадри

ffmpeg.exe -i .\bg.mkv bg%3d.jpg

***

# yt-dlp
yt-dlp

[Изтегли](https://github.com/yt-dlp/yt-dlp/releases)

## Изтегляне на видео

yt-dlp "URL"

## Изпозлване на видеокарта Nvidia

yt-dlp -f bestvideo[ext=mp4]+bestaudio[ext=m4a] <URL>

ffmpeg -i "изтеглено_видео.mp4" -i "изтеглено_аудио.m4a" -c:v h264_nvenc -preset p5 -b:v 5M -c:a aac -b:a 192k final_video.mp4

```
--postprocessor-args "-c:v h264_nvenc -preset p5 -b:v 5M -c:a copy": Тези аргументи се предават на FFmpeg. Тук казваме на FFmpeg да прекодира видеото с h264_nvenc и да копира аудиото.
```

## Изтегляне на YouTube playlist

yt-dlp -f "bestvideo+bestaudio/best" --merge-output-format mp4 --output "%(playlist_index)s - %(title)s.%(ext)s" <URL_на_плейлиста>

## Най-добро комбинирано изтегляне на видео и аудио

yt-dlp -f "bv*+ba/best" <video_url>

## Най-добър MP4 формат (широко съвместим)

yt-dlp -f "bv*[ext=mp4]+ba[ext=m4a]/b[ext=mp4]" <видео_линк>

## Команда за изтегляне само на най-доброто видео

yt-dlp -f "bv*" <видео_линк>

## Само аудио (например за музика)

yt-dlp -f "bestaudio" --extract-audio --audio-format mp3 <видео_линк>

## Изтегляне само на MP4 видео (ако трябва конкретен формат)

yt-dlp -f "bv*[ext=mp4]" <видео_линк>

## Списък с всички налични формати

yt-dlp --list-formats <видео_линк>

