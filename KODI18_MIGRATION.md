# Kodi 18 (Leia) Migration Guide

## Overview

This version of plugin.video.youtube has been specifically adapted for Kodi 18 (Leia) which requires Python 2.7 compatibility.

## Changes Made

### 1. Addon Metadata (addon.xml)

- **xbmc.python version**: Changed from `3.0.0` to `2.25.0`
- **Version number**: Updated to `7.4.0+beta.2.kodi18` to distinguish from Python 3 version
- **Dependencies updated**:
  - `script.module.requests`: `2.27.1` → `2.21.0`
  - `inputstream.adaptive`: `19.0.0` → `2.4.3`
  - **Added**: `script.module.kodi-six` for Python 2/3 compatibility

### 2. Python Code Compatibility

All Python source files already use the following future imports for Python 2/3 compatibility:
```python
from __future__ import absolute_import, division, unicode_literals
```

These imports ensure:
- **absolute_import**: Import behavior is consistent with Python 3
- **division**: Division operator `/` performs true division (not floor division)
- **unicode_literals**: String literals are Unicode by default

### 3. Compatibility Layer

The add-on includes a comprehensive compatibility layer at `resources/lib/youtube_plugin/kodion/compatibility/__init__.py` that:

- Provides unified imports for Python 2 and 3
- Uses `kodi_six` module for Kodi-specific API wrappers
- Handles differences in:
  - String types (unicode vs str)
  - URL parsing libraries
  - HTTP server modules
  - Pickle implementations
  - and more...

### 4. Code Practices

The codebase follows Python 2 compatible practices:
- No f-strings (uses `.format()` instead)
- No async/await syntax
- No type annotations
- No Python 3-only syntax (yield from, raise...from, etc.)
- Uses `.items()` for dictionary iteration (compatible with both versions)

## Testing

The add-on should be tested on Kodi 18 (Leia) to ensure:
1. Installation succeeds
2. All dependencies are resolved
3. Basic functionality works (browsing, search, playback)
4. Settings and configuration work correctly

## Technical Notes

### String Handling

Python 2 has two string types (str and unicode) while Python 3 has only one (str).
The compatibility layer handles this by:
- Using `basestring` type checking in Python 2
- Using `str` type checking in Python 3
- Providing `to_str()` function for conversions

### Division

With `from __future__ import division`:
- `/` operator does true division (e.g., `5/2 = 2.5`)
- `//` operator does floor division (e.g., `5//2 = 2`)

This matches Python 3 behavior and ensures consistent math operations.

### Import Statements

All relative imports use absolute import syntax:
```python
from .module import function  # ✓ Correct
from module import function   # ✗ Avoid
```

## Version Compatibility Matrix

| Kodi Version | Python Version | xbmc.python | This Add-on Version |
|--------------|----------------|-------------|---------------------|
| Kodi 18 (Leia) | Python 2.7 | 2.25.0 | 7.4.0+beta.2.kodi18 |
| Kodi 19+ (Matrix+) | Python 3.x | 3.0.0+ | Use original version |

## Support

For issues specific to Kodi 18 compatibility, please check:
1. All dependencies are installed correctly
2. You're running Kodi 18 (Leia)
3. script.module.kodi-six is installed

## References

- [Kodi 18 Add-on Development](https://kodi.wiki/view/Add-on_development)
- [Python 2/3 Compatibility](https://kodi.wiki/view/General_information_about_migration_to_Python_3)
- [kodi-six module](https://github.com/romanvm/kodi.six)
