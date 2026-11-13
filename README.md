# Project Atlas

**Your phone as a remote for your Windows PC or Mac**: touchpad, keyboard, media controls, your
apps, a game controller, PC status, files and clipboard. It works over your home Wi-Fi; nothing
goes through the internet.

## Download

Get the newest version from **[Releases](../../releases/latest)**:

| File | For |
|---|---|
| `Atlas-Setup-<version>.exe` | Windows 10 / 11 (64-bit) |
| `Project-Atlas-Mac-<version>.zip` | Mac with macOS 13.5 (Ventura) or newer, Apple chip or Intel |
| `INSTALL-TEST-MANUAL.md` | Step-by-step install and test guide, also for AI assistants |

The files aren't signed yet, so Windows and macOS warn you the first time. The steps below show
how to get past that.

## Install on Windows

1. Run **Atlas-Setup-&lt;version&gt;.exe**. If Windows says "Windows protected your PC": **More info →
   Run anyway**. Then **Install**. No admin rights needed.
2. The **PC page** opens in your browser. Follow its 3 steps:
   1. **Let phones reach this PC.** Windows asks for permission once; choose **Yes**.
   2. **A free name for this PC (optional, recommended).** Create a free account at
      [duckdns.org](https://www.duckdns.org), add a name, and paste the name and token on the PC page.
      Keep the token to yourself; it's like a password.
   3. **Pair your phone.** Scan the QR code with the phone (same Wi-Fi).
3. On the phone: install the Atlas app when the page offers it (Android), or use the page in the
   browser and add it to the home screen.

Atlas then runs as an icon next to the clock (double-click: the PC page; right-click: **Stop Atlas**)
and starts when you sign in.

**Update:** run a newer Atlas-Setup.exe. Your paired phones and settings stay.
**Remove:** Settings → Apps → **Project Atlas** → Uninstall.

## Install on a Mac

1. Double-click the zip. Drag **Project Atlas** into **Applications** and open it.
2. macOS asks the first time, because the app isn't signed yet:
   - **macOS 15 or newer:** **Done** → System Settings → **Privacy & Security** → scroll down →
     **Open Anyway**.
   - **macOS 13 / 14:** right-click the app → **Open** → **Open**.
   - It says the app is **"damaged"**? In Terminal: `xattr -cr "/Applications/Project Atlas.app"`,
     then open it again.
3. The PC page opens in the browser. There's no window or Dock icon; Atlas runs in the background.
4. **Allow Atlas to control the Mac:** System Settings → **Privacy & Security → Accessibility** →
   switch on **Project Atlas** (it may be called **node**). Then **Stop Atlas** on the PC page and open
   the app again.
5. Pair the phone with the QR code on the PC page.

**Remove:** turn off "Start with the Mac" on the PC page, **Stop Atlas**, then drag the app to the Trash.

## Let phones reach this PC (by hand)

Only needed if step 1 on the PC page didn't work (Windows):

1. Start menu → type `powershell` → right-click **Windows PowerShell** → **Run as administrator**.
2. Mark your home Wi-Fi as Private (replace `Wi-Fi` if your connection has another name):
   ```
   Set-NetConnectionProfile -InterfaceAlias "Wi-Fi" -NetworkCategory Private
   ```
3. Allow Atlas through the firewall on private networks:
   ```
   New-NetFirewallRule -DisplayName "Project Atlas (port 3000)" -Direction Inbound -Protocol TCP -LocalPort 3000 -Action Allow -Profile Private
   ```

Only mark networks as Private if you trust them (your home, not a café).

## Something doesn't work?

| Problem | Try |
|---|---|
| The phone can't open the page | Same Wi-Fi on both? Was "Let phones reach this PC" done on this network? |
| "Your connection is not private" on the phone | Do step 2 on the PC page (free name), then scan the QR code again |
| The pointer doesn't move (Mac) | Accessibility permission (Mac step 4), then restart Atlas |
| The phone asks to pair again | It was removed or not used for a long time; scan the QR code again |
| Xbox controller in the Console tab doesn't work | PC page → **Xbox controller driver** → Download, install it, restart Atlas |

To report a problem, use `INSTALL-TEST-MANUAL.md` from the release: it lists checks and a report
format. You can hand it to an AI assistant together with the download.

## Privacy

Atlas only works inside your home network. Phones must be paired with a code from your PC before
they can do anything. Your settings stay on your computer.
