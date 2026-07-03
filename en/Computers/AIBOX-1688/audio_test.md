---
title: "Audio Interface Testing"
description: "AIBOX-1688 Audio Interface Testing documentation."
---

# Audio Interface Testing

AIBOX-1688 supports the American standard headphone interface.

Playback Test:
```
$ aplay -D hw:CARD=cv186xdac,DEV=1 /usr/share/sounds/alsa/Front_Center.wav
```
Recording Test:
```
$ arecord -D hw:CARD=cv186xadc,DEV=0  -c 2 -r 48000  -f S16_LE test.wav # Record audio (stereo)
$ aplay -D hw:CARD=cv186xdac,DEV=1  test.wav # Play the recorded audio
```