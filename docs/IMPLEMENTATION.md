# Implementation notes

## Design goals

- One original short (8 seconds), generated from a constrained shot sheet.
- 1920 × 1080 at 24 fps (192 frames).
- A fixed ten-color "Vermilion eclipse" palette.
- Three shots with one action-heavy sequence; no voice, titles, or music.
- A deterministic, seekable HTML/SVG + GSAP animation compatible with HyperFrames.

## Timeline

| Shot | Start | End | Notes |
| --- | ---: | ---: | --- |
| Establish | 0.00 s | 2.40 s | Small rooftop figure; 100%–106% camera move; rain |
| Sakuga | 2.40 s | 6.00 s | Sword draw, anticipation, two single-frame smears, settled hold |
| Button | 6.00 s | 8.00 s | Close-up, short blink, final fade |

The shot transition at 2.40 s falls between two display frames (2.40 × 24 = 57.6). It is covered by a full-frame color dip. Do not claim this cut is on an exact integer frame.

The project is authored as a single HTML composition with `data-composition-id="film"` and a paused GSAP timeline registered under `window.__timelines["film"]`.

## Animation methods

- **Held drawings:** limited unique poses provide anime-like stepped character action rather than continuous interpolation.
- **Sakuga:** one designated action shot concentrates most of the drawing budget.
- **Smear frames:** the blade sweep uses brief distorted drawings to imply speed.
- **Rain:** deterministic paths and finite loops rather than random values at capture time.
- **Color dips:** full-frame overlays conceal shot transitions, rather than fading characters into a scene.

## Fixes made during development

A read-only audit found rain tweens that outlived their source clips and extended the timeline beyond 8 seconds. The helper was adjusted to distribute a finite number of loops over each clip duration:

| Rain layer | Start | Duration | End |
| --- | ---: | ---: | ---: |
| Establish | 0.00 s | 2.40 s | 2.40 s |
| Sakuga | 2.15 s | 3.85 s | 6.00 s |
| Closing | 5.75 s | 2.25 s | 8.00 s |

A one-millisecond lead for drawing swaps was retained to reduce ambiguity around exact-frame seeking; this is an implementation choice, not a guarantee against every floating-point edge case.

## Test evidence

HyperFrames `0.8.210` `lint` and `check --snapshots` were used during development. The observed results were:

- `check`: passed.
- `lint`: 0 errors / 5 warnings (file length and nested composition structure).
- `runtime`: 0 errors / 0 warnings.
- `motion`: 0 errors / 0 warnings.
- `craft`: 0 errors / 0 warnings.
- `layout`: 0 errors / 3 overflow warnings and 7 informational observations.
- `audio`: no audio, as designed.

The specific file and environment tested were local development copies. These results are an honest record of the initial test, not a CI badge or a promise of future compatibility. Raw diagnostic logs and machine-specific paths are deliberately not published.

## Artistic limitations

The project uses flat vector artwork, not detailed hand-drawn illustration or video diffusion. The result is a stylized experiment rather than a high-fidelity animated film. Future work could improve poses, character design, or lighting while preserving reproducibility.
