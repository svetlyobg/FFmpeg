# FFmpeg
FFmpeg

## Конвериране на видео от mp4 към mkv

ffmpeg -i bg.mp4 -c copy -map_metadata 0 bg.mkv

## Вграждане на български субтитри

ffmpeg -i bg.mkv -i bg.srt -map 0 -map 1:s:0 -c copy -metadata:s:s:1 language=bul -metadata:s:s:1 title="Bulgarian Subtitles (SRT)" bg_subs.mkv

## Разделяне на видео на 15 минутни сегменти

ffmpeg -i bg.mkv -c copy -map 0 -segment_time 00:15:00 -f segment -reset_timestamps 1 bg%03d.mkv