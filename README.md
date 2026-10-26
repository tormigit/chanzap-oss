# Chanzap open-source components

[Chanzap](https://chanzap.com) is a media player for Windows by seljeSoft (Seljenes Konsult, org. no. 930 629 499,
Norway). It plays video through **libmpv**, which contains **FFmpeg** and other libraries licensed under the GNU Lesser
General Public License (LGPL). This repository provides the complete corresponding source code of those libraries, as the
LGPL requires.

Chanzap's own code is not open source. Everything listed here is used unmodified.

## The library

Chanzap ships `libmpv-2.dll` next to `chanzap.exe`. It is the prebuilt
`mpv-dev-x86_64-20230924-git-652a1dd.7z` from the media-kit project
([release 2023-09-24](https://github.com/media-kit/libmpv-win32-video-build/releases/tag/2023-09-24)), used by the
media_kit Flutter package. It is built **without** GPL or non-free parts (`gpl=false` for mpv; FFmpeg
`--disable-gpl --disable-nonfree --enable-version3`).

## Source code

The exact sources are attached to the [release](../../releases) of this repository, with SHA-256 checksums:

| Component | Licence | Version in the DLL | Archive |
| --- | --- | --- | --- |
| mpv | LGPL-2.1-or-later | v0.36.0-403-g652a1dd907 | `mpv-652a1dd90711839acdccc08004056d25514ef2d8.tar.gz` |
| FFmpeg | LGPL-3.0-or-later (built with `--enable-version3`) | n6.0 (commit ea3d24bb) | `ffmpeg-ea3d24bbe3c58b171e55fe2151fc7ffaca3ab3d2.tar.gz` |
| GNU FriBidi | LGPL-2.1-or-later | commit 4fc34ed7 | `fribidi-4fc34ed77ee985c19acb818dee1ed27054ddd434.tar.gz` |
| uchardet | MPL-1.1 / GPL-2.0 / LGPL-2.1 (used under LGPL-2.1) | commit ab1d2f11 | `uchardet-ab1d2f1120297af6537f2a0d09dca589d4c3ea3b.tar.gz` |
| SoX Resampler (libsoxr) | LGPL-2.1-or-later | commit 945b592b | `soxr-945b592b70470e29f917f4de89b4281fbbd540c0.tar.gz` |
| Build scripts (media-kit/libmpv-win32-video-build) | GPL-3.0 (scripts) | commit f5a6f879 (the build of 2023-09-24) | `libmpv-win32-video-build-f5a6f879c9b8bef6a73e52c8c0f35e51636c96e5.tar.gz` |

The build scripts fetched FriBidi, uchardet and libsoxr from their main branches on the build date; the archives are those
branches' last commits before 2023-09-24. FFmpeg and mpv versions are read from the shipped DLL.

The DLL also contains libraries under permissive licences, credited in Chanzap under Settings → About → Licenses:
libass (ISC), HarfBuzz (MIT), FreeType (FreeType License; portions of this software are copyright © The FreeType
Project, www.freetype.org), dav1d (BSD-2-Clause), Mbed TLS (Apache-2.0), Little CMS (MIT), zimg (WTFPL), libxml2 (MIT),
shaderc and SPIRV-Cross (Apache-2.0), libjxl (BSD-3-Clause), libwebp (BSD-3-Clause), Speex (BSD-3-Clause),
libmysofa (BSD-3-Clause), libbs2b (MIT), Intel VPL and AMF headers (MIT), and the nv-codec-headers (MIT).

## Replacing the library

`libmpv-2.dll` is loaded dynamically from Chanzap's install folder. You may replace it with your own build of the same or
a compatible libmpv version, for example built from the sources above with the media-kit build scripts.

## Written offer

If a link here stops working, email **hello@chanzap.com** and we will send the complete corresponding source code of
these components for at least three years after the last Chanzap release that includes them, for no more than the cost
of providing it.

## Licence texts

See [LICENSES](LICENSES): GNU LGPL 2.1, GNU LGPL 3.0 and GNU GPL 3.0 (which LGPL 3.0 builds on).
