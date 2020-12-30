---
title: Setting up OBS with Teams MACOSX.
description: This is a post on My Blog about agile frameworks.
date: 2020-12-30
tags:
  - MACOSX
  - OBS
  - MS Teams
layout: layouts/post.njk
---
So in these times of working from home, I have increasingly been frustrated by the fact my camera angles on video calls when using multiple screens are not the best. I am constantly looking on the content of another screen and people then just get to see the side of my head. This was an opportunity therefore to sort out the many cameras I have floating around and follow the advice of [Scott Hansellman's blogpost on OBS ](https://www.hanselman.com/blog/take-remote-workereducator-webcam-video-calls-to-the-next-level-with-obs-ndi-tools-and-elgato-stream-deck).  I installed OBS and set around setting up the required scenes. 


## But it did not work

Nothing wrong with the instructions provided by Scott the OBS setup went smoothly and I installed the [OBS Virtual camera plugin](https://obsproject.com/forum/resources/obs-virtualcam.539/). but teams coudl not find the camera. Turns out the missing bit was down to the codesigning. So I removed the codesigning signatures for all the releavnt parts.


``` bash/2-3
sudo codesign --remove-signature "/Applications/Microsoft Teams.app"

sudo codesign --remove-signature "/Applications/Microsoft Teams.app/Contents/Frameworks/Microsoft Teams Helper.app"

sudo codesign --remove-signature "/Applications/Microsoft Teams.app/Contents/Frameworks/Microsoft Teams Helper (GPU).app"

sudo codesign --remove-signature "/Applications/Microsoft Teams.app/Contents/Frameworks/Microsoft Teams Helper (Plugin).app"

sudo codesign --remove-signature "/Applications/Microsoft Teams.app/Contents/Frameworks/Microsoft Teams Helper (Renderer).app"
```
And voila the camera appeared I now have each screen with a camera and a corresponding hotkey in OBS. 
