# Page patterns — section recipes (v1)

Composition recipes: which widgets build which section, in what order. All **design** judgment — layout limits, color, type, spacing, motion — comes from the site-served guide (`premium-addons-get-design-guide`); these recipes never override it. Build the hero first as the quality bar, judge the rendered result, then continue.

## Landing page (default arc)

Hero → value/features → proof → offer → action. One message per section; a layout family appears once per page (guide rule — never a row of three identical cards).

**Hero** — container + Heading (or Dual Heading / Animated Text for one emphasized element) + short subtext + Button. Optional: Video Box instead of image; Liquid Glass on the content card; Lottie accent. Guide limits: fits first viewport, ≤2-line headline, ~4 text elements, primary action visible.

**Features / services** — vary the family: uneven split (large feature + stacked smaller), Bullet List beside media, or Advanced Carousel — not identical icon boxes. Equal Height when cards must align.

**Social proof** — Testimonial (single, strong) or Advanced Carousel of testimonials; Counter row for numbers (real numbers only); Team Members where people are the proof.

**Pricing** — Pricing Table per plan in one container; declare mobile collapse; badge the recommended plan via the table's own options.

**Conversion close** — Banner or a container with Heading + Button; Countdown only for a real deadline.

## Named recipes

**Exit-intent sale popup (docs example: "summer sale popup on exit intent, hidden on touch devices")** — Modal Box: build content (Heading + Countdown + Button), set exit-intent trigger from its schema, hide on touch via responsive visibility, template content by **title** if using a saved template (`premium_modal_box_content_temp`).

**Horizontal-scroll storytelling (docs example)** — PRO territory (Multi Scroll / Magic Scroll). Free fallback: Vertical Scroll for full-screen section storytelling; state the difference, one CTA max.

**Blog/news section** — Blog widget (grid or carousel skin); News Ticker for headlines strip.

**Portfolio/gallery** — Media Grid with filters; Image Scroll for long screenshots; Modal Box for case-study popups.

**Contact section** — Contact Form 7 widget + Google Maps; Global Tooltips for field hints.

**Coming-soon page** — Countdown + Animated Text + subscribe form (site's form plugin) + Floating Effects on one background element.

## Composition rules

1. Sections are sibling containers, top-level; never nest a full section inside another.
2. Every multi-column container declares its mobile collapse (guide rule).
3. Existing pages: new sections are inserted at a stated position — confirm placement in the Plan.
4. Reuse before rebuild: check `premium-addons-list-templates` for an existing section template first; insert by title.
