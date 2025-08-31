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


# yt-dlp
yt-dlp

[Изтегли](https://github.com/yt-dlp/yt-dlp/releases)

## Изтегляне на видео

yt-dlp "URL"

## Най-добро комбинирано изтегляне на видео и аудио

yt-dlp -f "bv*+ba/best" <video_url>

## Най-добър MP4 формат (широко съвместим)

yt-dlp -f "bv*[ext=mp4]+ba[ext=m4a]/b[ext=mp4]" <видео_линк>

## Само аудио (например за музика)

yt-dlp -f "bestaudio" --extract-audio --audio-format mp3 <видео_линк>

## Списък с всички налични формати

yt-dlp --list-formats <видео_линк>

