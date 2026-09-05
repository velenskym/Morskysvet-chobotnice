# Octopus kiosk — ZOO Sea World Prague

A touchscreen application running beside the octopus tank at ZOO Mořský svět (Sea World Prague), the Czech Republic's only public marine aquarium.

**Live:** https://velenskym.github.io/Morskysvet-chobotnice/
**Try it in a simulated kiosk screen:** https://velenskym.github.io/morskysvet-euac/

Plain HTML, CSS and JavaScript. No framework, no build step, no server. Hosted free on GitHub Pages, displayed by Chromium in kiosk mode on a small Linux box next to the glass.

---

## The exhibit

*Octopus vulgaris* — the common octopus. The application answers the three questions visitors actually ask at the glass: what is it, what can it do, and how did a mollusc end up this intelligent.

## Pages

| File | What it is |
|---|---|
| `index.html` | Home — hero and three cards |
| `druh.html` | The species: who it is, where it lives, why it is remarkable |
| `superschopnosti.html` | "Superpowers" in nine sections — intelligence, arms and suckers, the eye, colour change (microscopy video of chromatophores), mimicry, mimesis, hunting, the soft body, and escapes from aquariums |
| `hlavonozci.html` | The other cephalopods — nautilus, cuttlefish, squid — with full-screen photography |

Both languages live in the same files: every text node carries `data-cs` and `data-en` attributes and one function swaps them. The visitor's choice is remembered in `localStorage`.

## Video, deliberately not from YouTube

The videos are ordinary MP4 files in `videos/`, played inline with `autoplay muted loop playsinline` and `preload="none"`. Embedding them from YouTube was the first approach and it was worse in every way that matters in an exhibition: it needs a good connection, it shows branding and related-video overlays, and a visitor can click through and leave the application entirely. Local files have none of those problems.

Each video and photograph has a "⛶ full screen" button that opens a black full-viewport overlay — the one app-like gesture visitors get, and it is discoverable without instruction.

## Built for one specific screen

Authored at a fixed 1920×1080 layout and scaled with CSS to the tablet's 1366×768 panel. There is exactly one screen to support, so there is no responsive CSS in the project.

The practical consequence: **opening `index.html` on a laptop or a phone will not look right.** To see it as a visitor does, use the [kiosk simulator](https://velenskym.github.io/morskysvet-euac/), which frames the app at its native resolution and scales the whole frame to fit your screen.

## Running it locally

```bash
git clone https://github.com/velenskym/Morskysvet-chobotnice.git
cd Morskysvet-chobotnice
python3 -m http.server 8000
```

Then open http://localhost:8000 in a browser window sized to 1366×768 (in Chrome: DevTools → device toolbar → set a custom 1366×768 device).

## Reusing this for your own institution

You are welcome to. The code is MIT-licensed; the photographs, video and texts are not — see [LICENSE](LICENSE).

- **The machine underneath it** — Lubuntu with Openbox, autologin, Chromium kiosk flags, a watchdog and automatic power-off at closing time — is documented in [KIOSK-SETUP.md](https://github.com/velenskym/morskysvet-euac/blob/main/KIOSK-SETUP.md), including the mistakes that cost us the most time.
- **The design system** shared by all four kiosks is described in the same document.
- The three sister applications: [jellyfish](https://github.com/velenskym/Morskysvet-meduzy), [Great Barrier Reef](https://github.com/velenskym/Morskysvet-GBR), [Raja Ampat](https://github.com/velenskym/Morskysvet-kiosk).

## Contact

Mikuláš Velenský — Curator, ZOO Sea World Prague
velenskym@gmail.com · [morskysvet.cz](https://www.morskysvet.cz) · [github.com/velenskym](https://github.com/velenskym)

Shared with the EUAC community. If you build something from this, I would like to hear about it.
