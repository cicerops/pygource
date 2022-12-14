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

Debian Linux::

    apt install ffmpeg gource mp3wrap youtube-dl

macOS/Homebrew::

    brew install ffmpeg gource mp3wrap youtube-dl


*****
Usage
*****

::

    python pygource.py \
        --name "Project ACME" \
        --path /path/to/acme \
        --audio '/path/to/audio.mp3'


********
Examples
********

Common
======

Get an audio file::

    youtube-dl --extract-audio --format=m4a \
        --output="./var/Beastie boys - Suco De Tangerina.m4a" \
        https://www.youtube.com/watch?v=lpHWxf5xL0w

Convert it to MP3 format::

    ffmpeg \
        -i "./var/Beastie boys - Suco De Tangerina.m4a" \
        -c:v copy -c:a libmp3lame -q:a 4 \
        "./var/Beastie boys - Suco De Tangerina.mp3"

Gource
======

Acquire sources::

    git clone https://github.com/acaudwell/Gource ./var/Gource

Render and play video::

    python pygource.py \
        --name "Gource" \
        --path "./var/Gource" \
        --audio "./var/Beastie boys - Suco De Tangerina.mp3"

    open -a vlc Gource.mp4


CrateDB
=======

Acquire sources::

    git clone https://github.com/crate/crate ./var/crate

Render and play video::

    python pygource.py \
        --name "CrateDB 2022H2" \
        --start-date 2022-06-01 \
        --time-lapse \
        --path ./var/crate \
        --audio "./var/Beastie boys - Suco De Tangerina.mp3" \
        --outdir "./var" \
        --overwrite

    open -a vlc "./var/CrateDB 2022H2.mp4"


.. _Gource: https://github.com/acaudwell/Gource
