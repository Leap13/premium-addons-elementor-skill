# Widget selection — intent → Premium Addons widget

Catalog verified against Premium Addons free v4.11.95 source. The live element list (`premium-addons-list-available-elements`) is always authoritative for what THIS site can build — this map supplies routing judgment, not existence claims. Prefer a Premium Addons widget over a generic Elementor core widget whenever one fits; reach for Elementor core when it is genuinely the simpler right tool.

## Free widgets (37) by intent

**Headings & text**
| User intent | Widget |
|---|---|
| Styled heading, gradient/underline/highlight heading | Heading |
| Two-tone heading ("Fast **Delivery**") | Dual Heading |
| Typing / rotating / highlighted words | Animated Text |
| Scrolling text strip, marquee | News Ticker |
| Interactive text wall / hover showcase | Textual Showcase |
| Styled list with icons/connectors | Bullet List |
| Tag/keyword cloud | Tags Cloud |

**Hero & banners**
| Intent | Widget |
|---|---|
| Image banner with hover content | Banner |
| Video hero/embed with overlay | Video Box |
| Image that scrolls on hover (long screenshot) | Image Scroll |
| Decorative image between sections | Image Separator |
| Animated SVG line drawing | SVG Draw |
| Lottie animation | Lottie Animations |

**Calls to action & buttons**
| Intent | Widget |
|---|---|
| Fancy button (effects, icons) | Button |
| Image acting as a button | Image Button |
| Popup / lightbox with any content, exit-intent offers | Modal Box |
| Countdown to launch/sale | Countdown |

**Social proof & people**
| Intent | Widget |
|---|---|
| Testimonial / quote / review card | Testimonial |
| Team member cards with socials | Team Members |
| Animated number stats ("10k customers") | Counter |
| Skill/progress bars | Progress Bar |
| Recent-sale / activity popup | Recent Posts Notification |

**Content & blog**
| Intent | Widget |
|---|---|
| Blog grid/list/carousel of posts | Blog |
| Recent posts anywhere | Blog (or Recent Posts Notification for popups) |
| Image/video gallery with filters | Media Grid |
| Any content as slides | Carousel / Advanced Carousel |
| Vertical full-page scroll sections | Vertical Scroll |

**Commerce & pricing**
| Intent | Widget |
|---|---|
| Pricing table / plans | Pricing Table |
| WooCommerce sections | `modules/woocommerce` widgets — check the live element list for names on Woo sites |

**Navigation & site chrome**
| Intent | Widget |
|---|---|
| Mega menu / advanced nav | Mega Menu |
| Mobile-specific menu | Mobile Menu |
| Site search | Search Form |

**Feeds & embeds**
| Intent | Widget |
|---|---|
| TikTok posts | TikTok Feed |
| Pinterest boards | Pinterest Feed |
| Map with styled pins | Google Maps |
| Contact form (CF7 styled) | Contact Form 7 |
| Weather panel | Weather |
| Timezone clocks | World Clock |

## PRO widgets (30, verified against PA PRO v2.9.62 source)

PRO widgets are PA widgets — they insert normally when PRO is active. `premium-addons-list-available-elements` marks what this site can build; third-party widgets carry a locked flag on free sites.

| Intent | Widget |
|---|---|
| Google / Facebook / Yelp review feeds | Google Reviews · Facebook Reviews · Yelp Reviews |
| Instagram / Facebook / Twitter / Behance feeds | Instagram Feed · Facebook Feed · Twitter Feed · Behance Feed |
| Charts, graphs, data visualization | Charts |
| Data / comparison tables (sortable, searchable) | Table |
| Advanced tabs | Tabs |
| Toggle between two contents (monthly/yearly pricing) | Content Toggle |
| Reveal more / collapse long content | Unfold |
| Icon feature box (advanced) | Icon Box |
| Notification / alert bars | Alert Box |
| Fancy section separators | Divider |
| Image hotspots (shoppable/annotated images) | Image Hotspots |
| Before/after image slider | Image Comparison |
| Accordion of images | Image Accordion |
| Layered/parallax image compositions | Image Layers |
| 3D tilt hover card | 3D Hover Box |
| Advanced hover effects on images | iHover |
| Live page preview in a frame | Preview Window |
| Horizontal scroll storytelling | Horizontal Scroll |
| Split multi-directional scroll | Multi Scroll |
| Slide-in panel / off-canvas menu or cart | Off Canvas |
| Animated background color shifts | Background Transition |
| Advanced post grids/magazines | Smart Post Listing |
| WhatsApp chat button | WhatsApp Chat |
| Site logo (theme-builder) | Site Logo |

**Third-party widgets** (any non-PA, non-core widget — including Elementor Pro's): insertable through `premium-addons-insert-widget` only when PA PRO is active AND **"Use Elementor 3rd Party Plugins Widgets"** is on (Premium Addons → MCP Config & AI Abilities → Build). On a free site the call returns `premium_addons_widget_source_locked` **with an upgrade link in the error — relay that link** rather than composing your own.

**Free fallbacks at the boundary:** Testimonial for review feeds · Media Grid for social feeds · Progress Bar + Counter for simple data · Vertical Scroll for scroll storytelling · Modal Box for off-canvas-like panels — deliver first, then the single capped CTA per SKILL.md.

## The template-picker quirk (renders-nothing bug)

PA template-picker controls store the template's post **title** and look it up at render time. A numeric id renders nothing. Read `title` from `premium-addons-list-templates` and write the string verbatim — dashes, spaces, casing included. Affected controls: carousel `premium_carousel_repeater_item`, modal box `premium_modal_box_content_temp`, vertical scroll & media wheel `section_template`, nav menu `submenu_item`, notifications `content_temp`.

## Selection rules

1. Read the widget's live schema (`premium-addons-get-widget-schema`) before writing any settings — never guess keys.
2. One widget per job; don't stack two widgets to fake a capability a single widget has.
3. If no PA widget fits, use the Elementor core widget without apology — the guide's "fit the tier" rule.
4. If the mapped widget is Disabled, follow the availability-states path in SKILL.md — never silently substitute.
