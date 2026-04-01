# Description
A full-resolution (160x120) port of the iconic "Bad Apple!!" shadow art animation for the MakeCode Arcade engine.

# Project Overview
This project brings the "Bad Apple!!" music video to MakeCode Arcade. While I discovered later that others have attempted this before, my goal was to push the hardware limits beyond previous versions. Most existing versions use significantly lower resolutions; this build renders at the full 160x120 native resolution, prioritizing visual fidelity and the "authentic" aesthetic.

### Note on Origins
When I began this project, I was unaware of previous attempts. I did eventually find a community post with a functional music sequence which I adapted for this version. Unfortunately, the original author was not credited in the post I found—if you recognize the music sequence code, please reach out so I can provide proper credit!

# Optimizations
Running 6,000+ frames of animation at 30fps 160x120 alongside audio in a browser-based engine requires heavy optimization. At first, the project would not run and even crashed my browser. To solve this, I implemented two major changes:

### 1. Hex-Encoded Audio over MIDI
Initially, using a standard MIDI-style player caused significant overhead.

**The Change**: I bypassed the player logic and used hex-encoded music strings.

**The Result**: By editing the hex directly (specifically the second byte to control BPM), I reduced CPU cycles significantly. Switching to hex-based music increased the overall frame rate by approximately 30%.

### 2. Strategic Frame Skipping
The MakeCode engine struggled to maintain a consistent 30 FPS at 160x120.

**The Change**: Instead of forcing the engine to render every single frame, the code now renders every 4th frame (effectively 7.5 FPS).

**The Result**: This simple change took the project from not running at all to finally running consistently, smoothly, and reliably allowing the audio and video to stay in sync throughout the duration. 

# Credits & Attribution

**Original Creator**: The "Bad Apple!!" music video was originally created by Alstroemeria Records (Music) and ZUN (Composer, Team Shanghai Alice), with the iconic shadow-art PV created by Anira.

**Music Sequence**: Adapted from a community-shared hex string. While the original author of the MakeCode-compatible hex sequence remains anonymous as I could not find who made the original post (only the project was found), their work on the initial music coding was instrumental in making this version possible.

# Running this project

As this code is **MASSIVE** (~200,000 lines) sharing the code using the share button simply just times out an doesn't work. As a result, we have to compile it manually from GitHub. Below I have stated how to compile and run the code yourself.

* open [Makecode Arcade](https://arcade.makecode.com/)
* click on **Import** then click on **Import URL**
* paste **https://github.com/gongitygongitygong/bad-apple** and click import
