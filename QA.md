# Browser verification — 9 October 2026

Verified in the Codex Chromium-based browser at desktop width and a 390 × 844 phone viewport.

- Hero: original imagery loaded; headline, navigation, CTA and scroll cue visible.
- Scroll animation: one pinned section present in normal motion mode. At 800 pixels into the scene, progress settled at 0.3607. Moving farther advanced progress; reversing to the earlier position restored the earlier frame. Cap separation, bottle rotation, lighting, ingredient position and notes changed together. Scrub smoothing may briefly interpolate toward the final value after a rapid scroll.
- Composition: corrected cap travel after observing clipping during the camera close-up. Reduced mobile cap separation and ingredient scale to preserve title space.
- Deterministic reversal: the same position restored progress 0.4959 after jumping to the footer (progress 1.0000); returning to the top restored 0.0000. Final cap framing remained fully inside the viewport.
- Navigation and release: collection, ritual, closing and footer remain accessible after the pinned scene. Returning to the top restores the hero. Rapid jumps and direction changes did not produce a stuck state.
- Responsive layout: desktop-to-phone resize refreshed renderer dimensions and pin measurements. No horizontal overflow at 390 pixels. Phone layout is portrait-readable. Scrolling was tested through browser input; physical iOS/Android touch testing has not been performed.
- Reduced motion: no pin spacer, no atmospheric animation, and all three notes have opacity 1. Essential content remains available.
- Collection: discovery filter showed one product; product details dialog opened correctly.
- Shopping bag: added discovery set, persisted through reload, incremented to two items/$70, decremented and removed to the empty state. Test bag was cleared through normal controls.
- Newsletter: valid email produces an explicit preview confirmation and does not submit data.
- Dialogs: close buttons and native modal focus behavior work. Escape uses native dialog support.
- Console: no application errors observed during initial and interactive checks.
- Build: `npm run build` succeeds; all imagery and locally bundled animation dependencies included in `dist/`.

## Limits

The 3D scene is an authored stylized real-time render, not a filmed or pre-rendered video. The campaign and collection cutout are original generated photography. Fragrance variants share a tinted concept bottle render. Contact details, product information, checkout and newsletter are illustrative and require production business data/services. Font requests use Google Fonts with system fallbacks. WebGL failure displays static imagery; this code path was reviewed but not forced on a real unsupported device. Physical device performance and Safari have not been tested.

## Motion preference fix

The in-app browser reports `prefers-reduced-motion: reduce`, which selected the static accessibility layout. Added a visible motion toggle backed by a browser-local preference and a reversible GSAP context. Verified default reduced state has zero pins, explicit enable has one pin, forward progress changes from 0.5342 to 0.9081 and reverse restores 0.5342. Verified pause, resume and persistence through reload without changing system preferences.

## Explicit cinematic preview

The original app tab stopped responding to browser inspection/navigation. Opened an explicit `?motion=full` preview and verified actual browser scrolling, rather than programmatic scroll alone: down two pages reached about 6%, another page reached 44%, and upward scrolling reversed toward 6%. Captured before/after frames in `output/scroll-before.png` and `output/scroll-after.png`. Added visible story progress to distinguish live animation from the static layout.

## Photorealistic scene update

Replaced the stylized mesh scene with independently composited generated photographic bottle, cap, rose, bergamot and sandalwood cutouts. Preserved the pinned bidirectional GSAP timeline, ingredient parallax, reflection sweep, motion toggle and reduced-motion layout. Removed the WebGL dependency from the build. Earlier mesh-specific checks above document the previous implementation.

Photographic scene browser checks passed: scrolling upward from the collection restored the animated composition; cap separates visibly; realistic image layers remain aligned; phone viewport 390×844 shows no horizontal overflow and title/notes remain clear of the objects. Production build passes with the WebGL bundle removed.

## Ritual image correction — 10 October 2026

Replaced the zoomed campaign background with the complete bottle cutout using object-fit contain. Bottle uses 70% of panel height, reserving room for its ±9% parallax travel; background moves in the opposite direction and the light layer travels independently. Verified the full cap and base remain visible. Browser scroll changed the bottle translation from 0.11859px to 27.1209px; reversing restored 0.11859px. Reduced-motion mode keeps all layers static. Build passes.

## First-fold cover transition — 10 October 2026

Moved the header inside the hero so the whole first fold pins together. Added a no-spacing hero ScrollTrigger pin for one hero height, with opaque subsequent scenes on a higher stacking layer. Removed hero content fading and image drift during coverage. At scroll 426.5px the hero top remained 0 and intro top was 426.5px; at 853px the intro reached 0. Upward scrolling restored partial coverage. The introduction fills at least one viewport so it can cover the complete hero. Reduced-motion/paused mode retains normal document scrolling.

## Desktop hero framing — 10 October 2026

Removed desktop background zoom and changed the campaign background from cover to contain, right-centered over a matching dark fill. Verified full cap, bottle base and campaign composition at 1456×853. Hero pin and cover transition remain unchanged. Mobile retains its separately composed background treatment. Production build passes.

## Mobile hero framing — 10 October 2026

Changed the mobile campaign background to auto 66% sizing, positioned near the top, with a dark gradient behind the copy. Removed background scaling and adjusted the headline and content placement. Verified at 393×852: the bottle cap and base are visible, headline and CTA remain readable, and there is no horizontal overflow. Desktop framing is unaffected. Production build passes. Screenshot: output/hero-mobile-corrected.png.
