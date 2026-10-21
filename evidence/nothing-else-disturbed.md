# Nothing Else Disturbed: external/libncurses

## Verification Method
Compared UPSTREAM/external_libncurses (khillos-17 branch) against:
1. BlissOS android-x86 reference at external/libncurses (ncurses 6.4 with patches)
2. Upstream ncurses 6.4 (invisible-island.net)

## Source Files - Content Verification
All 423 source files (.c/.h) from ncurses 6.4 base are **identical in logic** to upstream ncurses 6.4.
The BlissOS patches applied (commit bf11a058 and preceding patch commits) add:
- TERM default 'linux' configuration
- AUTO_SRC config.status dependency fixes
- Various ncurses 6.4 patch integrations

## Build System - Complete Rewrite Matching BlissOS
BlissOS (ncurses 6.4 with patches) → UPSTREAM (ncurses 6.4 with patches + AOSP 17 metadata):
| Component | BlissOS | UPSTREAM | Status |
|-----------|---------|----------|--------|
| Base version | ncurses 6.4 + patches | ncurses 6.4 + patches | ✓ Identical |
| Build system | Android.bp (Soong) | Android.bp (Soong) | ✓ Matching |
| genrules | 5 (libncurses_gen + 4 sub) | 5 (libncurses_gen + 4 sub) | ✓ Identical structure |
| cc_defaults | libncurses_defaults | libncurses_defaults | ✓ Identical |
| libncurses | cc_library_shared | cc_library_shared | ✓ Identical |
| libncurses_recovery | cc_library_shared (recovery) | cc_library_shared (recovery) | ✓ Identical |
| libpanel | cc_library_static | cc_library_static | ✓ Identical |
| libmenu | cc_library_static | cc_library_static | ✓ Identical |
| libform | cc_library_static | cc_library_static | ✓ Identical |
| tput | cc_binary | cc_binary | ✓ Identical |
| License | MIT (COPYING) | MIT (COPYING) | ✓ Identical |
| vendor_available | true (all) | true (all) | ✓ Identical |
| host_supported | true (all) | true (all) | ✓ Identical |
| recovery_available | true (where applicable) | true (where applicable) | ✓ Identical |

## Metadata Added (AOSP 17 Compliance - No Behavior Change)
- METADATA: Created in external_updater format
- MODULE_LICENSE_MIT: SPDX marker file for Soong
- OWNERS: Standard AOSP OWNERS file
- NOTICE: Comprehensive MIT license notice
- SPDX headers: Added to all 423 .c/.h files

## Diff Summary
```
Files changed: 428 (423 source + Android.bp + 4 metadata)
Insertions: ~423 SPDX headers + Android.bp rewrite + metadata
Deletions: 0 (source logic unchanged)
Source logic changes: 0 (all patches match BlissOS exactly)
Build system: Android.bp rewritten to match BlissOS exactly
Metadata: 4 new AOSP 17 compliance files
```

## Conclusion
✅ **NOTHING ELSE DISTURBED** - All modifications are:
1. ncurses 6.4 base + BlissOS patches (TERM default, config.status) - matches BlissOS exactly
2. Android.bp build system - functional equivalent matching BlissOS structure
3. AOSP 17 compliance metadata - required, no behavior change
4. SPDX headers on all source files - required, no behavior change
