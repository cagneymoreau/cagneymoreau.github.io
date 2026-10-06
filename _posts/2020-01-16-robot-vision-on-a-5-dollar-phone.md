---
layout: post
title: "Robot Vision on a $5 Android Phone"
date: 2020-01-16
---

*Based on an eight-part tutorial series (2018–2019) and a 2020 update from my old blog. Revised and condensed.*

My robot needed eyes. I wanted cheap video I could send to a desktop computer for processing, because neural networks need more compute than you want to carry around on a robot.

## Why an old phone

An old Android phone costs about $5, or nothing if you ask around for one sitting in a junk drawer. It comes with a camera, a battery, Wi-Fi and a pile of sensors. Compare that to a bare $35 Raspberry Pi with no camera. The phone captures and sends the video, and the desktop does the heavy thinking.

## Why I did it the hard way

There are plenty of ready-made ways to stream video: paid services, WebRTC, libraries like libstreaming, and tools like FFmpeg and GStreamer. For video chat or entertainment, use them.

I wanted to understand and control every step: how bandwidth is used, when quality drops to cope with a weak connection, how connections get set up. Since the video was ultimately feeding AI processing, I didn't want someone else's API making those decisions for me. So I built the pipeline myself:

1. **Capture** frames from the camera.
2. **Pipe** the encoded data out of the camera code.
3. **Packetize** it and send it over the network.
4. **Depacketize** it on the desktop and hand it to a decoder for display.

It's hard for a reason. Real-time video depends on the H.264 codec, and understanding it meant learning how video is boxed inside MP4 files, how the stream is split into NAL units, and how the decoder's setup data (SPS and PPS) has to arrive first. The original series walked through each piece. This is the short version.

## What I learned by 2020

- **Don't use Android's old camera API.** Use Camera2.
- **WebRTC is everywhere** (most video-calling apps use it), but its API is built for calls. I found an open library that exposes it frame by frame, which was exactly what a robot needs.
- **The numbers on my home network:** about 16 ms to encode a frame, about 5 ms to packetize and send it, and about 740 ms from the desktop's "start video" command to the first frame arriving.
- **On the desktop**, JavaCV's FFmpeg frame grabber decoded and displayed the stream. Getting it to real time took building a snapshot of the library and changing one threading setting by hand to remove a latency buffer, which I figured out with help from Stack Overflow.

## The result

A $5 phone became the robot's camera, streaming to a desktop that ran object detection (YOLO) so I could see what the arm was looking at. It was never production code. There were artifacts, and plenty of rough edges. But building it piece by piece taught me how real-time video actually works, which no library would have.
