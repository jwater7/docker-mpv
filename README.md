# docker-mpv
Implement the mpv video player (mplayer fork) in a docker container

## Usage
Using the command line interface, execute the container:
~~~~
sudo docker run -it --rm --privileged -v /dev/dsp:/dev/dsp jwater7/docker-mpv mpv --help
~~~~
The --privileged flag must be set to work properly with alsa.  The -v (volume) flag must be used to mount the sound card device to listen to audio.

An example to play an web radio station:
~~~~
sudo docker run -it --rm --privileged -v /dev/dsp:/dev/dsp jwater7/docker-mpv mpv --playlist https://jbradio2.ca/links/m3u/320_mp3.m3u
~~~~

An example to watch a video (mounted inside the container):
~~~~
xhost +localhost
sudo docker run -it --rm -v /dev/dsp:/dev/dsp -v /path/to/videofile:/data -v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY=$DISPLAY --privileged jwater7/docker-mpv mpv '/data/videofilename.avi'
~~~~

