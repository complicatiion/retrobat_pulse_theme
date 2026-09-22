# Changelog

## Pulse RetroBat Compatibility v1.0 — 2026-09-22

- Created RetroBat-specific compatibility edition from Batocera Pulse Theme.
- Kept theme format version 7.
- Verified `controllerActivity` and `batteryIndicator` as valid parser elements.
- Removed unsupported `scrollSound` from `menuText`.
- Preserved supported gamelist and carousel scroll sounds.
- Fixed duplicate background subset names for MIX9 and MIX10.
- Corrected Grid `md_rating` element type from `text` to `rating`.
- Removed redundant conditional `maxLogoCount` referencing an undefined subset.
- Updated theme header/comments for RetroBat compatibility edition.
- Updated README and installation instructions for Windows/RetroBat.
- Added automated PowerShell installer and full-package builder.
- Added compatibility audit documentation.
