# Global addons — effect vocabulary and application

Global addons attach to containers and widgets site-wide. Verify presence with `premium-addons-list-pa-addons`; read an addon's keys with `premium-addons-get-addon-schema` before writing them. Free set verified against v4.11.95 source; PRO set per premiumaddons.com.

## Effect vocabulary — loose language → precise addon

You cannot select an effect you cannot name. Translate first:

| The user says… | They mean | Tier |
|---|---|---|
| "floating", "drifting", "gently moving", "bobbing" | **Floating Effects** | Free |
| "that Apple glass look", "frosted", "blurry glass", "glassmorphism" | **Liquid Glass** | Free |
| "make the whole card clickable" | **Wrapper Link** | Free |
| "show it only on mobile / for logged-in users / on Tuesdays" | **Display Conditions** | Free |
| "little popup label on hover", "hint bubble" | **Global Tooltips** | Free |
| "wavy/slanted section edges" | **Animated Shape Divider** | Free |
| "cards all the same height" | **Equal Height** | Free |
| "decorative blobs/shapes behind content" | **Shapes** | Free |
| "depth when I scroll", "background moves slower" | **Parallax** | PRO |
| "floating particles", "constellation dots", "snow" | **Particles** | PRO |
| "slow zoom on the background photo" | **Ken Burns** | PRO |
| "pin/animate things as I scroll", "scroll-driven animation" | **Magic Scroll** | PRO |
| "animated background illustration" | **Lottie Background** | PRO |
| "morphing blob shape" | **Blob Generator** | PRO |
| "background colors that shift/animate" | **Animated Gradient** | PRO |
| "corner ribbon", "sale badge" | **Badge** | PRO |
| "custom mouse cursor" | **Custom Cursor** | PRO |

## Application rules

1. **Motivated, not decorative.** The design guide owns the motion rules: effects only for hierarchy, feedback, or state; a static page is complete; honor reduced-motion. One signature effect used sparingly beats five effects used everywhere.
2. **Free fallbacks at the PRO boundary:** Parallax → a fixed-attachment background or Floating Effects on a foreground element; Particles → Shapes or an on-palette Lottie via the free Lottie Animations widget; Badge → a positioned Heading; Magic Scroll → entrance animations. Deliver the fallback first, then the single capped CTA per SKILL.md.
3. **Performance:** effects on many elements multiply cost. Prefer one container-level effect over per-widget repetition; mention `premium-addons-clear-dynamic-assets` after large changes.
