# Cinny desktop (Lndr fork)

This is a personal fork of [cinnyapp/cinny-desktop](https://github.com/cinnyapp/cinny-desktop) with a few changes. Frontend changes live in [Lndr2501/cinny](https://github.com/Lndr2501/cinny).

## What's different

- **Voice chat works on macOS.** WebKit's media devices are switched on, so joining a voice room no longer hangs.
- **Screen sharing stays sharp** while Cinny is in the background (no throttling).
- **Screen-share sound (macOS).** System audio is captured natively and sent with the stream; there is an on/off button in the call bar. Cinny's own call audio is excluded, so nobody hears an echo.
- **Deafen mutes mic and sound together** and restores the mic when you undeafen.
- **Join All Rooms / Auto-Join Rooms** in the space menu: join every room of a space with one click, or automatically whenever new rooms appear.
- The built-in updater is off, so the app never replaces itself with the upstream version.

## Install

Download the latest build from the [Releases page](https://github.com/Lndr2501/cinny-desktop/releases).

**macOS** (`.dmg`: `aarch64` for Apple Silicon, `x64` for Intel)
1. Open the `.dmg` and drag Cinny to Applications.
2. The app is not notarized. Run once: `xattr -cr /Applications/Cinny.app`
3. Start it and allow Microphone and, for stream sound, *Screen & System Audio Recording*.

**Linux** (`.AppImage` or `.deb`)
- AppImage: `chmod +x Cinny_*.AppImage && ./Cinny_*.AppImage`
- Debian/Ubuntu: `sudo apt install ./Cinny_*.deb`
- Voice and video calls do not work on Linux yet: WebKitGTK has no WebRTC ([upstream #545](https://github.com/cinnyapp/cinny-desktop/issues/545)). Chat and the space features work.

Build it yourself: see *Local development* below.

---

# Cinny desktop (upstream readme)

<a href="https://github.com/cinnyapp/cinny-desktop/releases">
  <img alt="GitHub release downloads" src="https://img.shields.io/github/downloads/cinnyapp/cinny-desktop/total?style=social"></a>

Cinny is a matrix client focusing primarily on simple, elegant and secure interface. The desktop app is made with Tauri.

## Download (upstream)

Installers for macOS, Windows and Linux can be downloaded from [Github releases](https://github.com/cinnyapp/cinny-desktop/releases). Releases are signed with a [Ed25519](https://ed25519.cr.yp.to/) public-key.

Operating System | Download
---|---
Windows | <a href='https://github.com/cinnyapp/cinny-desktop/releases/latest/download/Cinny_desktop-x86_64.msi'>Cinny.msi</a> · <a href='https://scoop.sh/#/apps?q=cinny'>Install via Scoop</a>
Windows ARM64 | <a href='https://github.com/cinnyapp/cinny-desktop/releases/latest/download/Cinny_desktop-aarch64.exe'>Cinny.exe</a>
macOS | <a href='https://github.com/cinnyapp/cinny-desktop/releases/latest/download/Cinny_desktop-universal.dmg'>Cinny.dmg</a> · <a href='https://github.com/cinnyapp/cinny-desktop/releases/latest/download/Cinny_desktop-universal.app.tar.gz'>Cinny.app</a>
Linux | <a href='https://github.com/cinnyapp/cinny-desktop/releases/latest/download/Cinny_desktop-x86_64.AppImage'>Cinny.AppImage</a> · <a href='https://flathub.org/apps/details/in.cinny.Cinny'>Flatpak</a>

Decoded public key:
> RWRflTUQD3RHFtn25QNANCmePR9+4LSK89kAKTMEEB4OKpOFpLMgc64z

To verify release files, you need to download [minisign](https://jedisct1.github.io/minisign/) tool and [decode](https://www.base64decode.org/) the *.sig* file before running:
>  minisign -Vm ***RELEASE_FILE.msi.zip*** -P RWRflTUQD3RHFtn25QNANCmePR9+4LSK89kAKTMEEB4OKpOFpLMgc64z -x ***Decoded_SINGATURE.msi.zip.sig***

## Local development

Firstly, to setup Rust, NodeJS and build tools follow [Tauri documentation](https://v2.tauri.app/start/prerequisites/).

Now, to setup development locally run the following commands:
* `git clone --recursive https://github.com/cinnyapp/cinny-desktop.git`
* `cd cinny-desktop/cinny`
* `npm ci`
* `cd ..`
* `npm ci`

To build the app locally, run:
* `npm run tauri build`

To start local dev server, run:
* `npm run tauri dev`

## License
Cinny Project  
Copyright © 2024–present Ajay Bura  
https://cinny.in  

Cinny is licensed under the GNU Affero General Public License, 
Version 3 of the License (AGPL-3.0-only).
You may obtain a copy of the License at https://www.gnu.org/licenses/agpl-3.0.html
