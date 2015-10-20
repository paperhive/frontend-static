
Creating the rocket videos for launch page
---

Go to [the NASA HD video archives](https://www.nasa.gov/multimedia/hd/index.html)
and get [the Atlantis launch video](http://s3.amazonaws.com/akamai.netstorage/HD_downloads/135_launch_1080i.wmv).

Then cut the video and convert it to webm/mp4:

```
ffmpeg \
  -i 135_launch_1080i.wmv \
  -ss 3.2 \
  -t 0.7 \
  -an \
  -c:v libvpx \
  -crf 10 \
  -b:v 2M \
  -vf mp=eq2=1:1.0:-0.1:1:1:1:1 \
  -vf crop=1900:950:10:130 \
  rocket.webm
```

```
ffmpeg \
  -i 135_launch_1080i.wmv \
  -ss 3.2 \
  -t 0.7 \
  -an \
  -c:v mpeg4 \
  -crf 10 \
  -b:v 2M \
  -vf mp=eq2=1:1.0:-0.1:1:1:1:1 \
  -vf crop=1900:950:10:130 \
  rocket.mp4
```

Check out the videos with
```
mplayer -loop 0 rocket.webm
```
