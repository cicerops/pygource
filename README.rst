########
PyGource
########


*****
About
*****

Render video of VCS repository commit history using `Gource`_, with audio.


*****
Setup
*****

::

    brew install ffmpeg gource mp3wrap youtube-dl


*****
Usage
*****

Get an audio file::

    youtube-dl --extract-audio --format=m4a \
        --output="./var/Beastie boys - Suco De Tangerina.m4a" \
        https://www.youtube.com/watch?v=lpHWxf5xL0w

Convert it to MP3 format::

    ffmpeg \
        -i "./var/Beastie boys - Suco De Tangerina.m4a" \
        -c:v copy -c:a libmp3lame -q:a 4 \
        "./var/Beastie boys - Suco De Tangerina.mp3"

Get sources of repository::

    git clone https://github.com/acaudwell/Gource ./var/Gource

Invoke renderer and play video, example 1::

    python pygource.py \
        --name Gource \
        --path "./var/Gource" \
        --audio-source "./var/Beastie boys - Suco De Tangerina.mp3" \
        --audio-loops 2

    open -a vlc Gource.mp4

Invoke renderer and play video, example 2::

    python pygource.py \
        --name "CrateDB 2022Q1" \
        --path ~/dev/crate/sources/crate \
        --audio-source "./var/Beastie boys - Suco De Tangerina.mp3" \
        --audio-loops 10 \
        --outdir "./var" \
        --overwrite

    # --time-lapse \

    open -a vlc "./var/CrateDB 2022Q1.mp4"

.. _Gource: https://github.com/acaudwell/Gource
