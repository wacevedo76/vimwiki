# Linux General Notes

## Audio and Video
### ffmpeg
Combine Audio and Video files
`ffmpeg -i video.mp4 -i audio.webm -c:v copy -c:a aac -strict experimental output.mp4`

