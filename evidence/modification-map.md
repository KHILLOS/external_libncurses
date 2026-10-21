# Modification Map: external/libncurses

## Source: BlissOS android-x86 reference (external/libncurses)
- BlissOS reference: android-x86/external/libncurses (ncurses 6.4 with patches)
- UPSTREAM commits:
  - bf11a058 (Patch ncurses 6.4: TERM default 'linux' + AUTO_SRC config.status dependency)
  - 5a6189b2 (Android.bp: add Soong build for libncurses - KhillOS port)
  - 87c2c84c+ (ncurses 6.4 patches from upstream)
- Upstream base: ncurses 6.4 (invisible-island.net)

## Modifications Applied to UPSTREAM/external_libncurses (khillos-17 branch)

### 1. Android.bp Build System (COMPLETE REWRITE)
**Replaced with BlissOS-compatible Soong build (based on BlissOS Android.bp):**
- `genrule` libncurses_gen - generates sources/headers via configure/make
- 4 sub-genrules for source/header splitting
- `cc_defaults` libncurses_defaults with comprehensive source patterns
- `cc_library_shared` libncurses (vendor/host/recovery)
- `cc_library_shared` libncurses_recovery (recovery: true)
- `cc_library_static` libpanel (vendor/host)
- `cc_library_static` libmenu (vendor/host)
- `cc_library_static` libform (vendor/host)
- `cc_binary` tput (vendor/host/recovery)
- License module: external_libncurses_license (MIT, COPYING)

### 2. Source Code Patches (From BlissOS commits)
**Files modified in commit bf11a058:**
- TERM default 'linux' configuration
- AUTO_SRC config.status dependency fixes
- Various ncurses 6.4 patch integrations (20230311 through 20221105)

### 3. AOSP 17 Compliance Metadata Files (NEW)
**Files:** `METADATA`, `MODULE_LICENSE_MIT`, `OWNERS`, `NOTICE`
- METADATA: Package metadata per AOSP external_updater format
- NOTICE: Comprehensive MIT license notice with copyright
- MODULE_LICENSE_MIT: SPDX identifier for Soong license module
- OWNERS: Standard AOSP OWNERS file

### 4. SPDX Headers (NEW)
**All 423 .c/.h files:** Added SPDX-License-Identifier: MIT after first comment block

## Summary
- **Total files modified:** 423 source files + Android.bp + 4 metadata = 428
- **Source files:** 423 .c/.h files with SPDX headers added
- **Build system:** Complete Android.bp rewrite matching BlissOS structure
- **Logic/behavior changes:** ncurses 6.4 patches + TERM default fix from BlissOS
- **AOSP 17 compliance:** All required metadata files added
