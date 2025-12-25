
![](https://github.com/anxdpanic/plugin.video.youtube/raw/master/resources/media/icon.png)

[![Build Status](https://img.shields.io/endpoint.svg?url=https%3A%2F%2Factions-badge.atrox.dev%2Fanxdpanic%2Fplugin.video.youtube%2Fbadge&logo=none)](https://actions-badge.atrox.dev/anxdpanic/plugin.video.youtube/goto)
![License](https://img.shields.io/badge/license-GPL--2.0--only-success.svg)
![Kodi Version](https://img.shields.io/badge/kodi-leia%20(18)-success.svg)
![Python Version](https://img.shields.io/badge/python-2.7-blue.svg)
![Contributors](https://img.shields.io/github/contributors/anxdpanic/plugin.video.youtube.svg)

## Kodi 18 (Leia) - Python 2 Version

This is a special version of the YouTube add-on that has been adapted for Kodi 18 (Leia) with Python 2.7 compatibility.

### Key Changes

- **Python Version**: Requires Python 2.7 (xbmc.python version 2.25.0)
- **Dependencies Updated**: All dependencies have been adjusted for Kodi 18 compatibility
  - script.module.requests: 2.21.0
  - inputstream.adaptive: 2.4.3
  - script.module.kodi-six: Required for Python 2/3 compatibility layer

### Compatibility

The codebase uses `from __future__` imports throughout to ensure Python 2/3 compatibility:
- `from __future__ import absolute_import, division, unicode_literals`

All code follows Python 2.7 compatible syntax while maintaining compatibility with the original Python 3 design.

## Links

* [YouTube](http://www.youtube.com)
* [Support thread](https://ytaddon.page.link/forum)
* [Wiki](https://github.com/anxdpanic/plugin.video.youtube/wiki)

---

![](https://i.imgur.com/fzPmDDJ.gif)
