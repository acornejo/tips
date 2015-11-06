# DVD-Rip

    mplayer dvd:/// -chapter 1-1  -dumpstream -dumpfile video.vob
    ffmpeg -i video.mp4 -f mp4 -vcodec mpeg4 -maxrate 1000 -b 700  -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 96 -s 320x240 -aspect 4:3 video.mp4
    ffmpeg -i video -f mp4 -vcodec mpeg4 -maxrate 1000 -b 700  -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 96 -s 320x240 -aspect 4:3 -map 0:0 -map 0:2 video.mp4
