# NOIR & BLOOM

A responsive, cinematic fragrance boutique built with Vite, semantic HTML, CSS, GSAP ScrollTrigger.

## Run locally

Requires Node.js 20.19+ or 22.12+.

```sh
npm ci
npm run dev
```

Open the Local URL printed by Vite. To produce and inspect the static build:

```sh
npm run build
npm run preview
```

Deploy the contents of `dist/` to any static host (Netlify, Cloudflare Pages, Vercel, or an ordinary web server). No backend or environment variables are required. Use `npm run build` as the build command and `dist` as the output folder.

## Animation architecture

The alchemy scene uses a pinned GSAP scrubbed timeline over 2.6 viewport heights. A single normalized progress value drives five separate photographic cutouts: the amber bottle body, detachable ribbed cap, Damask rose, bergamot and sandalwood. GPU transforms animate reversible cap lift, subtle perspective framing and independent ingredient parallax. A masked reflection sweep travels across the glass; notes crossfade on the same timeline. This is a layered photographic composition, not a real-time 3D mesh or filmed video.

Original generated sprite sheets preserve independent object layers. No WebGL is required. The scene uses CSS compositing and GSAP, with all positions derived directly from scroll progress, so scrolling upward retraces the same animation. Media and fonts are refreshed after load. Desktop and mobile framing use different scale and lift distances. Reduced motion keeps the cap attached and ingredients still while displaying all scent notes. The visible motion toggle supports persistent opt-in and pause; explicit `?motion=full` selects the cinematic preview.

## Interactions

Collection filters, product details, shopping bag quantity controls, persistent browser-local bag, native accessible modal dialogs, newsletter validation, privacy and terms are implemented. Product descriptions and prices are illustrative USD content. Checkout displays a clear concept-store message; it does not take payment. The newsletter is a preview and sends no data. The contact address uses the reserved `.example` domain. Replace these with real commerce, mailing-list, legal and contact services before commercial launch.

## Assets

`public/assets/campaign.jpg` and `public/assets/bottle.png`, `cinematic-bottle.png` and `cinematic-ingredients.png` are original AI-generated campaign/product imagery for this project. Atmospheric overlays and discovery packaging illustrations are authored in code. Typography uses Cormorant Garamond and Manrope from Google Fonts with local system fallbacks. GSAP is bundled, not fetched at runtime. Hero artwork is eagerly preloaded.

## Verification

Browser QA covers the initial hero, pinned scene progression, reversal, top/bottom restoration, product filtering, product dialogs, shopping bag operations, newsletter preview, phone-width composition, viewport resizing and reduced-motion layout. See `QA.md` for results and practical limitations.

For the cinematic local preview, open `http://127.0.0.1:5174/?motion=full` (adjust the port to match Vite). The explicit URL enables motion and saves that choice. New localhost previews default to full motion unless the visitor explicitly paused it. Hosted sites continue to honor system reduced motion by default.
