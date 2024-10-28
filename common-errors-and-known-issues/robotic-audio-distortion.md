---
description: Some causes and solutions for robotic audio issues
---

# Robotic Audio Distortion

## Troubleshooting Robotic Audio Distortion in VDO.Ninja

### Overview

When experiencing robotic audio distortion in VDO.Ninja, the issue could stem from several sources - your system settings, OBS Studio, or even your browser. Below, we'll explore the various causes and their solutions.

### System Configuration Issues

One of the most common sources of audio distortion relates to your system's audio settings. Users with high sample rates (such as 384-khz) on their microphone or default system device often encounter problems. Similarly, 32-bit audio sampling can create issues. VDO.Ninja performs best with 48-khz sampling rate and either 16- or 24-bit depth. This is particularly relevant for users with FiiO audio DACs.

Some users have found that certain software features can interfere with audio quality. For instance, the _MyAsus_ software's AI Noise-Cancelling Speaker feature, when enabled for the default audio output device, has been known to cause distortion. Simply switching this setting to OFF has resolved the issue for many users.

Gaming peripherals can also be a source of trouble. Users with surround sound headphones, particularly 5.1/7.1 Logitech or Corsair gaming headsets, may experience distorted audio. To resolve this, try setting your headphones and speakers to 2.0 stereo audio and disable any surround sound / DTX effects. If problems persist, consider switching to a different headset.

### OBS Studio-Related Problems

When using OBS Studio, you might notice the issue becomes more pronounced when the browser source is minimized or running in the background. Some users have found success by simply running OBS in Administrator mode, suggesting the problem may be related to system priority settings.

If you see "Max audio buffering reached!" in your OBS log files, your computer might be struggling with CPU load. You have several options: reduce the demands on your CPU, upgrade your hardware, or try using the [Electron Capture app ](../steves-helper-apps/electron-capture.md)instead of the OBS Browser source for audio and video capture.

### Audio Routing and Echo Issues

If you're using virtual audio cables or a professional audio mixer, audio buffer issues might manifest as clicking sounds or distortion. Increasing the audio buffer size in your virtual audio cable settings often resolves these problems.

Echo cancellation can create unexpected robotic effects, particularly in specific scenarios. Having multiple VDO.Ninja tabs open on the same computer can create feedback loops that trigger echo cancellation. Similarly, if you have a mobile phone or second computer nearby that's streaming into the same VDO.Ninja group, you might experience feedback loops resulting in echo cancellation issues.

### Network and Connection Problems

High packet loss can significantly impact audio quality. While adding `&enhance&red` to your view/scene link might help, addressing the underlying packet loss is usually more effective. If you're using a VPN or operating behind a strict firewall that forces the use of relay servers, try to resolve these network constraints first.

### Version-Specific Considerations

Different versions of VDO.Ninja may handle audio processing differently. If you're experiencing persistent issues, you might want to try an older version, such as https://vdo.ninja/v23/. For systems under heavy load, adding `&noap` to your VDO.Ninja URL will disable web-audio processing, which can help with robotic audio effects caused by audio buffer underruns.

If you notice that the audio issues are specific to certain versions, please report them through the Discord community (https://discord.vdo.ninja). Your feedback helps improve the platform for everyone.
