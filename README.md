# Brightness Controller

One slider for every screen on your Mac — including external monitors.

Most Macs give you a brightness slider for the built-in display and nothing for
the monitors plugged into it. This is a small menu bar app that controls all of
them together, and keeps them *matched* rather than just moving them by the same
amount.

**This repository is the download and issue tracker. The source is not public.**

---

## Install

1. Download the latest `Brightness Controller.zip` from
   [Releases](../../releases).
2. Drag the app into your Applications folder and open it.
3. The first time, macOS may refuse to open it. Go to
   **System Settings → Privacy & Security**, find the note about Brightness
   Controller, and click **Open Anyway**. You only do this once.
4. A sun icon appears in your menu bar. That's the app — no Dock icon, no window.

**Requirements:** a Mac with Apple Silicon (M1 or later) and macOS 14 or newer.

---

## How it works

Every monitor has its own slider, and a **master** slider moves all of them
together.

The point is *matched* brightness, not identical numbers. Monitors differ in how
bright and how dim they can physically go, so there's a natural give and take:
your least-dimmable monitor sets how dark the set can get, and your least-bright
one sets how bright it can get. The master travels only across the range where
your monitors genuinely stay together.

Two ways to match them:

- **Proportional** — one level per monitor, they dim toward black together.
  Nothing to set up.
- **Calibrated** — dim the room and set each monitor by eye, then come back when
  it's bright and set them again. The app remembers both and blends between them
  as the light changes. Make the two passes in genuinely different light, or it's
  guessing about everything in between.

**Auto-follow** ties the whole set to your MacBook's ambient light sensor, so
when the built-in display adjusts itself, the external monitors move with it.

---

## Will it work with my monitor?

Depends on the monitor and, annoyingly, on the cable.

- **USB-C / Thunderbolt / DisplayPort** usually work.
- **HDMI** is less reliable, and on some Macs the built-in HDMI port cannot do
  monitor control at all.
- Some monitors ship with **DDC/CI turned off** in their own on-screen menu —
  turn it on and try again.
- Some monitors only accept brightness commands in their **Custom / Standard**
  picture mode, not in Game or Movie presets.
- Cheap hubs, dongles and KVMs often block the control signal entirely.

If a monitor can't be controlled, its slider shows a `≈` and stays put. Nothing
breaks — that monitor just isn't reachable this way.

**Please [open a monitor report](../../issues/new?template=monitor-report.yml)
whether it works or not.** Reports are how the compatibility list gets built.

---

## Privacy

The app has no account, no login, and sends nothing anywhere by default.

It keeps a plain-text diagnostic log at
`~/Library/Logs/Brightness Controller.log` recording what it changed and why,
so you can see exactly what happened while you were away. That file never
leaves your Mac.

---

## Something looks wrong?

- **A slider shows `≈`** — the app couldn't read that monitor. Move the slider
  once and it takes over from there.
- **Everything says 100% but the screen is dim** — your monitor's own hardware
  brightness is a separate knob that multiplies with this one. Turn it up with
  the buttons on the monitor.
- **Brightness changed while I was away** — open the diagnostic log above. Every
  change is timestamped with its cause.
- **The icon disappeared** — the app was quit. Reopen it from Applications.

Still stuck? [Open an issue](../../issues/new/choose) and attach the log.
