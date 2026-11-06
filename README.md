# Poly Octave

A POG-style polyphonic octave generator for guitar, written as a REAPER JSFX.
Unlike an OC-2-style divider (see Divider Synth), it shifts chords as chords.

## How it works

The guitar is split into 31 bands (60 Hz – 4 kHz) using complex resonators.
In each band the octave is computed directly from the band's analytic signal:

- **−1 octave:** square root, with phase continuity
- **−2 octaves:** square root again
- **+1 octave:** squared

Each band holds roughly one partial, so every note of a chord is shifted independently.

## Latency

No lookahead and no reported plugin latency (nothing is added to REAPER's PDC).
The band filters need about 5–15 ms to respond, slowest on the lowest notes.
The **Response** control trades speed against chord separation.

## Install

1. In REAPER: Options → Show REAPER resource path.
2. Copy `Poly Octave.jsfx` into the `Effects` folder.
3. In the FX browser press F5 and search for **Poly Octave**.

## Controls

| Control | What it does |
|---|---|
| Input Gain | Level into the band bank |
| Gate Threshold | Stops hum and noise from producing octaves |
| Dry Guitar | Original signal, untouched |
| −1 Octave / −2 Octaves / +1 Octave | Level of each octave voice |
| Tone | Low-pass on the octave voices |
| Drive | Saturation on the octave voices only |
| Response | Lowest band width: higher is faster, lower gives cleaner chords |
| Output | Final level |
| Preset | POG Organ, Bass Chords, 12-String Shimmer, Fuzz Octaves (automatable) |

## Tips

- Expect an organ-like, smooth octave rather than a square-wave synth.
  For aggressive single-note synth sounds, use Divider Synth.
- Put drive or an amp after Poly Octave for grittier chords.

## License

MIT. See [LICENSE](LICENSE).
